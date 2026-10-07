---
title: "Hash Tables"
---

## Overview
Hash tables offer very fast insertion and searching (close to O(1)) by using a hash function to map keys to array indices. They're essential when fast lookup is critical.

## How Hash Tables Work
1. **Hash Function**: Transforms keys into array indices
2. **Array Storage**: Data stored at computed index
3. **Collision Resolution**: Handle when multiple keys map to same index

## Hash Functions

### Good Hash Function Properties
- **Simple and Fast**: Quick to compute
- **Deterministic**: Same key always produces same index
- **Uniform Distribution**: Spreads keys evenly across table
- **Uses all key data**: Every part contributes to hash
- **Prime table size**: Helps avoid clustering

### Common Hash Functions
- **Division Method**: `index = key % tableSize`
- **Multiplication Method**: Using powers for strings
- **Folding**: Breaking key into groups and adding
- **Horner's Method**: Efficient for string hashing

## Collision Resolution Strategies

### Open Addressing
When collision occurs, find another open slot:

#### Linear Probing
- Check next slot sequentially: i+1, i+2, i+3...
- Simple but causes **primary clustering**
- Keep load factor < 0.5-0.67

#### Quadratic Probing
- Check slots at: i+1², i+2², i+3²...
- Eliminates primary clustering
- Suffers from **secondary clustering**

#### Double Hashing
- Use second hash function for step size
- Formula: `stepSize = constant - (key % constant)`
- Eliminates both primary and secondary clustering
- **Requires prime table size**

### Separate Chaining
- Each slot contains a linked list
- Colliding items added to list
- Can handle load factor > 1
- More memory overhead but simpler

## Load Factor
- `loadFactor = nItems / tableSize`
- Critical for performance
- Open addressing: Keep < 0.67
- Separate chaining: Can exceed 1.0

## Efficiency Analysis

### Linear Probing
- Successful search: `(1 + 1/(1-L)²)/2`
- Unsuccessful: `(1 + 1/(1-L))/2`
- Degrades rapidly at high load factors

### Double Hashing
- Successful: `-log₂(1-L)/L`
- Unsuccessful: `1/(1-L)`
- Better than linear probing

### Separate Chaining
- Average list length = load factor
- Search time: `1 + loadFactor/2`

## Rehashing
When table becomes too full:
1. Create larger array (usually 2x size)
2. Rehash all existing items
3. Insert into new positions
- Takes O(n) time

## Applications
- **Databases**: Index lookups
- **Caches**: Fast data retrieval
- **Compilers**: Symbol tables
- **Spell Checkers**: Dictionary lookups
- **Routers**: IP address lookups

## Advantages
- O(1) average case for insert/delete/search
- Simple to implement
- Very fast for exact match lookups

## Disadvantages
- No ordering of elements
- Performance degrades with high load factor
- Fixed size (resizing is expensive)
- Cache performance can be poor

## Implementation
- HashTableOpenAddressing.java: Double hashing with prime table sizes
