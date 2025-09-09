---
num: "Lecture 16"
desc: "Binary Search Trees cont."
ready: true
lecture_date: 2025-09-09 14:00:00.00-7:00
---

Recorded Lecture: [9-9-25](https://drive.google.com/file/d/1OLdr-1Kb0qD2FcGeHOMZ5P6piS7iit0S/view?usp=drive_link)

# BST Deletion continued.

## Case 3: Delete a node with two children
* First find the successor (node with next greater value) in the right subtree
    * This can be done by traversing the left children of the node to be deleted’s right subtree
    * Also note that the successor will always only have **at most** one child
        * If the successor had a left child, then it wouldn’t be the successor!
* Temporarily store the successor and delete the successor from the tree
    * Deleting the successor will fall in either Case 1 or Case 2
* Replace the deleted node’s value with the successor’s value

![BSTDeleteCase3.png](BSTDeleteCase3.png)