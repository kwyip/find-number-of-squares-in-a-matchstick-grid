<h1 align="center" style="display: block; font-size: 2.5em; font-weight: bold; margin-block-start: 1em; margin-block-end: 1em;">
  <br><br><strong>Find number of squares in a matchstick grid
</strong>
</h1>

![Latest release](https://img.shields.io/github/v/release/aregtech/areg-sdk?label=%20%F0%9F%93%A3%20Latest%20release&style=flat&logoColor=b0c0c0&labelColor=363D44)

---

<!-- markdownlint-disable -->
## Project Status 
<table class="no-border">
  <tr>
    <!--<td><img src="https://github.com/aregtech/areg-sdk/actions/workflows/c-cpp.yml/badge.svg" alt="C++ compiltation"/></td>-->
    <td><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="Sonarqube"/></td>
    <td><img src="https://img.shields.io/badge/Codeforces-445f9d?style=for-the-badge&logo=Codeforces&logoColor=white" alt="Sonarqube"/></td>
    <td><img src="https://github.com/aregtech/areg-sdk/actions/workflows/codeql-analysis.yml/badge.svg" atl="CodeQL"/></td>
  </tr>
  <tr>
    <td><img src="https://img.shields.io/badge/Solution-Python-blue.svg?style=flat&logo=Python&logoColor=b0c0c0&labelColor=363D44" alt="Python solution"/></td>
    <td><img src="https://img.shields.io/badge/Environment-Jupyter%20notebook-orange"/></td>
    <td><img src="https://img.shields.io/badge/CPU-x86%20%7C%20x86__64%20%7C%20arm%20%7C%20aarch64-blue?style=flat&logo=amd&logoColor=b0c0c0&labelColor=363D44" alt="CPU Architect"/></td>
  </tr>
</table>

---

## Introduction[![](./docs/img/pin.svg)](#introduction)

**AREG SDK** is a developer-friendly, interface-centric real-time asynchronous communication engine to enable [distributed-](https://en.wikipedia.org/wiki/Distributed_computing) and [mist-](https://csrc.nist.gov/publications/detail/sp/500-325/final)computing, where connected Things interact and provide services, as if they act like thin distributed servers.


---

## Table of contents[![](./docs/img/pin.svg)](#table-of-contents)
1. [Motivation](#motivation)
2. [More than embedded](#more-than-embedded)
3. [Composition](#composition)
4. [Software build](#software-build)
5. [Software integration](#software-integration)
   - [Multicast router](#mulitcast-router)
   - [Logging service](#logging-service)
   - [Development](#development)
6. [Use cases and benefits](#use-cases-and-benefits)
   - [Distributes solutions](#distributed-solution)
   - [Driverless devices](#driverless-devices)
   - [Real-time solutions](#real-time-solutions)
   - [Digital twin](#digital-twin)
   - [Simulation and test automations](#simulation-and-test-automations)
7. [Examples](#examples)
8. [Licensing](#licensing)
9. [Call for action](#call-for-action)

---

## Motivation[![](./docs/img/pin.svg)](#motivation)

![Alt text](https://github.com/kwyip/find-number-of-squares-in-a-matchstick-grid/blob/main/screenshot_1.png) 
In the above figure, are you able to count how many squares in the 4 × 4 square grid? There are 16. In general, given any N × N matchstick grid comprised of matchsticks, we would like to find out a way to calculate the total number of squares from size 1 × 1 to N × N. (Inspired from this [puzzle](https://matchstickpuzzles.blogspot.com/2011/06/55-4x4-square-how-many-squares.html)).

## File Input format[![](./docs/img/pin.svg)](#FileInputformat)
The matchstick grid is encoded as two dimensional boolean arrays of size N × (N + 1).
The first array encodes the vertical-oriented matchsticks “I” in row-major order from the top-left corner, and the second array encodes the horizontal-oriented matchsticks “-” in column-major order also from the top-left corner.
A boolean value of “true” (1) indicates that a matchstick is present at that location, while a
boolean value of “false” (0) indicates that there is no matchstick at that location.

### Example:
![Alt text](https://github.com/kwyip/find-number-of-squares-in-a-matchstick-grid/blob/main/screenshot_3.png) 

This is equivalent to the input file of:
![Alt text](https://github.com/kwyip/find-number-of-squares-in-a-matchstick-grid/blob/main/screenshot_4.png) 


## Solution[![](./docs/img/pin.svg)](#Solution)
```
with open(‘sample_input.txt’) as f:
lines = f.readlines()
print(lines)
```

[‘4\n’, ‘\n’, ‘1 0 1 1 1\n’, ‘1 1 1 1 1\n’, ‘1 1 1 1 1\n’, ‘1 0 1 1 1\n’, ‘\n’, ‘1 1 1 0 1\n’, ‘1 1 1 1 1\n’, ‘1 1 1 1 1\n’, ‘1 1 1 0 1\n’]

`4` in the first means the size of matchstick grid. Now, let’s make two lists: `h_list` has dimension (n+1)x(n) and `v_list` has dimension (n)x(n+1), so both are counting matchsticks from top-left to bottom-right.

```
# Let's make two lists: h_list has dimension (n+1)x(n) and v_list has dimension (n)x(n+1), so both are counting matchsticks from top-left to bottom-right.
f = open('sample_input.txt', 'r')
content = f.read().splitlines()
size = int(content[0])
v_list = []
h_list = []
for v in range(2, size+2):
#temp = list(content[h].split(" "))
v_list.append([int(i) for i in list(content[v].split(" "))])
print(v_list)
for h in range(size+3, 2*size+3):
#temp = list(content[v].split(" "))
h_list.append([int(i) for i in list(content[h].split(" "))])
h_list = list(map(list, itertools.zip_longest(*h_list, fillvalue=None)))
print(h_list)
```
[[1, 0, 1, 1, 1], [1, 1, 1, 1, 1], [1, 1, 1, 1, 1], [1, 0, 1, 1, 1]] [[1, 1, 1, 1], [1, 1, 1, 1], [1, 1, 1, 1], [0, 1, 1, 0], [1, 1, 1, 1]]

Define the variable `M` and `N` as follows.

```
M = len(v_list[0])   #v_list: N x M
print(M)
N = len(h_list[0])   #h_list: M x N
print(N)
cuV = [[0]*len(v_list[0]) for _ in range(0, len(v_list))]
cuH = [[0]*len(h_list[0]) for _ in range(0, len(h_list))]
```

`cuV` stands for cumulative-V and `cuH` stands for cumulative-H. Next populate the `cuV` and `cuH`.


```
#cuV: N x M is to keep track of how many consecutive vertical bars it precedes.
for j in range(0, M):
    for i in range(0, N):
      if v_list[i][j]:
          if i == 0:
             cuV[i][j] = 1
          else:
             cuV[i][j] = cuV[i - 1][j] + 1
      else:
           cuV[i][j] = 0
print(cuV)
```

[[1, 0, 1, 1, 1], [2, 1, 2, 2, 2], [3, 2, 3, 3, 3], [4, 0, 4, 4, 4]]

```
#cuH: M x N is to keep track of how many consecutive horizontal bars it precedes.
for i in range(0, M):
    for j in range(0, N):
       if h_list[i][j]:
          if j == 0:
             cuH[i][j] = 1
          else:
             cuH[i][j] = cuH[i][j-1] + 1
       else:
          cuH[i][j] = 0
print(cuH)
```
[[1, 2, 3, 4], [1, 2, 3, 4], [1, 2, 3, 4], [0, 1, 2, 0], [1, 2, 3, 4]]

One way is to solve the problem is to use dynamic programming. The idea is illustrated in the following snippet.

```
# Start from the bottom right corner of the grid. Let's see if we can form square of length `l` at every (i, j) point.
# For the example of point (i = 2, j = 2):
# From h point of view, it is (2, 1):
#            *--------*----------*---------*--------*
#            |                   |         |        |
#            |                   |         |        |
#            *--------*(i-1,j)-*---------*--------*
#            |        |          |         |        |
#            |        |          |         |        |
#            *--------*----------*(i,j-1)----*--------*
#            |        |          |         |        |
#            |        |          |         |        |
#            *        *----------*---------*        *
#            |                   |         |        |
#            |                   |         |        |
#            *--------*----------*---------*--------*
#
#
# From v point of view, it is (1, 2):
#            *--------*----------*---------*--------*
#            |                   |         |        |
#            |                   |         |        |
#            *--------*(i-2,j-1)---*---------*--------*
#            |        |          |         |        |
#            |        |          |         |        |
#            *--------*----------*(i-1,j)*--------*
#            |        |          |         |        |
#            |        |          |         |        |
#            *        *----------*---------*        *
#            |                   |         |        |
#            |                   |         |        |
#            *--------*----------*---------*--------*
#
# For example, when we want to see if a square of length l can be formed at (i,j) point (from point of view of h). We want to see if:
# dH(i-s,j-1) >= s, dV(i-1,j-s) >= s, dH(i,j-1) >= s, dV(i-1,j) >= s
#
# We want to start with i=(N-1),j=(M-1) point, and iterate until i=0,j=0.
```

## Implementation
We want to be more ambitious. Why not along the algorithm also store the number of squares of size `s = 1 … size`?

```
outputlist = []
total = 0
for s in range(size, 0, -1):
   count=0
      for i in range((M-1), s-1, -1):
           for j in range((M-1), s-1, -1):
                condition = i-s>=0 and j-1>=0 and i-1>=0 and j-s >=0 and i >=0 and j-1>=0 and i-1 >= 0 and j >=0
                try:
                     if condition and cuH[i-s][j-1]>=s and cuV[i-1][j-s]>=s and cuH[i][j-1]>=s and cuV[i-1][j]>=s:
                         count+=1
                     except IndexError:
                         continue
      string = str(s)+' x '+str(s) +": "+str(count)+ '\n'
      outputlist.append(string)
      total += count
conclusion = 'Number of squares: ' + str(total)
outputlist.append(conclusion)
print(conclusion)
print(outputlist)
```
Number of squares: 16
[‘4 x 4: 1\n’, ‘3 x 3: 1\n’, ‘2 x 2: 5\n’, ‘1 x 1: 9\n’, ‘Number of squares: 16’]


## Conclusion

We implemented a dynamic-programming based algorithm in Python. This program will work for any size of N x N matchstick grid and any configuration of matchsticks. In addition to outputting the number of squares, this program will also count of the number of squares for each size, from 1 to N.

The whole Jupyter notebook is at:

https://github.com/kwyip/find-number-of-squares-in-a-matchstick-grid/


---
