# DFS-User-input


import java.io.*;
import java.util.*;
  

class Graph {
    private int V; 
    private LinkedList<Integer> adj[];
 
   
     Graph(int v)
    {
        V = v;
        adj = new LinkedList[v];
        for (int i = 0; i < v; ++i)
            adj[i] = new LinkedList();
    }
 
    
    void addEdge(int v, int w)
    {
        adj[v].add(w); 
    }
 
    
    void DFSUtil(int v, boolean visited[])
    {
       
        visited[v] = true;
        System.out.print(v + " ");
 
        
        Iterator<Integer> i = adj[v].listIterator();
        while (i.hasNext()) {
            int n = i.next();
            if (!visited[n])
                DFSUtil(n, visited);
        }
    }
 
   
    void DFS()
    {
       
        boolean visited[] = new boolean[V];
 
        
        for (int i = 0; i < V; ++i)
            if (visited[i] == false)
                DFSUtil(i, visited);
    }
 
    
    public static void main(String args[])
    {
        
        	Scanner sc = new Scanner(System.in);
		
		System.out.println("Enter number of vertices and edges");
		
		int v = sc.nextInt();
		int e = sc.nextInt();
		
		Graph g = new Graph(v);
		System.out.println("Enter "+ e +" edges");
		for(int i = 0; i<e; i++) {
			int a = sc.nextInt();
			int w = sc.nextInt();
			
			g.addEdge(a,w);
		} 
		
		System.out.println("Enter source and destination");
		
		int a = sc.nextInt();
		int w = sc.nextInt();
        
 
        System.out.println("Following is Depth First Traversal");
 
        g.DFS();
    }
