# Binary_Search


### Definition 

The mother of all divide-and-conquer algorithms is binary search, which is a
fast algorithm for searching in a sorted array of keys S. To search for key q, we
compare q to the middle key S\[n/2\]. If q appears before S\[n/2\], it must reside
in the left half of S; if not, it must reside in the right half of S. By repeating
this process recursively on the correct half, we locate the key in a total of 
\[lgn\]comparisons—a big win over the n/2 comparisons expected using sequential search:
```binary_search
int binary_search(item_type s[], item_type key, int low, int high) {
  int middle; /* index of middle element */

  if (low > high) {
       return (-1); /* key not found */
  }

  middle = low + (high - low) / 2;  /* low + (high-low+1) / 2  --or-- low +( high-low) / 2 */

  if (s[middle] == key) {
       return(middle);   
  }
  
  if (s[middle] > key) {
       return(binary_search(s, key, low, middle - 1));
  } else {
       return(binary_search(s, key, middle + 1, high));
  }
  
}
```


### Hamburgers.py
Problem on the binary  search

|      |  A |  B  |  C  |
| -----| -- | --  | --  |
| need | c1 | c2  | c3  |
| have | h1 | h2  | h3  |
|price | p1 | p2  | p3  |
 ```money
 MONEY
 L -> ---------
                     |
>                    |
>                    |
>                    --------- <- h
```
>                  
```pseudocode
Pseucode
bool OK(n)
for i [1--->3]
money - = max( (n c1 - h1) p1 , 0  )
return money > = 0

while(l<h)
 mid = l + (l-h)/2
  If( OK (mid)) l= mid 
  else h= mid - 1
  
```
-------------------------------
```c++
#include<bits/stdc++.h>
using namespace std;
#define int int64_t
int b,s,c;
int p[3];
int m;
int req[] ={0,0,0}
bool binary_search(int mid)
{
  int to[3];
  for(int i; i<3 ;i++)
  {
    to[i] = req[i]+mid;
   }
   to[0] - =b;
   to[1] - =s;
   to[2] - =c;
   int cost=0;
    for(inti;i<3;i++)
      if(to[0]>0)
           cost + = to[i] + p[i];
     if(cost<=m)
        return true;
     return false;
  }
 } 
 signed main(){
 string ss;cin>>ss;
 for(char i:ss)
 {
  if(i=='B')
     req[0]++;
   else if(i=='S')
     req[1]++;
   else
     req[2]++;
   }
   cin>>b>>s>>c;
   for(int i=0;i<3;i++)
     cin>>p[i];
   cin>>m;
   int st=0;
   int en=1e14;
   int ans=0;
   while(st<=en)
   {
     int mid=st+(en - st)/2;
     if(binary_search(mid))
     {
       ans=mid;
       st=mid+1;
     }
     else
     {
       en=mid-1;
     } 
   }
   cout<<ans"\n";
   return0;
   
 }
```
```explan

//BBBSSC
//6 4 1
//1 2 3
//4
//
//recipe:- b-3,s-2,c-1
//i can make 1 hamburger
//check for 2
//b-6 ,s-4, c-2
//b-6,s-4,c-1+1 (market)
//remaining money - 1
//
//check for 3
//
//b-9,s-6,c-3
//
//b-3*1, s-2*2 ,c-2*3 = 13




```
