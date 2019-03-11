```cpp
#include <stdio.h>
#include<stack>
using namespace std;
int main()
{
 
 
    int inf=99999999; 
    
    int n,m; //n顶点个数，m边的条数
    scanf("%d %d",&n,&m);
    
    int e[n+1][n+1];
    //初始化,有向图 
    for(int i=1;i<=n;i++)
        for(int j=1;j<=n;j++)
            if(i==j) e[i][j]=0;  
              else e[i][j]=inf;
              
    //读入边
    int t1,t2,t3;
    for(int i=1;i<=m;i++)
    {	
        scanf("%d %d %d",&t1,&t2,&t3);
        e[t1][t2]=t3;
    }
    
	int dis[n+1]; 
    //初始化dis数组，这里是1号顶点到其余各个顶点的初始路程
    for(int i=1;i<=n;i++)
        dis[i]=e[1][i];
	
	int book[n+1];
    //book数组初始化,1表示已找到最短路径的点，0反之 
    for(int i=1;i<=n;i++)
        book[i]=0;
    
    book[1]=1;//自身确定 
    //i的前一个顶点，由此顺藤摸瓜找出路径，初始化为1，因为一开始定义dis从1开始 
    int pre[n+1];
    for(int i=1;i<=n;i++)
        pre[i]=1;
    
    
    //Dijkstra算法核心语句
    for(int i=1;i<=n-1;i++)//n-1循环确定所有 
    {
        //步骤一：在book0中找到离1号顶点最近的顶点u 
        int min=inf;
        int u;//中转顶点 
        for(int j=1;j<=n;j++)
        {
            if(book[j]==0 && dis[j]<min)
            {
                min=dis[j];
                u=j;
            }
        }
        book[u]=1;//步骤二：book1，u为此次确定的近距离顶点 
        
        for(int v=1;v<=n;v++)//步骤三：利用顶点u为最后中转更新距离,从集合范围外找 
        {
            if(book[v]==0&&dis[v]>dis[u]+e[u][v])//u，v相连才更新 
            {
                
                	 dis[v]=dis[u]+e[u][v];
                	 pre[v]=u; //更新v的起点为u 
			 
            }
        }    
    }
    //输出最终的结果,dis[i]表示到1到i的最短距离 
    for(int i=1;i<=n;i++)
        printf("%d ",dis[i]);
        
	//输出路径,假设要到达的点为k 
	stack<int> s;
	int k=n;
	while(k!=1){
		s.push(k);
		k=pre[k];
	}
	s.push(1);
	printf("\n%d",s.top());
	s.pop();
	while(!s.empty()){
		printf("->%d",s.top());
		s.pop();
	}
	
    return 0;
}
```
