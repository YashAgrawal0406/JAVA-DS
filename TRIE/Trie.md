
# Topics
- [Topics](#Topics)
  - [Summary](#Summary)
  - [Complexity](#complexity)
  - [What is a Trie Data Structure?](#What-is-a-Trie-Data-Structure)
  - [Why Use a Trie Data Structure?](#Why-Use-a-Trie-Data-Structure)
  - [Properties of a Trie Data Structure](#Properties-of-a-Trie-Data-Structure)
  - [Basic Operations in a Trie Data Structure](#Basic-Operations-in-a-Trie-Data-Structure)
    - [Trie Node structure](#Trie-Node-structure)
    - [Search Operation in Trie](#Search-Operation-in-Trie)   
    - [Insert Operation in Trie](#Insert-Operation-in-Trie)      
  - [References](#references)
 
## Summary
> Trie data structure is an advanced data structure used for storing and searching strings efficiently. Trie comes from the word reTRIEval which means to find or get something back. Dictionaries can be implemented efficiently using a Trie data structure and Tries are also used for the autocomplete features that we see in the search engines. Trie data structure is faster than binary search trees and hash tables for storing and retrieving data. Trie data structure is also known as a Prefix Tree or a Digital Tree. We can do prefix-based searching easily with the help of a Trie.

## Complexity
- Time complexity of insertion, deletion and searching for a string of length 'k' in the Trie data structure is:
  - Insert - O(k)
  - Delete - O(k)
  - Search - O(k)
- The time complexity for building a Trie data structure is O(N * avgL), where 'N' is the number of strings we want to insert in Trie and 'avgL' is the average length of 'N' strings.
- Trie data structure has many applications, including 'prefix-based searching', 'sorting strings lexicographically' etc.

## What is a Trie Data Structure?
> Trie data structure is a tree-based data structure used for storing collections of strings. The word trie comes from the word reTRIEval which means to find or get something back. If two strings have a common prefix then they will have the same ancestor in the trie. In a trie data structure, we can store a large number of strings and can do search operations on it in an efficient way. A trie can be used to sort a collection of strings alphabetically as well as search whether a string with a given prefix is present in the trie or not. A dictionary can be implemented efficiently with the help of a trie data structure. Let us now discuss the when and how to implement a Trie Data Structure.

## Why Use a Trie Data Structure?
A trie data structure is used for storing and retrieval of data. Another data structure that we can think of for doing the same operations is a Hash Table. However, a trie data structure can be used to handle these operations more efficiently than a Hash Table. Moreover, a trie data structure can be used for prefix-based searching while we can not use a hash table for the same. An example of prefix-based searching is to search how many strings present in a collection of strings contain a given prefix. A trie data structure gives us advantages over a hash table mainly in the following factors-
- A trie data structure can be used to implement a wide range of features that can't be implemented with a hash table. For example, Prefix-based searching can't be done with a hash table.
- There are no collisions in a trie data structure which means a better worst-case time complexity than a hash table that is not implemented properly.
- Hash functions are not used in a Trie data structure.
- Searching of a string in a Trie data structure is done in O(k) time complexity. Where k is the number of words in the query string. It may also take less than O(k) time when the query string is not present in the trie.


## Properties of a Trie Data Structure
The structure of a trie is like that of a tree. Each trie consists of a root node. The root node branches into various child nodes having multiple edges. Each TrieNode consists of an array of pointers where every index of the array represents a character. Each node of a trie represents a string and each edge represents a character. The root node is an empty string. Each node except the root node is a string having characters along the path from the root to that node. Let us understand the structure of the Trie data structure with the help of an example.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/5d371f9a-90fe-4449-b39a-578e24b75dfc)

The diagram above shows a trie data structure with input strings as ball, bat, eAr, eAt, tea, and ten. We can see that every node represents a part or prefix of the given strings. The root node represents an empty string. Each edge is represented by a character.

Every level of the Trie data structure represents a prefix of a given length. If we consider the root node to be at level 0. Then the root node represents a prefix of length 0 or an empty string. Level 1 of the Trie represents a prefix of length 1 and so on.

Two child nodes have the same ancestors if tea and ten have the same ancestors which are te and t. This is because they share the same prefix of te.

Note that we can include any number of characters in our Trie data structure ranging from alphabets, numbers, and special characters. In this article, we will discuss strings with characters a-z. Thus for every node in the Trie, we will need an array of pointers of size 26. Where the 0th index will represent a and the 25th index will represent z.

Another important thing to note is that every string in the Trie data structure is sorted lexicographically from left to right. We will learn how to implement it while discussing the insert operation in a Trie.

Now let us discuss how we can implement insert, search and delete operations in a Trie data structure.

## Basic Operations in a Trie Data Structure
### Trie Node structure
```Java
static class Node{
    Node[] children;
    boolean endOfWord;

    public Node(){
        children = new Node[26];
        for (int i = 0; i < 26; i++) {
            children[i] = null;
        }
        endOfWord = false;
    }
}
static Node root = new Node();
```


### Insert Operation in Trie.
```Java
public static void insert(String word){
    Node curr= root;
    for (int i = 0; i < word.length(); i++) {
        int idx = word.charAt(i) - 'a';

        if(curr.children[idx] == null){
            //add new node
            curr.children[idx] = new Node();
        }
        if(i == word.length() -1) {
            curr.children[idx].endOfWord = true;
        }

        curr = curr.children[idx];
    }
}
```


### Search Operation in Trie
```Java
public static boolean search(String word){
    Node curr= root;
    for (int i = 0; i < word.length(); i++) {
        int idx = word.charAt(i) - 'a';

        if(curr.children[idx] == null){
            //add new node
            return false;
        }
        if(i == word.length()-1 && curr.children[idx].endOfWord == false) {
            return false;
        }
        curr = curr.children[idx];
    }
    return true;
}
```


## References
- [Trie DS Scaler](https://www.scaler.com/topics/data-structures/trie-data-structure/)

















