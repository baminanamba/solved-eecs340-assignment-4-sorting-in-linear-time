Download Link: https://assignmentchef.com/product/solved-eecs340-assignment-4-sorting-in-linear-time
<br>
Draw the decision tree for the deterministic version of Quicksort on an array with <em>n </em>= 3 elements.

<h1>Problem 2</h1>

Given an array <em>A </em>of <em>n </em>integers in the range [0<em>,k</em>), we would like to build an index, which we would like to use to answer any query of type “what is the number of integers in <em>A </em>that are in the range [<em>a,b</em>]?” For this purpose, write the following two procedures:

<ul>

 <li>Procedure PreProcess(<em>A</em>) should process <em>A </em>to build an index in <em>O</em>(<em>n </em>+ <em>k</em>) time. The size of your index should be <em>O</em>(<em>k</em>).</li>

 <li>Procedure Query(<em>A</em>, <em>a</em>, <em>b</em>) should return the number of integers in <em>A </em>that are in the range [<em>a,b</em>] in <em>O</em>(1) time.</li>

</ul>

<h1>Problem 3</h1>

Let <em>A </em>be an <em>m </em>× <em>n </em>matrix. The <em>transpose </em>of <em>A </em>is an <em>n </em>× <em>m </em>matrix <em>A</em><sup>0 </sup>such that for all 0 ≤ <em>i &lt; n </em>and 0 ≤ <em>j &lt; m</em>, <em>A</em><sup>0</sup>(<em>i,j</em>) = <em>A</em>(<em>j,i</em>). For example, if

(1)

then

 0     0     3 

<em>A</em>0 =  9    0   8 <sub>                                                                             </sub>(2)

 0     1     0 

1    0    0

Let <em>k </em>denote the number of non-zero entries in <em>m</em>×<em>n </em>matrix <em>A </em>(in the above example, <em>k </em>= 5). We say that a matrix <em>A </em>is <em>sparse </em>if <em>k </em>= <em>o</em>(<em>mn</em>). Clearly, it is more efficient to store a sparse matrix using a special data structure, instead of storing it as a 2-dimensional array. One common data structure is known as the <em>compressed sparse-row </em>(CSR) representation.

In CSR representation, matrix <em>A </em>is stored using three arrays: <em>R</em>, <em>C</em>, and <em>V </em>. These arrays are respectively of length <em>m </em>+ 1, <em>k</em>, and <em>k</em>. The array <em>C </em>stores the column indices of the non-zeros, such that for each 0 ≤ <em>i </em>≤ <em>m</em>−1, the subarray <em>C</em>[<em>R</em>[<em>i</em>]<em>..R</em>[<em>i</em>+1]−1] stores the column indices of the <em>i</em>th row of <em>A</em>, in increasing order (for convenience, the indexing of the arrays starts from 0). For each <em>C</em>[<em>j</em>], <em>V </em>[<em>j</em>] stores the value of the corresponding non-zero entry, i.e., if <em>R</em>[<em>i</em>] ≤ <em>j &lt; R</em>[<em>i</em>+1], then <em>V </em>[<em>j</em>] = <em>A</em>(<em>i,C</em>[<em>j</em>]). For example, the CSR representation of matrix <em>A </em>in Equation (1) is as follows:

<em>R </em>=        <em>&lt; </em>0<em>,</em>2<em>,</em>3<em>,</em>5 <em>&gt;</em>

<em>C </em>=         <em>&lt; </em>1<em>,</em>3<em>,</em>2<em>,</em>0<em>,</em>1 <em>&gt;                                                                              </em>(3)

<em>V </em>=         <em>&lt; </em>9<em>,</em>1<em>,</em>1<em>,</em>3<em>,</em>8 <em>&gt;</em>

For this problem, you are asked to write the algorithm for transposing a matrix in CSR representation. In other words, write the pseudo-code of procedure Sparse-Transpose(<em>R,C,V,m,n,k</em>) that will return arrays <em>R</em><sup>0</sup>, <em>C</em><sup>0</sup>, and <em>V </em><sup>0</sup>, representing the transpose of the matrix represented by <em>R</em>, <em>C</em>, and <em>V </em>in row major format. For example, if your procedure is called with the <em>R</em>, <em>C</em>, and <em>V </em>in Equation (3), it should return:

<em>R</em><sup>0 </sup>=        <em>&lt; </em>0<em>,</em>1<em>,</em>3<em>,</em>4<em>,</em>5 <em>&gt;</em>

<em>C</em><sup>0 </sup>=         <em>&lt; </em>2<em>,</em>0<em>,</em>2<em>,</em>1<em>,</em>0 <em>&gt;                                                                              </em>(4)

<em>V </em><sup>0 </sup>=        <em>&lt; </em>3<em>,</em>9<em>,</em>8<em>,</em>1<em>,</em>1 <em>&gt;</em>

which is the row-major representation of <em>A</em><sup>0 </sup>in Equation (2). Your algorithm should work in <em>O</em>(<em>m </em>+ <em>n </em>+ <em>k</em>) time. (<em>Hint: </em>The algorithm can be thought of as a generalization of CountingSort).