```cpp
#include <cstdio>
const int INT_MAX = 10000; 
const int MAX = 501;
 
int wei[MAX];//weight quanzhi
int visit[MAX];//visited or not
int map[MAX][MAX];//distance between two points
 
int mind;//min distance
int cnt;//the number of min distance road
int maxt;//max weight
int n;//number of citys
//initialize 
void init(int n){
	int i,j;// two dimension
 
	for(i=0;i<n;++i){
		visit[i] = 0;//has not visited
		for(j=0;j<n;++j){
			map[i][j]=INT_MAX;//aistance between two citys
		}
	}
}
//deepth first search
//p:started point end:end point dist:distance between started point and now point 
//weit: the weight between started point and now point
void dfs(int p,const int end,int dist,int weit){//the hardest part
	//find the end point, three cases,but is bigger ,we don't need to handle
	if(p==end){
		if(dist<mind){//we find a road between p and end, whose distance is small than minimum distance
		//so we need to record this diatance as the min 
		//and the number cnt should be 1
			cnt = 1;
			mind=dist;//new min distance
			maxt = weit;//because dis is small so maxt has to change for this way's weight
		}else if(dist==mind){//another one minimum way ,cnt++,
			++cnt;
			if(maxt<weit){//compare ,choose the max
				maxt = weit;
			}
		}
		return;//finish this branch
	}
 
 
	if(dist>mind)return;//triming，if situation like this we know this is useless
	visit[p] = 1;//visit it
	for(int i=0;i<n;++i){//the next point
		if(visit[i]==0 && map[p][i]!=INT_MAX){//don't go back ||  there exists road
		
			dfs(i,end,dist+map[p][i],weit+wei[i]);// i to end ,record dis=dist+map[p][i],weight gather ,weit+wei[i]
		
		}
	}
	visit[p] = 0;// return there,you konw ,i should change back to 0 ,because to other point ,they haven't visit i
}
 
int main(){
	int m,st,end,x,y,d,i;//
	mind = INT_MAX;//initialize
	cnt = 0;//number of shortest road
 
	scanf("%d %d %d %d",&n,&m,&st,&end);//citys roads begin end
	init(n);//map[n][n]  visited[n] initialize
	for(i=0;i<n;++i){
		scanf("%d",&wei[i]);//input the weight of city i
	}
	while(m--){
		scanf("%d %d %d",&x,&y,&d);
		if(map[x][y]>d){// maybe there two road between two citys
			map[x][y] = map[y][x] = d;//record
		}
	}
	dfs(st,end,0,wei[st]);//search the result   for the started point distance is 0 weight is wei[st]
	printf("%d %d\n",cnt,maxt);//cnt maxt
	return 0;
}
```
