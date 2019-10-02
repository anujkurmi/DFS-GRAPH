# DFS-GRAPH
#include<bits/stdc++.h>
using namespace std;
class graph
{
    unordered_map<int,list<int>> adja;
public:
    int component=0;
    void addedge(int src,int dest)
    {
        adja[src].push_back(dest);
        adja[dest].push_back(src);
    }

   void dfshelper(int v,unordered_map<int,bool> &visited)
    {
        visited[v]=true;
        for(auto neighbour:adja[v])
        {
            if(!visited[neighbour])
                dfshelper(neighbour,visited);
        }
    }
   void dfs()
   {   unordered_map<int,bool> visited;
        component=0;
        for(auto j:adja)
        {if(!visited[j.first])
        {
            component++;
            dfshelper(j.first,visited);
        }
        }
        cout<<component<<"\n";
    }

};
void f()
    {   graph g;
        int n,m,a,b;
        cin>>n>>m;
        for(int i=0;i<n;i++)
            g.addedge(i,i);
        while(m--)
        {
            cin>>a>>b;
            g.addedge(a,b);
        }
        g.dfs();
}
int main()
{  ios_base::sync_with_stdio(false);
cin.tie(NULL);
cout.tie(NULL);
    int T;
    cin>>T;
    while(T--)
    {
        f();
    }
    return 0;
}
