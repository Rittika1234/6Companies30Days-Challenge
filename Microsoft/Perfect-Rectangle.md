# Perfect Rectangle


[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/perfect-rectangle/)

Given an array rectangles where rectangles[i] = [xi, yi, ai, bi] represents an axis-aligned rectangle. The bottom-left point of the 
rectangle is (xi, yi) and the top-right point of it is (ai, bi).

Return true if all the rectangles together form an exact cover of a rectangular region.

### Example 1
![perectrec1-plane](https://user-images.githubusercontent.com/98543049/210233282-e7cf94ae-0587-4845-8e66-821b2a371f92.jpg)

```
Input: rectangles = [[1,1,3,3],[3,1,4,2],[3,2,4,4],[1,3,2,4],[2,3,3,4]]
Output: true
Explanation: All 5 rectangles together form an exact cover of a rectangular region.
```
### Example 2
![perfectrec2-plane](https://user-images.githubusercontent.com/98543049/210233368-f970e139-ea78-4ef4-970e-20f51975990a.jpg)

```
Input: rectangles = [[1,1,2,3],[1,3,2,4],[3,1,4,2],[3,2,4,4]]
Output: false
Explanation: Because there is a gap between the two rectangular regions.
```
### Example 3
![perfecrrec4-plane](https://user-images.githubusercontent.com/98543049/210233408-e9f91d76-8a6a-4e78-b1d6-16cd25e4052f.jpg)

```
Input: rectangles = [[1,1,3,3],[3,1,4,2],[1,3,2,4],[2,2,4,4]]
Output: false
Explanation: Because two of the rectangles overlap with each other.
```

### Solution
```java
class Solution {
    public boolean isRectangleCover(int[][] rectangles) {
        int X1 = Integer.MAX_VALUE, 
        Y1 = Integer.MAX_VALUE, 
        X2 = Integer.MIN_VALUE, 
        Y2 = Integer.MIN_VALUE;
        
        Set<String> points = new HashSet<>();
        int actual_area = 0;
        
        for(int[] item : rectangles){
            int x1 = item[0], 
            y1 = item[1], 
            x2 = item[2], 
            y2 = item[3];
            
            X1 = Math.min(X1, x1);
            Y1 = Math.min(Y1, y1);
            X2 = Math.max(X2, x2);
            Y2 = Math.max(Y2, y2);
            
            actual_area += (x2-x1)*(y2-y1);
            int[] p1 = new int[]{x1,y1};int[] p2 = new int[]{x1,y2};
            int[] p3 = new int[]{x2,y1};int[] p4 = new int[]{x2,y2};
            for(int[] p : new int[][]{p1,p2,p3,p4}){
                String s = p[0] + "," + p[1];
                if(points.contains(s)){
                    points.remove(s);
                }else{
                    points.add(s);
                }
            }
        }
        int expected_area = (X2-X1)*(Y2-Y1);
        if(actual_area != expected_area){
            return false;
        }
        if(points.size() != 4) return false;
        String s1 = X1 + "," + Y1;
        String s2 = X1 + "," + Y2;
        String s3 = X2 + "," + Y1;
        String s4 = X2 + "," + Y2;
        if(!points.contains(s1)) return false;
        if(!points.contains(s2)) return false;
        if(!points.contains(s3)) return false;
        if(!points.contains(s4)) return false;
        return true;
    }
}
```

### Accepted
[![image](https://user-images.githubusercontent.com/98543049/210233677-663da3dc-2f2e-4644-8d0d-2e92078eec63.png)](https://leetcode.com/submissions/detail/869688470/)
