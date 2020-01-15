# Complexities of sorting algorithms

### Insertion Sort:

- Average Case / Worst Case : Θ(𝑛2) ; happens when input is already sorted in descending order
- Best Case : Θ(𝑛) ; when input is already sorted
- No. of comparisons : Θ(𝑛2) in worst case & Θ(𝑛) in best case
- No. of swaps : Θ(𝑛2) in worst/average case & 0 in Best case


### Selection Sort
- Average Case / Worst Case / Best Case: Θ(𝑛2)
- No. of comparisons : Θ(𝑛2)
- No. of swaps : Θ(𝑛) in worst/average case & 0 in best case At most the algorithm requires N swaps, once you swap an element - - into place, you never touch it again.


### Merge Sort 
- Average Case / Worst Case / Best case : Θ(𝑛𝑙𝑔𝑛) ; doesn't matter at all whether the input is sorted or not
- No. of comparisons : Θ(𝑛+𝑚) in worst case & Θ(𝑛) in best case ; assuming we are merging two array of size n & m where 𝑛<𝑚
- No. of swaps : No swaps ! [but requires extra memory, not in-place sort]


### Quick Sort
- Worst Case : Θ(𝑛2) ; happens input is already sorted
- Best Case : Θ(𝑛𝑙𝑜𝑔𝑛) ; when pivot divides array in exactly half
- No. of comparisons : Θ(𝑛2) in worst case & Θ(𝑛𝑙𝑜𝑔𝑛) in best case
- No. of swaps : Θ(𝑛2) in worst case & 0 in best case


### Bubble Sort
- Worst Case : Θ(𝑛2)
- Best Case : Θ(𝑛) ; on already sorted
- No. of comparisons : Θ(𝑛2) in worst case & best case
- No. of swaps : Θ(𝑛2) in worst case & 0 in best case


### Linear Search
- Worst Case : Θ(𝑛) ; search key not present or last element
- Best Case : Θ(1) ; first element
- No. of comparisons : Θ(𝑛) in worst case & 1 in best case


### Binary Search
- Worst case/Average case : Θ(𝑙𝑜𝑔𝑛)
- Best Case : Θ(1) ; when key is middle element
- No. of comparisons : Θ(𝑙𝑜𝑔𝑛) in worst/average case & 1 in best case
