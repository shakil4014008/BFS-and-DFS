# BFS-and-DFS

````c#
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
        
        
        

````
