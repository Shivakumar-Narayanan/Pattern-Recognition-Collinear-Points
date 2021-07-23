# Pattern-Recognition-Collinear-Points
Recognizing line patterns in a set of points.  
Part of Algorithms - Part-1, Princeton University.

Computer vision involves analyzing patterns in visual images and reconstructing the real-world objects that produced them. The process is often broken up into two phases: feature detection and pattern recognition. Feature detection involves selecting important features of the image; pattern recognition involves discovering patterns in the features.Following is a particularly clean pattern recognition problem involving points and line segments. This kind of pattern recognition arises in many other applications such as statistical data analysis. 

The problem : Given a set of n distinct points in the plane, find every (maximal) line segment that connects a subset of 4 or more of the points.  

Brute Force : examine every combination of 4 points and check if they form a line segment. Return all such line segments.

A faster, sorting-based solution : It is possible to solve the problem much faster than the brute-force solution described above. Given a point p, the following method determines whether p participates in a set of 4 or more collinear points :
    
    Think of p as the origin.

    For each other point q, determine the slope it makes with p.

    Sort the points according to the slopes they makes with p.

    Check if any 3 (or more) adjacent points in the sorted order have equal slopes with respect to p. If so, these points, together with p, are collinear.
    
Applying this method for each of the n points in turn yields an efficient algorithm to the problem. The algorithm solves the problem because points that have equal slopes with respect to p are collinear, and sorting brings such points together. The algorithm is fast because the bottleneck operation is sorting.   

Time Complexity : O(n^2 * log(n)), where n is the number of points.   
  Reason : for every point p, the slope is calculated for every other point with p as origin, which takes O(n) time. then these slopes are sorted, which is an O(nlogn)     operation. Then grouping 3 consequetive points with same slope takes O(n). Overall, for each point it takes O(n) + O(nlogn) + O(n) = O(nlogn). Doing the same for each of the n points results in O(n * nlogn) = O(n^2 * log(n)).  
  
Space Complexity : O(n + number of line segments returned).  
  
Point.java : An immutable data type Point that represents a point in the plane.  
LineSegment.java : present in algs4.jar.  
FastCollinearPoints.java : implementation of the algorithm.
