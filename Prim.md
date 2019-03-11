```cpp
#include<iostream>
#include<stdio.h>
#include<string.h>
using namespace std;
 
 
int INF = 999999999;
 
int G[110][110];
int sta[110]; //以i为终点以visit的连通点为起点的最短边的起点 
int low[110];//以i为终点以visit的连通点为起点的最短边长 
int vis[110];//是否已选择 
int N,M;
 
int prim()
{
    int res=0;
 
    vis[1]=1;
    low[1]=0;
 
    for(int i = 2 ; i <= M ; i++)//顶点1到所有顶点的距离，1在vis内 
        low[i] = G[1][i];
 
    for(int i = 2 ; i <= M ; i++)//寻找n-1条边 
    {
        int minc = INF;//最短边 
        int pos=0;//将选择的顶点 
 
        for(int j = i ; j <= M ; j++)//找边 
            if(!vis[j] && low[j] < minc )
            {
                minc = low[j];
                pos = j;
            }
 
        if(minc == INF)//不连通 
            return -1;
		printf("顶点%d - 顶点%d :边长 %d\n",sta[i],i,minc);//输出边 
        vis[pos]=1;//访问之 
        res += minc;//加权和 
 
        for(int j = 1 ; j <= M ; j++){//更新low 
            if(!vis[j] && low[j] > G[pos][j]){//low为vis与i之间的最短边，这样保证选的不是连通vis内部的点 
                low[j] = G[pos][j];
                sta[j]=pos;//更新起点 
            }
            }
    }
 
    return res;
 
}
 
int main()
{
 
    while(scanf("%d%d" , &N,&M)&& N)
    {
		//初始化 
		for(int i=0;i<=N;i++){
			sta[i]=1;
				low[i]=INF;
					vis[i]=0;
		}
		for(int i=0;i<=N;i++){
			for(int j=0;j<=N;j++){
				G[i][j]=INF;
			}
		}
		
		//读入数据 
        for(int i = 0 ; i < N ; i++)
        {
            int a,b,w;
            scanf("%d%d%d",&a,&b,&w);
 
            G[a][b] = G[b][a] = w;
        }
 
        int res = prim();
 
        res == -1 ? puts("?") : printf("%d\n" , res);
    }
 
    return 0;
}
```
