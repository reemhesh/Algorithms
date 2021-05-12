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

  middle = (low + high) / 2;

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
>def canBeMade(/count, need, have, price, money/):
