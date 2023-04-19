# SC1007-Algorithms
Algorithm Code

## Hash Table
### Coalesced Hash
Task: code the hashinsert and hashfind function in a coalesced hash table
Setup: hash table with 3 columns, key, value and next. the next column points to the next row i should look at
this is because if a slot is used, the next key would likely contain the value i want

EG:
h(k) = k mod 3
| Key | Value |next |
|-----|-------|-----|
| 1   |  4    |   2 |
| 2   |  7    |   - |



in this case both 4mod3 and 7mod3 = 1, since 4 is inserted first, 4 gets the first slot.
1 will have a value of next = 2 to tell the user that 7 is likely in 2 and to search in 2 for 7. 
#### Hash Insert Function
For the hash insert function, i split the problem into 3 cases
##### Case 1
the simple case, where the index is the key
i.e the slot is unused previously

##### Case 2
the duplicate case, where the key value already exists in the hash table

##### Case 3
the toughest case
first i get next possible key value, and check if the next key is a repeat key 
i.e first slot is used by another value, but the next slot is used by the value i want to insert

if alls clear, then i let index = next and next be the next after the current next, this sets up a loop i can use later
 from there i try to insert it into any available slot after the current slot. 
 if there are no more slots available, i use a second for loop to look in front of the current index 
 
 if all else fails, that means the table is full

#### Hash find function
this function is relatively simple, once again there are 3 cases
##### Case 1
value doesnt exist, the index that it is supposed to be in is empty

##### Case 2
value exist and is in the first iteration

##### Case 3
keep searching using the next until i get a hit, if i dont get a hit, it means the value doesnt exist


### Doubly Linked List
Task: Code the hash insert and hash delete function
Setup: I am to use linked lists to insert functions into the hashtable and delete functions from the hash table

#### Hash Insert
this function computes the hash index of the key using the hash function.
the hash function returns a value between 0 and hashtable size -1.

i then use a linked list to check if the key exists in the hash table by iterating over the linked list using a while loop

if the key doesnt exist, i then allocate a new listnode and add it to the head of the linked list
i use a if loop to make sure the linked list is not empty, 
if it is not empty, i update the previous pointer of the current head node to point to the new node
i then update the size of the linked list and hash table

#### Hash delete
similar to above, i compute the hash index of the key using the hash function
i then iterate over the linked list to find the node
once i find the node, i remove the node from the linked list by updating the next and prev pointer of the neighbours
this is done by first making sure that this is not the head node,
if it isnt the head node, then i connect pre and next
if this is the head node,
then i set the next node as the head node

next i make sure this is not the tail node,
if this is not the tail node then i set the next and pre to connect
if this is the tail node, then removal can be done with no qualms as nothing else is affected

after all the deletion, i make sure the reduce the table size and linked list size

if the key cannot be found, then i return that the deletion failed


### Double Hashing
Task: coding the hashinsert and hash delete function
Setup: a standard double hashing table where two modulo functions are used to determine the position of keys
h(k) = (key + i*step) mod n

#### Hash insert





