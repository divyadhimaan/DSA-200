# Detect Cycle in an undirected graph - DFS

Practice [Link](https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card)

Given an undirected graph with V vertices and E edges, check whether it contains any cycle or not. 

![Alt text](/images/graph-b.png)
> No Cycle


![Alt text](/images/graph-a.png)
> Cycle exists

## Note
Graph can also be disconnected -> Check for every node as source/starting node.

Visited array cannot be the only check here since for DFS the adjacent node can also be the parent node itself, which will always be visited.

## Intiution
- Start from one node(unvisited) and explore all nodes, keep track of rhe parent node.
- Use visited array to keep track of explored nodes.
- For every node, iterate over the adjacent nodes
  - If not visited, call dfs() on the node and return true if its true.
  - If not visited, and the node is not the parent df current node -> cycle exists.
- Return false


## Implementation

```
void bfsOfGraphUtil(vector<vector<int>> &adj, vector<int> &ans, vector<bool> &visited)
    {
        queue<int> q;
        q.push(0);
        visited[0] = true;

        while(!q.empty())
        {
            int currNode = q.front();
            q.pop();
            
            ans.push_back(currNode);
            
            for(auto nextNode: adj[currNode])
            {
                if(!visited[nextNode]){
                    visited[nextNode]=true;
                    q.push(nextNode);
                }
            }
        }

    }
  
  
    // Function to return Breadth First Traversal of given graph.
    vector<int> bfsOfGraph(vector<vector<int>> &adj) {
        
        vector<int> ans;
        vector<bool> visited(adj.size(), false);
        bfsOfGraphUtil(adj, ans, visited);
        return ans;
        
    }
```


## Complexities

### Time Complexity: O(V+E) + O(N), 
We are exploring every vertex V and exploring all its edges. 
O(N) -> For covering disconnected components



### Space Complexity: O(N)+O(V+E), 
O(N) to keep visited nodes, and O(V+E) to create the adjacency list.