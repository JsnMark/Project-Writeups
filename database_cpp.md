## The Problem

The goal was to build a working relational database engine in C++, backed by B+ tree indexes and supporting core operations such as insert, delete, update, and join. 

## The Approach

The project was built bottom up, starting from the file I/Os all the way to the high level relational operators. My most used strategy to approach this project was using a pen and paper to draw the page layout. For example, I would start with the data records on the top, then create a footer and slot directory at the bottom. I would trace through the steps of operations such as inserting a record at the end of the data records, or coalescing the records after a delete. This felt similar to my coursework in data structures and algorithms, but with a sprinkle of dealing with physical limitations such as cache locality and memory pages. 

Being able to visualize how the data pages and B+ tree change over time helped me better understand the underlying mechanisms and the tradeoffs a database has to make. One thing that surprised me the most was learning about how records can be stored. If every data attribute type is fixed in length, like an int32, then our lives would be so easy as we could just store data in an array like structure. However, variable length data types like strings turned out to be a pain to work with. In most relational databases, you are able to specify the maximum length of string a attribute can hold such as "VARCHAR(64)". Does this mean we should reserve 64 bytes for each data entry? Is there room to save space? If we decide to save space, how do we know when the next attribute starts? What about null values? As you can see, a simple problem of storing values quickly becomes convoluted once we introduce variable length data types. There are a few solutions to this problem, but I implemented a directory at the front of the data entry, with each pointer pointing to the end of the attribute.

## The Hard Parts

The hardest bugs showed up during page splitting, but only after thousands of pages had been written, which made them miserable to track. Tracing them back, the root cause wasn't necessarily the splitting logic. It was due to my poor planning in earlier parts of the project that caused me to write code without clear abstractions and modular functionalities. As a result, every new change I made felt more like a quick hack rather than an elegant solution. Looking back, I now realize that this is one of my first experiences with technical debt. Because I didn’t carefully consider the entire system as a whole early in development, I had to eventually pay the price and deal with the unkept code.

## Results

## Lessons
