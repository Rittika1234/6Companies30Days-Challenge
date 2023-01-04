# Number of Ways to Arrive at Destination

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/)



### Solution
```java
class Solution {
    static int mod = (int)(Math.pow(10, 9)+7);
    class Pair{
        int node, wt;
        public Pair(int node, int wt){
            this.node = node;
            this.wt = wt;
        }
    }
    public int countPaths(int n, int[][] roads) {
        ArrayList<ArrayList<Pair>> adj = new ArrayList<>();
        for(int i = 0; i< n; i++){
            adj.add(new ArrayList<>());
        }

        for(int[] e: roads){
            adj.get(e[0]).add(new Pair(e[1], e[2]));
            adj.get(e[1]).add(new Pair(e[0], e[2]));
        }

        PriorityQueue<Pair> pq = new PriorityQueue<>((a, b)-> a.wt- b.wt);
        pq.offer(new Pair(0, 0));
        int[] dist = new int[n];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[0] = 0;


        int[] count = new int[n];
        count[0] = 1;
        while(!pq.isEmpty()){
            Pair front = pq.poll();

            for(Pair e: adj.get(front.node)){

                if(e.wt+ front.wt < dist[e.node]){
                    dist[e.node] = e.wt+ front.wt;
                    pq.offer(new Pair(e.node, dist[e.node]));
                    count[e.node] = count[front.node];
                }
                else if(e.wt+ front.wt == dist[e.node]){
                    count[e.node] = (count[e.node]+ count[front.node]) %mod;
                }
            }
        }
        return count[n-1]%mod;

    }
}
```

### Accepted
[![image](https://user-images.githubusercontent.com/98543049/210581854-481a4337-0529-4d32-84a9-deb95967465b.png)](https://leetcode.com/submissions/detail/871250490/)
