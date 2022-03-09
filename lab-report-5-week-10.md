# **Lab Report 3**

[Link to our repository](https://github.com/KQwQK/markdown-parse-lab3)


# 1. Figuring out the different output:
1. We create a bash script that will print out all the result.
```
for file in test-files/*.md;
do
  echo -n "$file "
  java MarkdownParse $file
done
```
2. Then, we use command ```bash script.sh > results.txt``` to store the output in an txt file.

3. Then we use ```diff``` to compare the results.

# 2. Choose two tests and explain how to fix it.

1. First difference case: Our group markdown parse didn't pick up the /uri but the lab9 markdown parse did.
```
< test-files/510.md [/uri]
---
> test-files/510.md []
```
Here is the original file
```
[link] (/uri)
```
**My approach to fixing this:**
    In this test case, I think that the lab9 markdownparse file made mistakes. Note that there is a space between the square brackets and the parenthesis. Therefore it shoudn't be consider a link because from the md file the square bracket should be next to the parenthesis. One simplfy code fix can be:

    ```
    if(markdown.indexof("]") + 1 == " "){
        nextOpenBracket = markdown.index("[", nextCloseBrackets)
        break;
        }
    ```
That is if there is an space after the closing square brackets, make the openBracket to search for the next open brackets that is before the closing square brackets.

2. Second difference case: Our group markdown parse pick up the whole thing that is inside the parenthesis but the lab9 markdown parse didn't take any.
```
< test-files/504.md []
---
> test-files/504.md [/url "title", /url 'title', /url (title]
```
Here is the original file
```
[link](/url "title")
[link](/url 'title')
[link](/url (title))
```
**My approach to fixing this:**
    In this test case, I think both markdownparse are wrong. The only valid link is the ```/url``` part but not the "title" part. The markdwon parse. If I'm to fix this, I think I will search for the space after the link. Since a URL link cannot have sapce, the only space will occur is after the link, and if the program reaches a space in the parenthesis, return the value. A helper methods can be implmented.

    ```
        public String helperMethods(String insideStr){
            //Example input: (\url ("title"))
            
            int start = insideStr.indexof("(") + 1;
            int end = insideStr.indexof(" ") ;
            return insideStr.subString(start, end);
        }
    ```
That when searching inside the parenthesis, use a helper methods to find the URL link inside, and only take the substring of from the first to the space.
