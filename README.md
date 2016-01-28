####Tradd Deaver
####January 27 2016
####CSCI 223 Problem Set 2

####Collaborators: 
1. James Andrus

####Resources:
1. TextBook, Eclipse

####Feedback:
The concepts for the six problems assigned were simple to understand; however, to write the code so that it works is another matter.  

###Problem Set 2
Six problems from the book in chapter one section three.

####Full Source Code
[Full Code](Problem-Set-2 / source code )
https://github.com/cdeaver/Problem-Set-2/blob/master/source%20code

###Discussion
The purpose to these exercises are to practice working on Stacks and moving and removing Nodes inside these LinkedLists.  I wrote code for 6 methods that manipulate a Stack. 

###Removes the last node in the stack

####1.3.19 Testing Code
```javascript
// 1.3.19
	public void removeLast() {
		Node temp = first;
		while (temp.next.next != null) {
			temp = temp.next;
		}
		N--;
		temp.next = null;
	}

```

###Deletes the kth term in stack

####1.3.20 Testing Code 
```javascript
// 1.3.20
	public void delete(int k) {
		if (k > N) {
			System.out.println("Element at " + k + " does not exist.");
		} else if (N == k) {
			removeLast();
		} else if (k == 1) {
			first = first.next;
			N--;
		} else {
			Node temp = first;
			int count = 2;
			while (count < k) {
				temp = temp.next;
				count++;
			}
			N--;
			temp.next = temp.next.next;
		}

	}
```
 
###Finds the kth term in a stack

####1.3.21 Testing Code 
```javascript
// 1.3.21
	public boolean find(LinkedList<Node> list, String key) {
		Node temp = list.getFirst();
		// checks first node
		if (temp == null)
			return false;
		if (((String) temp.item).equalsIgnoreCase(key))
			return true;
		// checks rest of nodes in list
		while (temp.next != null) {
			if (((String) temp.next.item).equalsIgnoreCase(key))
				return true;
			temp = temp.next;
		}
		return false;
	}
```
 
###Removes the node after the given node
######This method removes the Node after the given Node and does nothing if 
######*argument is null 
######*there is no Node after given Node

####1.3.24 Testing Code 
```javascript
// 1.3.24
	public void removeAfter(Node node) {
		Node temp = first;
		// argument is not null
		if (node != null) {
			if (first != null) {
				// iterates to the node before node we are searching for
				while (temp.next != null && temp.next != node) {
					temp = temp.next;
					N--;
				}
				// if next node is the node we are looking for
				if (temp.next != null && temp.next == node) {
					temp = temp.next;
					// if node after node we are looking for has an item
					if (temp.next != null) {
						temp.next = null;
					}
				}
			}
		}
	}
```

###Method insertAfter
######Given two Nodes, this method goes through the Stack and finds the first given node and inserts the second given node after the first.  If either are null, then this method does nothing.  Then the code checks every node in the stack to see if the first given node is in the list.  If it is, then the node is inserted and any nodes originally connected after the first given node are then linked to the inserted node.

####1.3.25 Testing Code 
```javascript
// 1.3.25
	public void insertAfter(Node one, Node two) {
		// if the arguments are not null
		if (one != null && two != null) {
			// if first is not one
			if (first != one) {
				Node temp = first;
				while (temp.next != null && temp.next != one) {
					temp = temp.next;
					N--;
				}
				if (temp.next != null && temp.next == one) {
					// temp == one
					temp = temp.next;
					// inserts two after one
					if (temp.next != null) {
						Node n1 = temp.next;
						temp.next = two;
						two.next = n1;
					} else {
						temp.next = two;
					}
				}
			}
			// if first is one
			else {
				// inserts two after one and connects rest of list
				if (first.next != null) {
					Node n1 = first.next;
					first.next = two;
					two.next = n1;
				} else {
					first.next = two;
				}
			}

		}
	}
```

###Method remove
######Given a list and a key, you search for any and all nodes that match the key.  You then remove the nodes from the list while keeping it intact, as in just remove the one node not all the ones after it.

####1.3.26 Testing Code 
```javascript
// 1.3.26
	public void remove(LinkedList<Node> list, String key) {
		int k = list.size();
		Node temp = list.getFirst();

		// if first is key
		if (((String) temp.item).equalsIgnoreCase(key)) {
			first = temp.next;
		}

		while (N < k) {
			// if temp is key, remove and add rest of nodes again.
			// if key is last node, just remove.
			if (((String) temp.item).equalsIgnoreCase(key)) {
				if (temp.next != null) {
					Node n1 = temp.next;
					temp = null;
					temp = n1;
				} else {
					temp = null;
				}
			}
			temp = temp.next;
			N++;
		}
	}
```
