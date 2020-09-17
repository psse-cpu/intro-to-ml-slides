Non-learning Algorithms:  A* Search
-----------------------------------



### What is it?

* Finds the shortest path
  - originally a graph algorithm

![romania](images/romania.png)




### But can be used in grids as well

* Adjacent tiles replace graph child-nodes
  - since this batch are game experts, we'll practice A* on grids

![A*](images/a-star.png)



#### Let's first study the algorithm on a graph

- it's an example of an informed search
- DFS and BFS are blind searches

![A*](images/sample-a-star.png)



#### Cost functions (1/5)

- Each node has two parameters for its _cost_ function
  + **g** measures travel distance to its adjacent node
  + **h** (heuristic function) estimates the distance to the goal

![A*](images/sample-a-star.png)



#### Cost functions (2/5)

- The two values help _"tie-break"_ one another
  + **g** in most cases, is not an estimate
  + **h** can simply be _"as-the-bird-flies"_ straight-line distance

![A*](images/sample-a-star.png)



#### Cost functions (3/5)

- **g** can break ties when heuristic estimate is tied
  + **c** and **d** are both 18 units from **z**
  + but shorter travel from **a** to **c**

![A*](images/sample-a-star.png)



#### Cost functions (4/5)

- **h** can break ties when actual distance is the same
  + very obvious in grids
    - distance from **x** to horizontal and vertical adjacents is 10
    - distance from **x** to diagonals is 14
    - we just use Pythagorean, `int`s easier to reason about, faster
    - $ \sqrt{10^2 + 10^2} \approx 14 $

<table style="border: 1px solid black; margin-top: 32px">
<tr style="border: 1px solid black">
  <td style="border: 1px solid black">
    14
  </td>
  <td style="border: 1px solid black">
    10
  </td>
  <td style="border: 1px solid black">
    14  
  </td>
</tr>
<tr style="border: 1px solid black">
  <td style="border: 1px solid black">
    10
  </td>
  <td style="border: 1px solid black; text-align: center; color: darkred">
    x
  </td>
  <td style="border: 1px solid black">
    10
  </td>
</tr>
<tr style="border: 1px solid black">
  <td style="border: 1px solid black">
    14
  </td>
  <td style="border: 1px solid black">
    10
  </td>
  <td style="border: 1px solid black">
    14
  </td>
</tr>
</table>



#### Cost functions (5/5)

- **h** can break ties when actual distance is the same
  + when the goal is to the right of **x**
    - the 3 adjacent cells to its left will have a larger **h**
    - the vertical cells above and below it will have a larger **h**
    - **50** vs. $ \sqrt{10^2 + 50^2} \approx 51 $

<table style="border: 1px solid black; margin-top: 32px">
<tr style="border: 1px solid black">
  <td style="border: 1px solid black">
    14
  </td>
  <td style="border: 1px solid black">
    10
  </td>
  <td style="border: 1px solid black">
    14
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
</tr>
<tr style="border: 1px solid black">
  <td style="border: 1px solid black">
    10
  </td>
  <td style="border: 1px solid black; text-align: center; color: darkred">
    x
  </td>
  <td style="border: 1px solid black">
    10
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
  <td style="border: 1px solid black; color: blue">
    G
  </td>
</tr>
<tr style="border: 1px solid black">
  <td style="border: 1px solid black">
    14
  </td>
  <td style="border: 1px solid black">
    10
  </td>
  <td style="border: 1px solid black">
    14
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
  <td style="border: 1px solid black">
    &nbsp;&nbsp;
  </td>
</tr>
</table>



### Overview of A* on a graph

![A*](images/a-star.gif)

* Cost of each node is `f = g + h`



### A* Demo on Graph (1/5)

![A*](images/orig-graph.png)

<pre>
Q = [S(7)]
</pre>



### A* Demo on Graph (2/5)

![A*](images/orig-graph.png)

```
Q = [SA(3+9), SD(2+5)]
Q = [SA(12),  SD(7)]
```



### A* Demo on Graph (2/5)

![A*](images/orig-graph.png)

```
Q = [SA(3+9), SDB(3+4), SDE(6+3)]
Q = [SA(12),  SDB(7), SDE(9)]
```



### A* Demo on Graph (3/5)

![A*](images/orig-graph.png)

```
Q = [SA(3+9), SDE(6+3), SDBC(5+2), SDBE(4+3)]
Q = [SA(12),  SDE(9),   SDBC(7), SDBE(7)]
```



### A* Demo on Graph (4/5)

![A*](images/orig-graph.png)

```
Q = [SA(3+9), SDE(6+3), SDBE(4+3), SDBCG(9+0)]
Q = [SA(12),  SDE(9),   SDBE(7),   SDBCG(9)]
```



### A* Demo on Graph (4/5)

![A*](images/orig-graph.png)

```
Q = [SA(3+9), SDE(6+3), SDBCG(9+0), SDBEG(7+0)]
Q = [SA(12),  SDE(9),   SDBCG(9),   SDBEG(7)]
```



### A* Demo on Graph (5/5)

![A*](images/orig-graph.png)

```
Q = [SA(12),  SDE(9),   SDBCG(9)]
popped == goal, path is S➡D➡B➡E➡G
```



## Demo for A* on a grid is on the video