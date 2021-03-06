Problem one: Trains
 
The local commuter railroad services a number of towns in Kiwiland.  Because of monetary concerns, all of the tracks are 'one-way.'  That is, a route from Kaitaia to Invercargill does not imply the existence of a route from Invercargill to Kaitaia.  In fact, even if both of these routes do happen to exist, they are distinct and are not necessarily the same distance!
 
The purpose of this problem is to help the railroad provide its customers with information about the routes.  In particular, you will compute the distance along a certain route, the number of different routes between two towns, and the shortest route between two towns.
 
Input:  A directed graph where a node represents a town and an edge represents a route between two towns.  The weighting of the edge represents the distance between the two towns.  A given route will never appear more than once, and for a given route, the starting and ending town will not be the same town.
 
Output: For test input 1 through 5, if no such route exists, output 'NO SUCH ROUTE'.  Otherwise, follow the route as given; do not make any extra stops!  For example, the first problem means to start at city A, then travel directly to city B (a distance of 5), then directly to city C (a distance of 4).
1.	The distance of the route A-B-C.
2.	The distance of the route A-D.
3.	The distance of the route A-D-C.
4.	The distance of the route A-E-B-C-D.
5.	The distance of the route A-E-D.
6.	The number of trips starting at C and ending at C with a maximum of 3 stops.  In the sample data below, there are two such trips: C-D-C (2 stops). and C-E-B-C (3 stops).
7.	The number of trips starting at A and ending at C with exactly 4 stops.  In the sample data below, there are three such trips: A to C (via B,C,D); A to C (via D,C,D); and A to C (via D,E,B).
8.	The length of the shortest route (in terms of distance to travel) from A to C.
9.	The length of the shortest route (in terms of distance to travel) from B to B.
10.	The number of different routes from C to C with a distance of less than 30.  In the sample data, the trips are: CDC, CEBC, CEBCDC, CDCEBC, CDEBC, CEBCEBC, CEBCEBCEBC.
 
Test Input:
For the test input, the towns are named using the first few letters of the alphabet from A to D.  A route between two towns (A to B) with a distance of 5 is represented as AB5.
Graph: AB5, BC4, CD8, DC8, DE6, AD5, CE2, EB3, AE7
Expected Output:
Output #1: 9<p>
Output #2: 5<p>
Output #3: 13<p>
Output #4: 22<p>
Output #5: NO SUCH ROUTE<p>
Output #6: 2<p>
Output #7: 3<p>
Output #8: 9<p>
Output #9: 9<p>
Output #10: 7<p>


## Application <p>
## 设计思路:
1.将每个字母作为Town的唯一标识，这些Town的集合信息通过读取townLine.properties获取<p>
2.将获取的Town集合信息转为二维矩阵，这里就涉及到如何将每个Town与二维矩阵的每行的index进行匹配起来;<p>
我们将Town集合数据放进到TreeSet之中，然后遍历这些Town（每次遍历出来顺序都是一致的），最先出来的Town就对应的二维矩阵行和列
的index都为0，其他依次类推。这样就把Town的信息与二维距阵的index就匹配起来了<p>
3.通过深度优先算法查找各线路方案，迪特斯特拉算法不能解决有回路的情况所以没有采用<p>

## 使用测试 <p>
通过运行test模块下com.tw.trains.test包的test case
