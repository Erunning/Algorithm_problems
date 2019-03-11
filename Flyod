```cpp
#include <bits/stdc++.h>
#define inf 0x3f3f3f3f
using namespace std;
int G[105][105];
int n,m;
int next[105][105];
void init()
{
    cin>>n>>m;
    for(int i=0; i<=n; i++)//初始化
    {
        for(int j=0; j<=n; j++)
        {
            if(i==j)
                G[i][j]=G[j][i]=0;
            else G[i][j]=G[j][i]=inf;
        }
    }
    for(int i=0; i<m; i++)
    {
        int x,y,w;
        cin>>x>>y>>w;
        if(G[x][y]>w)//有些题目给重复路径
            G[x][y]=G[y][x]=w;
    }
}
void printpath(){
    int st=1,ed=n;
    while(st!=ed){
        cout<<st<<"->";
        st=next[st][ed];
    }
    cout<<ed<<endl;
}
void Floyd()
{
    for(int i=1; i<=n; i++)//初始化路径
        for(int j=1; j<=n; j++)
            next[i][j]=j;
 
    for(int k=1; k<=n; k++)
        for(int i=1; i<=n; i++)
            for(int j=1; j<=n; j++)
                if(G[i][j]>G[i][k]+G[k][j])
                {
                    G[i][j]=G[i][k]+G[k][j];
                    next[i][j]=next[i][k];
                }
    cout<<G[1][n]<<endl;
 
       
    printpath();
}
 
int main()
{
    init();
    Floyd();
    return 0;
}
```
