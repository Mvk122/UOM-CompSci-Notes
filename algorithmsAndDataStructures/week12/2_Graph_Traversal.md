# Graph Traversal
* In a directed graph where all nodes are connected directly or by proxy to a given starting node, we can traverse the graph to reach all nodes in the graph using a simple algorithm: 
```python
discovered_nodes = []
to_discover = [Node(0)]

while len(to_discover) > 0:
	current = to_discover.get()
	to_discover.remove(current)
	discovered_nodes.add(current)
	for node in current.children:
		if node not in discovered_nodes:
			to_discover.add(node)
```
* The above can be converted to a `Breadth First Search` by using a FIFO queue.
* The above can be converted to a `Depth First Search` by using a LIFO structure like a stack.

## DFS using recursion
* Instead of using a separate list for the nodes to be discovered, the call stack can be used instead for DFS: 
```python
def DFS(node):
	for n in node.children:
		if not n.discovered:
			DFS(n)
	node.discovered = True
```