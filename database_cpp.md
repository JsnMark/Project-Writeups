## The Problem

The goal was to build a working database engine in C++, backed by B+ tree indexes and supporting core operations such as insert, delete, update, and join. 

## The Approach

The project was built bottom up, starting from the file ios all the way to the high level relational operators.

## The Hard Parts

The hardest bugs showed up during page splitting, but only after thousands of pages had been written, which made them miserable to track. Tracing them back, the root cause wasn't necessarily the splitting logic. It was due to my poor planning in earlier parts of the project that caused me to write code without clear abstractions and modular functionalities. As a result, every new change I made felt more like a quick hack rather than an elegant solution. Looking back, I now realize that this is one of my first experiences with technical debt. Because I didn’t carefully consider the entire system as a whole early in development, I had to eventually pay the price and deal with the unkept code.

## Results

## Lessons
