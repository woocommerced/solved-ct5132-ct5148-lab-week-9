Download Link: https://assignmentchef.com/product/solved-ct5132-ct5148-lab-week-9
<br>



<h1>Regular expressions and web scraping</h1>

In lectures we studied regular expressions and used &lt;regex101.com&gt; to test regexs interatively. Now let’s practice using them in Python.

Figure 1: On <a href="https://nationalservice.ichec.ie/login/login.php">https://nationalservice.ichec.ie/login/login.php,</a> there is a list of all the ICHEC projects, Classes

A, B and C.

We can use Ctrl-A, Ctrl-C, Ctrl-V to put this data in a text file: data/ichec_projects_scrape.txt.

However, it is now unstructured plain text. Let’s use regular expressions to extract the project codes. Each code is like ngcom018c or ulphy033a.

<ol>

 <li>import re</li>

 <li>Read the data: s = open(“../data/ichec_projects_scrape.txt”).read()</li>

 <li>Write a pattern p to match codes (maybe test on regex101.com)</li>

 <li>Call a Python re function to find all the project codes.</li>

 <li>Notice that the codes seem to have a specific encoding: ngcom018c is NUI Galway, Computer Science, 18, Class-C. ulphy033a is University of Limerick, Physics, 033, Class-A. Use <strong>grouping </strong>( ) to extract the four individual parts in each code. Using this, how many Class-C Computer Science projects are there across all universities?</li>

 <li>Write a new pattern to match only NUI Galway projects, and test it.</li>

</ol>

(Solutions: code/count_ichec_projects.py.)

<h1>Generative art using grammars</h1>

We already have the following code which will generate an image given a string (the string representing an arithmetic expression). Notice here we are using x[0] and x[1] to represent the two axes (not x and y as in the notebook).

<table width="632">

 <tbody>

  <tr>

   <td width="632">import numpy as npimport matplotlib.pyplot as plt import matplotlib.cm as cmn <strong>= </strong>200xs <strong><sub>= </sub></strong>np.linspace(0, 1, n) ys <strong><sub>= </sub></strong>np.linspace(0, 1, n)x <strong>= </strong>np.meshgrid(xs, ys) <em># x contains x[0] and x[1]</em>ps <strong><sub>= </sub></strong>“np.sin(40 * x[0]) * np.sin(30 * (x[1]+0.5)) * x[0] * x[1]” p <strong><sub>= </sub></strong>eval(“lambda x: ” <strong><sub>+ </sub></strong>ps)plt.imshow(p(x)) plt.axis(‘off’) plt.show()</td>

  </tr>

 </tbody>

</table>

<ol start="7">

 <li>Change ps to make cooler/more complex images.</li>

</ol>

We also have the following code which will derive a new string we can use instead of ps:

from grammar import Grammar <em># assume we are in code/ directory </em>fname <strong><sub>=</sub></strong> “arithmetic.bnf” g <strong><sub>=</sub></strong> Grammar(file_name<strong><sub>=</sub></strong>fname) ps <strong><sub>=</sub></strong> g.derive_string() print(ps)

<ol start="8">

 <li>Use this to generate several images. If you sometimes see the error TypeError: Invalid shape () for image data, that’s probably because the grammar generated a string like 0, i.e. a constant. There are ways to work around this, but we can just ignore it and generate a new one.</li>

 <li>If you like, put everything in a convenient function or in a loop to make the process of trying new ones quicker.</li>

 <li>Change arithmetic.bnf to allow some cooler/more complex images. Post your best images on the Discussion Board.</li>

</ol>

Optional ideas: try different colour maps (see matplotlib.cm), or create polar coordinate variables

(<em>r,θ</em>).

<ol start="11">

 <li>Take a look at derive_string(), defined in grammar.py, to see the implementation of the simple algorithm that we defined in lectures for deriving a string from a grammar.</li>

</ol>