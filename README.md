Download Link: https://assignmentchef.com/product/solved-cs2123-data-structures-assignment-4-tree-algorithms
<br>
For this assignment you’ll be implementing several tree-based algorithms that we saw in class. Specifically you’re editing only “tree.c”. You shouldn’t need to change any other files. Here are your algorithms to implement:

<h1>Huffman Tree – printHuffmanEncoding</h1>

Given the root of a Huffman tree and a character, print the sequence of bits used to encode that character based on the tree.

<strong>Reminder: </strong>Going left in the Huffman tree appends a ‘0’ and going right appends a ‘1’.

<h1>AVL Tree – rebalanceTree</h1>

Here is a brief outline of algorithm for rebalancing the tree using AVL trees:

<strong>Reminder: </strong>the balance of <em>x </em>is the height of the left subtree of <em>x </em>– height of the right subtree of <em>x</em>.

<ul>

 <li>Let <em>x </em>be the node we are starting our rebalance from</li>

 <li>While <em>x </em>is not NULL

  <ul>

   <li>if the balance of <em>x </em>is −2 or 2

    <ul>

     <li>Set <em>z </em>equal to the child of <em>x </em>with the greater height</li>

     <li>if the balance of <em>x </em>and the balance of <em>z </em>have different signs

      <ul>

       <li>if the sign of the balance of <em>z </em>is + right rotate on <em>z</em></li>

       <li>if the sign of the balance of <em>z </em>is − left rotate on <em>z</em></li>

      </ul></li>

     <li>if the balance of <em>x </em>is 2 right rotate on <em>x</em></li>

     <li>if the balance of <em>x </em>is −2 left rotate on <em>x</em></li>

     <li>Update height of the rotated nodes. (height of a node = height of its taller subtree plus 1).</li>

     <li>if <em>x </em>was the root before the rotate, update the root to the parent of <em>x</em></li>

    </ul></li>

   <li>Set <em>x </em>equal to the parent of <em>x</em></li>

  </ul></li>

</ul>

To test if your tree is balanced you can uncomment the calls to <em>checkAVLTree </em>in driver.c. This function will inform you if there are any balances in your tree outside of 1, 0, and -1. Likewise there is function <em>printTree </em>which will print the contents and structure of your tree (elements higher up in your tree are printed with more tabs in front of them).

For my implementation of rebalance I created the following helper functions. You don’t have to do this but it may help break this large problem down into several smaller, simpler, problems:

TNode* getTallerSubTree(TNode* x); bool isSameSignBalance(TNode* x, TNode* z);

The function <em>getTallerSubTree </em>finds and returns the subtree of <em>x </em>with the larger height. The function <em>isSameSignBalance </em>returns true if the two given nodes both have balance ≥ 0 or ≤ 0.

<h1>Segment Tree – insertSegment and lineStabQuery</h1>

Each TNode contains a low and high value. These specify the range of values that this represents on the number line. Each TNode also contains a count, <em>cnt</em>, that represents the number of line segments associated with this node. <strong>insertSegment </strong>This inserts a new line segment into the tree.

<ul>

 <li>Go down the the segment tree starting at the root</li>

 <li>If the root is a leaf, return.</li>

 <li>Else if the segment is completely to the left or right of the current node’s range, return.</li>

 <li>Else if the segment is completely covers the range represented by this node: increase <em>cnt </em>by 1 and return.</li>

 <li>Else: Recursively call insertSegment on the left and right children of this node.</li>

</ul>

<strong>lineStabQuery </strong>This checks how many line segments cross a given point, <em>queryPoint</em>.

<ul>

 <li>Go down the the segment tree starting at the root</li>

 <li>If the root is a leaf: return 0.</li>

 <li>Else if the <em>queryPoint </em>is completely to the left or right of the current node’s range: return 0.</li>

 <li>Else: Recursively call lineStabQuery on the left and right children of this node. Return the sum of their return values and current node’s <em>cnt</em>.</li>

</ul>

<strong>Deliverables:</strong>

Your solution should be submitted as “tree.c”. Upload this file to Blackboard under Assignment 4. <strong>Do not zip your file</strong>.

To receive full credit, your code must compile and execute. You should use valgrind to ensure that you do not have any memory leaks.


