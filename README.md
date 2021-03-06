## Insight Twitter Graph: Coding Challenge
===========================================================
Kevin Wang  
UC Berkeley  
Materials Science & Engineering

## Required Packages

- Python 3.4+
- NetworkX (1.10)
- [native to Python]  
  - datetime
  - JSON
  - sys

Cleans Twitter text, extract hashtags from JSON, and builds graph. Trims graph to within a time window of the most-recently processed message. **Run with: run.sh.** Script calls made with: **python3** (eg. *python3 average_degree.py in.txt out.txt 30*)  
Program prints to shell output, the filename of the second script output: f2.txt.

**Input**: tweet_input/tweets.txt  {List of JSON Tweet objects}  
**Output**: tweet_output/ft1.txt   {Cleaned text + # of tweets wtih Unicode}  
        tweet_output/ft2.txt   {Average graph degree, after each tweet}

## Feature 1 (Cleaning Text): 

Usage:
```
tweets_cleaned.py filein fileout
```

Removes Unicode chars > ASCII 127. Replaces whitespace and escape chars. Performed with native Python string operations.

## Feature 2 (Graph of Hashtags, Find Node Degree): 

Usage: 
```
average_degree.py filein fileout timewindow
```

  - --timewindow: the number of seconds window that the graph should contain, up until the most recently read Tweet. (Default is 60s)

# Summary
The graph is built with NetworkX default implementation (regular Python dictionaries). Speed is not great, because the program iterates through the entire (unsorted) dictionary. An improved version of this would used a Sorted List of edges (by time), so you can stop the iteration once you reach nodes/edges within the time window. This would achieve a speed up for a large number of nodes and high connectivity/degree in edges.

I began implementing a version overloading NetworkX with LastUpdatedOrderedDict rather than the regular dict. This works for Nodes, but the real issue lies in traversing the list of edges.



