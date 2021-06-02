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

  middle = (low + high) / 2;  /* low + (high-low+1) / 2  --or-- low +( high-low) / 2 */

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

> ! [add graph](https://ibb.co/1G8pKND)


```python
###Coding
def canBeMade(count, need, have, price, money):
 """
  count: the number of Hamburgers to be made
  need, have, price: arrays of 3 elements
    the ith element of each corresponds to the ith ingredient and represents
    1. the needed amount of that ingredient in the Hamburger
    2. the amount we have of that ingredient
    3. the price per unit of that ingredient
  money: the amount of money we can spend
  """
  for (needed, present, cost) in zip(need, have, price):
    m = max((count * needed - present) * cost, 0)
    if m > money: return False
    else: money -= m
  return True

def main():
  dic = {"B":0, "S":0, "C":0}
  for i in input(): dic[i] += 1
  need = list(dic.values())
  have = [int(v) for v in input().split(' ')]
  price = [int(v) for v in input().split(' ')]

  money = int(input())

  l , h = 0, int(10**15)
  # ||||||||||__________
  #          ^
  # the answer is in low
  while(l < h):
   mid = l + (h - l) / 2 #it would start rounding towards the higher bound
    # print(l, h, mid)
    if (canBeMade(mid, need, have, price, money)): l = mid
    else: h = mid - 1

  print(l)

if __name__ == '__main__':
  main()

```
