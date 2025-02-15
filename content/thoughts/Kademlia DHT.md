---
title: "Kademlia DHT"
date: 2022-06-07
tags:
- seed
---

Summarization of the [Kademlia paper](https://pdos.csail.mit.edu/~petar/papers/maymounkov-kademlia-lncs.pdf)

> A [[thoughts/peer-to-peer|peer-to-peer]] distributed hash table ([[thoughts/DHT|DHT]])

Participating computers each have a node ID in the 160-bit key space. Key-value pairs are stored on nodes with IDs "close" to the key for some notion of closeness. A node-ID-based routing algorithm lets anyone efficiently locate servers near any given target key.

Core ideas
- Uniform ID Space: names for both data and nodes share the same ID space
	- But collisions are ok as they mean different things depending on the context
- Decide what machine to place data on depending on a measure of 'closeness' between the name of the data and name of a machine
	- Euclidean distance can be ambiguous, two entries could have the same distance
	- XOR distance between $x$ and some arbitrary $y$ will *always* be unique
- Each node only needs information about its neighbours.
	- If the structure of the network is correctly chosen, then global properties apply to the whole network
	- Nested routing similar to [[thoughts/IP Addresses|IP]] routing
	- Each machine has a lot of info about machines closest to it, less about machines far away from it