# Problems
- [Problems](#Problems)
    - [WordBreakProblem](#WordBreakProblem)
    - [Reverse](#Reverse)
    - [Balanced Parathensis](#Balanced-Parathensis)
    - [Duplicate Parenthesis](#Duplicate-Parenthesis)
    - [Infix Prefix Postfix](#Infix-prefix-postfix)
    - [Infix to Prefix and Postfix Conversion](#Infix-to-Prefix-and-Postfix-Conversion)
        - [Infix to Prefix Conversion](#Infix-to-Prefix-Conversion)
        - [Infix to Postfix Conversion](#Infix-to-Postfix-Conversion)
    - [Prefix to Infix and Postfix Conversion](#Prefix-to-Infix-and-Postfix-Conversion)
        - [Prefix to Infix Conversion](#Prefix-to-Infix-Conversion)
        - [Prefix to Postfix Conversion](#Prefix-to-Postfix-Conversion) 
    - [Postfix to Infix and Prefix Conversion](#Postfix-to-Infix-and-Prefix-Conversion)
        - [Postfix to Infix Conversion](#Postfix-to-Infix-Conversion)
        - [Postfix to Prefix Conversion](#Postfix-to-Prefix-Conversion) 
- [Links To Stack Problems](#Links-to-stack-problems)

## WordBreakProblem
Need explanation of question
```Java
//Using Trie DS for WordBreakProblem

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

    public static boolean wordBreak(String key){
        if(key.isEmpty()){
            return true;
        }

        for (int i = 1; i <= key.length(); i++) {
            String firstPart = key.substring(0,i);
            String secondPart = key.substring(i);

            if(search(firstPart) && wordBreak(secondPart))
            {
                return true;
            }
        }
        return false;
    }
    public static void main(String[] args) {
        String[] word = {"i","like","sam","samsung","mobile"};

        for (int i = 0; i < word.length; i++) {
            insert(word[i]);
        }
        String key = "ilikesamsung";

        System.out.println(wordBreak(key));  // true

        System.out.println(wordBreak("ilikesung"));  // false
    }
}
```

