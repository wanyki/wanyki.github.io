---
title: Catch That Cow
published: 2024-01-17 17:08:45
tags: [C++]
---

Farmer John has been informed of the location of a fugitive cow and wants to catch her immediately. He starts at a point *N* (0 ≤ *N* ≤ 100,000) on a number line and the cow is at a point *K* (0 ≤ *K* ≤ 100,000) on the same number line. Farmer John has two modes of transportation: walking and teleporting.

\* Walking: FJ can move from any point *X* to the points *X* - 1 or *X* + 1 in a single minute
\* Teleporting: FJ can move from any point *X* to the point 2 × *X* in a single minute.

If the cow, unaware of its pursuit, does not move at all, how long does it take for Farmer John to retrieve it?

### Input

Line 1: Two space-separated integers: *N* and *K*

### Output

Line 1: The least amount of time, in minutes, it takes for Farmer John to catch the fugitive cow.

### Sample

| Input  | Output |
| ------ | ------ |
| `5 17` | `4`    |

### Hint

The fastest way for Farmer John to reach the fugitive cow is to move along the following path: 5-10-9-18-17, which takes 4 minutes.

```cpp
#include<iostream>
#include<algorithm>
#include<queue>
using namespace std;
struct node{
	int x;
	int time;
};
int sx,ex;
int vis[100001];
int b[100001];//没用但是必不可少，缺了就会报runtime error
int bfs()
{
	queue<node>Q;
	node now,next;
	now.x=sx;
	now.time=0;
	Q.push(now);
	while(!Q.empty()){
		now=Q.front();
		if(now.x==ex)
		return now.time;
		if(now.x>0&&!b[now.x-1]){
			next.x=now.x-1;
			next.time=now.time+1;
			b[next.x]=1;
			Q.push(next);	
		}
		if(now.x<ex&&!b[now.x+1]){
			next.x=now.x+1;
			next.time=now.time+1;
			b[next.x]=1;
			Q.push(next);	
		}
		if(now.x<ex&&!b[now.x*2]){
			next.x=now.x*2;
			next.time=now.time+1;
			b[next.x]=1;
			Q.push(next);	
		}
		Q.pop();		
	}
}
int main(){
	
	cin>>sx>>ex;
	b[sx]=1;
	if(sx>=ex)
		cout<<sx-ex;
	else
	cout<<bfs();
	return 0;
}

```

