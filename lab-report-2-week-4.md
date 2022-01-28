# **Lab Report 2**

> This is demonstration of how to fix bugs systematically. In Lab3 and Lab4 we worked on a file called MarkdownParse.java. Its purpose is to find all the link in a Markdown file, but the code will occur problems when testing different files, and it requires some changes.


# **First Code Change**
1. Screenshot of the first code changez
<p align="center">
  <img width="500" height="80" src="images/lab-week4-p1.png">
</p>

2. [Link to failure-inducing input file](test-file/test-file.md)

3. Symptom of the failure-inducing input
- The symptom is that there will be an infinite loop because the mthods indexOf() cannot find the next opening parenthesis if there is no link at all. Therefore, it will throw an Index Out Of Bounds Exception because the Substring() methods cannot find index at -1.

4. Explanation
- Our first solution is fairly simple, make the program break when encounter a problem that the while loop will stop when we cannot find open parenthesis shown in line 17. By this way the loop can be stop and it will return an empty list. It makes the codes executable, but still not all the problems are being solved.

# **Second Code Change**

1. Screenshot of the first code change
<p align="center">
  <img width="500" height="200" src="images/lab-week4-p2.png">
</p>

2. [Link to failure-inducing input file](test-file/test-file.md)

3. Symptom of the failure-inducing input:


4. Explanation


# **Third Code Change**

1. Screenshot of the first code change
<p align="center">
  <img width="430" height="300" src="images/lab-week4-3.png">
</p>


2. [Link to failure-inducing input file](test-file/test-file2.md)

3. Symptom of the failure-inducing input

4. Explanation
