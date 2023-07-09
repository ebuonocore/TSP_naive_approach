# TSP_naive_approach
A brutal solution to the problem of the travelling salesman.

Let be a list of cities such as:
```{python} 
cities = ["Paris", "Lyon", "Marseille", ...]
```
We have to explore all possible combinations and finds the shortest possible route that visits each city exactly once and returns to the city of origin.

As a first approach, we can imagine building a two-entry table to find out the cost of a route between each city.
![two-entries_table](/assets/TSP_two_entries_table.png)  

Each cell can be filled in by calling an API (OpenStreetMap, for example). The result is implemented by a dictionary.

```{python} 
cost = {
    "Paris": {"Paris": 0, "Lyon": 462.941, "Marseille": 772.335, ...},
    "Lyon": {"Paris": 462.941, "Lyon": 0, "Marseille": 312.659, ...},
    "Marseille": {"Paris": 772.335, "Lyon": 312.659, "Marseille": 0, ...},
    ...
}
```
From this same list of cities, we need to generate all the possible route combinations back to the city of origin. 
For example:
```{python} 
["Paris", "Lyon", "Marseille", ..., "Paris"]
...
["Paris", "Marseille", "Lyon" ..., "Paris"]
```
Now that we know the cost table and all the possible routes, all we have to do is find the route with the lowest cost.  
This is what a global schematic of the problem would look like.  

[![Top_diagram](/assets/TSP_diagram.svg)](/assets/TSP_diagram.svg)  
The last function will be responsible for systematically calculating the cost of each route.  
After that, we'll just have to take this top-down approach a step further by specifying each of the sub-functions more precisely.  

To find the distance between two towns, we'll need to call up the OpenStreetMap API, which will return the GPS coordinates for each town. Then we'll use it again to calculate the distance by car between two towns.

![diagram_v1](/assets/TSP_diagram_v1.svg)

To find the distance between two towns, we'll need to call up the OpenStreetMap API, which will return the GPS coordinates for each town. Then we'll use it again to calculate the distance by car between two towns.

![diagram_v2](/assets/TSP_diagram_v2.svg)

