![image2](https://github.com/Erunning/Algorithm_solutions/blob/master/image/image2.png)
```cpp
#include<stdio.h>
#include<iostream>
#include<cmath>
#include<vector>
#include<algorithm>
using namespace std;
int main(){
	int n;
	long long res=0,temp;//long long 类型，会超int 
	scanf("%d",&n);
	vector<long long> v;
	for(int i=0;i<n;i++){
		scanf("%lld",&temp);//lld 
		v.push_back(temp);
	}
	sort(v.begin(),v.end());//sort 
	while(--n){
		res+=v[0];
		res+=v[1];
		long long a=v[0]+v[1];
		v.erase(v.begin());
		v.erase(v.begin());
		vector<long long>::iterator it=v.begin();
 
		//将a插入应在的位置 
		int flag=0;
		for(;it<v.end();it++){
			if(*it>=a){
				v.insert(it,a);
				flag=1;
				break;	
			}
		}
		if(flag==0){//考虑到可能a大于所有元素 
			v.push_back(a);
		}
	}
	cout<<res<<endl;
	return 0;
}
/* 
Points：
	1.long long ，lld，会超int
	2.a的插入，不必sort，会超时
	3.哈夫曼编码
	4.vector<long long>::iterator it=v.begin();迭代器的应用
*/
```
