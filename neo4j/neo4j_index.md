# Graph databases are cool
When we talk about Graph databases, Neo4j is the king. It is the most widely used graph database so far based on [db-engines](https://db-engines.com/en/ranking/graph+dbms).

But, what is a graph? Graphs are actually a mathematical concept created by Euler. If you have studied graphs in college or school, you are probably familiar (or at leas have heard of) the problem of the Koninsberg bridges. Let's take a look at the following image:

![Koninsberg Bridges](https://www.maa.org/sites/default/files/images/cms_upload/Konigsberg_colour37936.jpg)

## Bridges are burning down!
The short story goes around like this: _"Let's say I have a carriage (or a car to make it more up to date). Is there a way in which, starting from any piece of land, I can go through each bridge only once and finish where I started?"_

The short answer, is that no, it isn't possible. But why? Let's imagine each piece of land as a circle and each bridge as an arrow linking these circles. The result would be like this:

![Koninsberg Graph](https://wild.maths.org/sites/wild.maths.org/files/pictures/articles/bridges.jpg)

Euler reduced the problem to the connections between the circles. Basically, if you come in through one line, you have to move out through a different line. If that is the case, the only circles that can have an uneven quantity of lines coming in, are the first and the last circles (all the other must have an even quantity, other wise, at some point you will be able to go in but not out). As you see in the image above, the four circles have an uneven quantity of lines which determines that it is impossible to start at one circle and go through each bridge only one.

## Why do we care?
Graphs are awesome for a very specific situation: Finding relationships between entities (or the shortes ways, or all the different ways to get from point A to B). Sometimes, when you are in a SQL interview, they ask you to solve a problem with hierarchies. Let's imagine an Organization Chart with people. You have a CEO, Directors, Managers and the rest of the team. This organization chart can go as far as you want in terms of quantity of people. Let's say I want all people working under the "Director of Engineering", how would you solve that in SQL?

To begin with, you would probably start having a table like this:

EmployeeId | EmployeeName | Position | ManagerID
-----------|--------------|----------|-----------
1|Alex|CEO|NULL
2|Steve|Engineering Director|1
3|John|Developer Manager|2
4|Jas|Sr Dev|3
5|Tony|DBA|3

and so on...

If you want a query to go through the whole tree, you have to use recursivity. In SQL, recursiveness is generally solved through CTEs (or Common Table Expressions). Some SQL Engines, have solutions for this but in general, you should know that this is a very expensive, very slow resolution. And it is no SQL's fault, since it wasn't really designed for this. In general, for small trees, SQL is ok, but if you want to be able to run through a tree with hundreds of thousands of leafs, then you are probably in trouble.

This is where Neo4j and graph databases start being awesome. Queries are much simpler since they are specifically designed for this, and also, data is stored in a way that the resoultion and resource usage is more cost/effective for this kind of issues.

Graphs are also used for navigation in maps, fraud detection and many more things. If you aren't using graphs, there is probably at least one or more analysis that could benefit from it.

For now, I'll leave it at that.