---
title: Hash Table
Tags: Public
Aliases: Hash Map
Date created: 2024-02-13 18:55
---

A hash table is an [[Associative Array]] data structure, meant for storing key-value pairs in a manner that allows quick lookup. It's principle is creating an array of values where the objects are input at locations determined by a hash function.

### Elements of a Hash Table
1. Hash function - a function responsible for [[Hashing]] the inputs and returning an integer index location in the array where the input will be stored
2. Array of hash buckets - the locations in the array are called buckets, they can hold one or more key-value pairs

### Mechanism

For any given key and value pair the hash function is applied to the key, and the result determines into which hash bucket should the key-value pair be inserted. 

This allows for O(1) access since we can directly go into the correct index when searching (by checking the hash of the key). 

### Collisions
When for two or more keys the hash function returns the same value, there is a collision. The question in such situation is where to store the second value

#### Chaining
In this solution each bucket contains a linked list (possibly another data structure), and the new key-value pair is appended at the end of such structure

#### Open Addressing
When a collision happens a new bucket is chosen according to a predefined algorithm

### Time Complexity
|Operation|Big-O|Note|
|---|---|---|
|Access|N/A|Accessing not possible as the hash code is not known|
|Search|O(1)*||
|Insert|O(1)*||
|Remove|O(1)*||

_* This is the average case, but in interviews we only care about the average case for hash tables._


### Hash Table Questions
[[Two Sum]]
[[Ransom Note (coding question)]]
[[Group Anagrams]]
[[Insert Delete GetRandom O(1)]]
[[First Missing Positive]]
[[LRU Cache]]
[[All O one Data Structure]]