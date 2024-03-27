# Problems
- [Problems](#Problems)
    - [WordBreakProblem](#WordBreakProblem)
    - [String Related Problems](#String-Related-Problems)

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

## String Related Problems
Q1.startsWith<br>
Q2.countUniqueSubstring<br>
Q3.longestWordWithALlPrefix

Need detailed explnation of each question
```Java
//Practice problem for Trie Ds
//Q1.startsWith
//Q2.countUniqueSubstring
//Q3.longestWordWithALlPrefix


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

    //Create a function boolean startsWith(String prefix) for a trie
    //Returns true if there is a previously inserted String word that has the prefix and false
    public static boolean startsWith(String prefix)
    {
        Node curr= root;
        for (int i = 0; i < prefix.length(); i++) {
            int idx = prefix.charAt(i) - 'a';

            if (curr.children[idx] == null) {
                return false;
            }
            curr = curr.children[idx];
        }
        return true;
    }


    //Count Unique Substrings
    //Given a string of length n of lower case alphabets characters,
    // We need to count total number of distinct substrings of the strings
    //we will prefix of all suffix
    public static int countUniqueSubstring(Node root){
        if(root == null)
        {
            return 0;
        }
        int count = 0;
        for (int i = 0; i < 26; i++) {
            if(root.children[i] != null)
            {
                count = count + countUniqueSubstring(root.children[i]);
            }
        }
        return count + 1;
    }


    //find the string that contains all the prefix from the given array
    //Each letter of the word in Trie has all EndOfWord is true is the longest word  with all prefix
    public static String finalString = "";
    public static void longestWordWithALlPrefix(Node root,StringBuilder temp)
    {
        if(root == null)
            return;

        for (int i = 0; i < 26; i++) {
            if(root.children[i] != null && root.children[i].endOfWord)
            {
                temp.append((char)(i + 'a'));
                if(temp.length() > finalString.length())
                {
                    finalString = temp.toString();
                }
                longestWordWithALlPrefix(root.children[i],temp);
                temp.deleteCharAt(temp.length() - 1);
            }
        }
    }


    public static void main(String[] args) {

        //Code for countUniqueSubstring
        String word = "ababa"; //a , ab, aba, abab, ababa, b, ba, bab, baba, ""
        for (int i = 0; i < word.length(); i++) {
            insert(word.substring(i));
        }
        System.out.println(countUniqueSubstring(root)); 10


        //Code For startsWith problem
        String[] word1 = {"a", "banana", "app", "appl", "ap", "apply", "apple", "mango", "man", "woman"};
        String prefix = "app";
        for (int i = 0; i < word1.length; i++) {
            insert(word1[i]);
        }
        System.out.println(startsWith(prefix)); // true


        //Code for longestWordWithALlPrefix
        String[] word2 = {"a", "banana", "app", "appl", "ap", "apply", "apple"};
        for (int i = 0; i < word2.length; i++) {
            insert(word2[i]);
        }
        longestWordWithALlPrefix(root, new StringBuilder());
        System.out.println(finalString);  // apple

        /*
        String word = "yash";
        System.out.println(word.charAt(0) - 'a'); //24
        System.out.println((char)(0 + 'a'));  //a
        */
    }
}
```
