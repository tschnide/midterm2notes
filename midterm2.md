### Midterm two notes
#### Sorting
* Merge Sort
    * As you merge you always take the first A B | A C would take the A on the left and copy it to the array
    * This is in place. In place means that it doesn't take any extra memory
    * Here is how the algorithm works:
        * Take a comparable array 
        * Given the starting element and the ending element find the center element
        * Sort left of the center, sort right of the center
        * Merge them using this same algorithm 
        * In other words you will now pass the first half and the second half back into this algorithm
        * It will continue recursively until it is only comparing two elements and then follow itsef back up the recursion stack
        * The key here is that the merge actually compares. It's ultimately doing the sorting.
    * It is equally fast in reverse order as unsorted
    * Analysis:
        * In worst case it's performance is N log
        * N because it will touch each element 1 time
        * Log N because divide and conquer is logarithmic
    * This requires an extra array equal to the size of the first array
    * Improvements:
        * If the array to be sorted is greater than about seven it's better to just use insertion sort because there is too much overhead and complication.
        * Stop if it's already sorted
            * As you are sorting if at any point the biggest in the smaller half is less than the smallest in the big half then you can stop. This works because the arrays have to be sorted to begin with.
    * Interesting note, there is no simple way to actually implement an in place merge sort that has yet been discovered
* Quick Sort
    * Here is how the algorithm works:
        * Shuffle to get it in random order
        * Pick a random element because it is random the first one will work. This will be the partitioning element.
        * Set up two pointers one to the first position after the partitioning element and one to the last element of the array. Call these l and r.
        * Now scan with l moving from left to right until it finds an element greater than the partitioning element.
        * Scan with r moving from right to left in the same fasion until it reaches an element less than the partitioning element.  
        * Now exchange r and l. 
        * Continue until r and l cross.
        * Once they have crossed r will point to the last position of the left partition. That will be the element one less than the partitioning element.
        * Exchange r and the partitioning element (placing the value of r at index 0) 
        * Now you know that everything to the left of the partitioning element is less than it and everything to the right is greater than it.
        * Take the two sub-partitions and repeat the process.
        * Here the act of partitioning actually sorts.
    * Best case: the random partition happens to be the average (center) of all of the elements
        * N log N
    * Worst case: the random partition happens the be the smallest of the set of elements in the array to be sorted
        * 1/2 N^2
        * Highly unlikely because it's shuffled ie random
        * Note that a sorted array will cause worst case run time. This is because the partition that is selected will be the smallest element ( It picks the partition by selecting the element at index 0).
    * Improvements:
        * If the array to be sorted is greater than about ten it's better to just use insertion sort because there is too much overhead and complication.
        * You can ensure that the partitioning element is closer to the middle by taking the median of three random selections from the array
* Selection Sort
* Insertion Sort
* Priority Queue
    * Unlike other collections such as a stack or a queue, the priority queue removes the largest or smallest item contained
    * A Binary Heap operates in N log M time. Where M is the number of items in the heap.
    * The heap structure is better than an resizing array because you don't have to shift all of the elements every time you add something to the center
    * Binary tree
        * Each node has at most two children
        * A complete binary tree has all levels full except for the bottom
        * The height of a _complete_ tree with N nodes is log N. This is because the height increases when N is a power of 2
        * Heap Ordered Binary Tree 
            * A heap ordered binary tree is a binary tree where each parent node's _key_ is no smaller than its children ie >=
            * Stored in an array with the root at index 1.
            * Stored in level order. Level order is like reading a book. Begin at the top and read each line from left to right.
            * To traverse:
                * The root k is at index 1 or array[1] . To find the children take 2k and 2k + 1. 
                * To find parents take k/2. Integer division throws out the remainder and you get the right node.
#### Searching
* 
#### Random 
* asserts 1) help detect logical bugs and 2) documents the code 
    * asserts take boolean conditions
    * you can enable or disable them at runtime so if you turn them off they don't cost anything while running in production
* Quicksort is actually faster than Mergesort even though they are both N log N. I'm assuming that this is because it has fewer constant time operations. Mergesort moves elements between two arrays.
* In place means that it doesn't take any extra memory
* Tree traversal
    * Level order: start at the top and go from left to right beginning at each new level.
    * In order: left, root, right. Imagine you are drawing vertical lines down from each begging from the left.
    * Pre order: root, left, right. Beginning at the root flow left along the outside of the tree.
    * Post order: left, right, root. Think of leaves. Begin with the left most bottom leaf, visit it, imagine that it dissapeared. Now repeat.
    * https://www.youtube.com/watch?v=eL8NZ-21lqI 
    * https://www.youtube.com/watch?v=gm8DUJJhmY4
#### Quick reference 
* Merge Sort
    * N log N
    * In place ?
    * Recursive
* Quick Sort
    * In place (This is an advantage that it has over Merge Sort )
    * N log N
    * Recursive
    * Not stable
* Binary Tree
    * Full binary tree: all the nodes have two children except for the leaves
        * I also read that it means that every node has either zero or two children. Not sure.
    * Complete binary tree: every level has two children except the last and all the nodes are as far left as possible 
    * A leaf node is a node with no children
    * The following are valid because each node has at most two children
    *              0            0                0   
    *            /            /   \            /   \
    *          0             0     0 
    *        /             /         \
    *      0              0           0
* Binary Heap
    * With k as the index:
        * Find parent: k/2
        * Find children: 2k and 2k + 1
    * To swim switch the key with its parent as long as it's larger.
    * To insert add the new element to the end of the array. (In tree terminology this is the bottom level in the first open left position.) Then swim if necessary. 
    * To sink, switch switch the key with its larger child until both children are smaller. 
    * To delete max switch the root with the end node then sink 
    * Del max and insert occur in log N time and the max function is constant 


#### Questions
* Is merge sort in place? Initially he says it is (first merge sort recording) later he says it isn't practically. Quora seemed to say that it is not.
* Does quicksort fully sort? The final step exchanges the partitioning element and the greatest element in the lesser sub partition. This means that it places it at index 0. So one element is out of place.
* What is a stable sort? (put this in the random category) 
* Quicksort randomizes every time. Why? Just to dislodge the index 0 element from the left array?