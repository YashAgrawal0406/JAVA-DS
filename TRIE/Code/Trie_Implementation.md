
# Topics
- [Topics](#Topics)
  - [Code](#Code)
    - [Node Sturcture](#Node-Sturcture) 
    - [Trie Data structre](#Trie-Data-structre)
 
## Code
### Node Sturcture
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
```

### Trie Data structre
```Java
//Trie Data Structure
//Trie is a K-ary tree means it can have any no. of child

public class Main {

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

    public static void main(String[] args) {
        String[] word = {"the","a","there","their","any"};

        for (int i = 0; i < word.length; i++) {
            insert(word[i]);
        }

        System.out.println(search("the")); //true
        System.out.println(search("a")); //true
        System.out.println(search("an")); //false
        System.out.println(search("any")); //true
        System.out.println(search("yash")); //false
    }
}
```
