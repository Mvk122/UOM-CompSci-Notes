# Hybrid Networks
* Where client server solutions are combined with decentralized architectures.

## Collaborative Distributed Systems
* Uses a traditional client-server architecture when nodes are joining the system and fully decentralised afterwards. Eg Torrents.
### Torrent Example
* A new node requesting a file accesses a global directory containing references to torrent files.
* Torrent files contain links to trackers which keep an accurate account of active nodes that have chunks of the requested file.
* The node uses the tracker to find other nodes to download the chunks from.
* The node downloads the files from the other nodes and optionally makes itself available through the tracker for other nodes to download the file from it.

## Edge-Server Systems
![[Pasted image 20230407190141.png]]
* Are servers deployed on the internet however they are at the edge (the boundary between enterprise networks and the internet).
* The edge server serves content. 
* Content is often a cached version of highly demanded content eg web pages.