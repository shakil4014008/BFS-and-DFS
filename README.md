# BFS-and-DFS

````c#
BFS and DFS differences and complexity; 
1. BFS uses queue or level ordering or FIFO process, and DFS uses stack or LIFO for traversing the graph
2. 

Algorithms:

BFS-B(G,s)
    for all v in V[G] do
      visited[v] := false
    end for
    Q := EmptyQueue
    visited[s] := true
    Enqueue(Q,s)
    while not Empty(Q) do
      u := Dequeue(Q)
      for all w in Adj[u] do
        if not visited[w] then
        visited[w] := true
        Enqueue(Q,w)
      end if
    end while
    
    
   DFS-A(G,s)
        for all v in V[G] do
          visited[v] := false
        end for
        S := EmptyStack
        Push(S,s)
        while not Empty(S) do
          u := Pop(S)
          if not visited[u] then
            visted[u] := true
            for all w in Adj[u] do
              if not visited[w] then
                Push(S,w)
              end if
            end for
          end if
        end while
        
        
        BFS and DFS code: 
        
        class Graph
    {
        int vertices;
        List<int>[] adj;

        public Graph(int nodes)
        {
            vertices = nodes;
            adj = new List<int>[vertices];

            for (int i = 0; i < nodes; i++)
            {
                adj[i] = new List<int>();
            }
        }

        //add edge from u -> v
        public void AddEdge(int u, int v)
        {
            adj[u].Add(v);
        }

        public void BFS(int s)
        {
            bool[] visited = new bool[vertices];
            for (int i = 0; i < vertices; i++)
            {
                visited[i] = false;
            }

            Queue<int> queue = new Queue<int>();
            visited[s] = true;
            queue.Enqueue(s);
            //Console.Write(s + " ");

            while (queue.Count != 0)
            {
                s = queue.Dequeue();
                Console.Write(s + " ");
                foreach (var next in adj[s])
                {
                    if (!visited[next])
                    {
                        visited[next] = true;
                        queue.Enqueue(next);
                    }
                }
            }
        }

        public void DFS(int s)
        { 
            bool[] visited = new bool[vertices];

            for (int i = 0; i < vertices; i++)
            {
                visited[i] = false;
            }

            Stack<int> stack = new Stack<int>();
            visited[s] = true;
            stack.Push(s);

            while (stack.Count != 0)
            {
                s = stack.Pop();
                Console.Write(s + " ");

                foreach (var next in adj[s])
                {
                    if (!visited[next])
                    { 
                        visited[next] = true;
                        stack.Push(next);
                    } 
                }
            }
        }

        public void PrintAdjMatrix()
        {
            for(int i=0; i<vertices; i++)
            {
                Console.Write(i + ":[");
                string s = "";

                foreach(var k in adj[i])
                {
                    s = s + (k + ",");
                }
                s = s.Substring(0, s.Length - 1);
                s = s + "]";
                Console.Write(s);
                Console.WriteLine();
            }
        }
        static void Main(string[] args)
        {
            var g = new Graph(4);
            g.AddEdge(0, 1);
            g.AddEdge(0, 2);
            g.AddEdge(1, 2);
            g.AddEdge(2, 0);
            g.AddEdge(2, 3);
            g.AddEdge(3, 3);
            g.PrintAdjMatrix();
            int root = 2;

            Console.WriteLine("BFS traversal starting from " + root);
            g.BFS(root);
            Console.WriteLine();
            Console.WriteLine("DFS traversal starting from " + root);
            g.DFS(root); 
            Console.ReadLine();
        }  
    } 
        

````
