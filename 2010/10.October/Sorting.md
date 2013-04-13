{"title": "Sorting Algorithms","date": 1285907350000}
++++++++++
> In computer science and mathematics, a sorting algorithm is an algorithm that puts elements of a list in a certain order.

<cite>Source: [Wikipedia](http://en.wikipedia.org/wiki/Sorting_algorithm "I understand that Wikipedia is not technically a correct 'Source'. Piss off.")</cite>

In my effort to [find decent visualizations](http://stackoverflow.com/questions/3809288/different-sort-algorithms-visually-performed) for popular sorting algorithms I stumbled upon a horrible fact. **There are none**. I figured I would then make my own. Here I'm going to describe (to the best of my ability) the ones I implemented, and a link to the page where they are visually represented. I have included the JavaScript implementation I wrote along with each sort, however I have left off `var` to keep the code more generic. I will also (in time) provide a link to each implementation in a source file. **The finalized page (with instructions, IE tested but slow) is [available separately here](http://joshuakehn.com/blog/static/sort.html).**

>Note on implementations. Implementations as given on this page are licensed under the [GPL v3.0](http://www.gnu.org/licenses/gpl.html) excluding the Radix Sort implementation. Code on the visual sort page is **not** licensed for public or personal use.

### Bubble Sort

The bubble sort is one of the simplest sorting algorithms known. It is also one of the least efficient simply because it's not smart. Start at the beginning of an array, and for every number compare it with the one ahead of it. If it's bigger, swap them and move on to the next number (which will be the one you swapped). Keep track of if you have swapped or not. At the end of the array, if you have swapped, repeat. If not, the array is sorted.

    var swapped = true,
        i = 0;
    while(swapped)
    {
        swapped = false
        for(i = 0; i < a.length - 1; i++)
        {
            if(a[i] > a[i+1])
            {
                swap(a, i, i+1)
                swapped = true;
            }
        }
    }
    
In relatively few lines of code you can implement this sort. It's also not too bad when used on data that is almost already sorted, taking *xn* time where *x* is the number of elements that are out of order. The average and worst case are the same at *O(n<sup>2</sup>)*.

### Selection Sort

A bit like the insertion sort but still "dumb" on a basic level. It finds the lowest number in the list and swaps it with the element at the start. Then it continues finding the next lowest element in the list and swapping it with start + 1. I implemented two algorithms, showing the simpler here. The more complex (Selection Improved) doesn't perform a direct swap when it finds a number lower, instead it stores it until the end. This will limit the number of swaps it makes to *n* but not help the number of passes it makes through the data set.

    var i = 0, j = 0;
    for(i = 0; i < a.length - 1; i++)
    {
        for(j = i + 1; j < a.length; j++)
        {
            if(a[i] > a[j])
            {
                swap(a, i, j);
            }
        }
    }

Still an *O(n<sup>2</sup>)* average / worst sort.

### Insertion Sort

This is another simple sort, but tends to be more efficient in smaller data sets, live data, and where the list is already partially sorted. It is also used as the base for other, more complex sorts (like the Shell sort) which build off the same insertion principal. Worst and average case are both the same at *O(n<sup>2</sup>)* 

The algorithm is similar to what you would use to sort a deck of cards, or a handful of bills. Start at the top and work your way down, inserting new cards into new ordered list. 

    var i = 0,
        j = 1;
    for(j = 1; j < a.length; j++)
    {
        key = a[j];
        i = j - 1;
        
        while(i >= 0 && a[i] > key)
        {
            a[i+1] = a[i];
            i = i - 1;
        }
        
        a[i+1] = key;
    }
    
### Shell Sort

The Shell sort was invented by [Donald Shell](http://en.wikipedia.org/wiki/Donald_Shell) in 1959 and for years (until the Quicksort) was considered one of the best comparison based sorts available. The sort is simple to code, but a little tricky to understand. It helps to see it visually. When it makes passes, it performs an insertion sort on every pass. However, unlike a standard insertion sort it has a gap. This gap is decreased until it is 1 and the list is then insertion sorted. This is similar to how the Comb sort works, however with an insertion sort instead.

    var m = a.length / 2 | 0; // JavaScript rounding
    m++; // Fixes a small bug with rounding
    
    while(m > 0)
    {
        for(var i = m; i < a.length; i++)
        {
            tmp = a[i];
            j = i;
            
            while(j >=  m && a[j - m] > tmp)
            {
                a[j] = a[j-m];
                j = j-m;
            }
            
            a[j] = tmp;
        }
        
        m = m / 2.2 | 0;
    }
    
The [Wikipedia article](http://en.wikipedia.org/wiki/Shell_sort) on the Shell Sort goes into much more mathematical detail, frankly it's over my head. The best case performance is *O(n)* and the worst case (gap dependent) is *O(n log<sup>2</sup>n)*.

### Comb Sort 

The Comb Sort is very much like the bubble sort, only it employs a gap mechanism to remove low values at the end of the list. By removing these low values you can improve a bubble sort to the point where it might actually be efficient. The Comb sort starts with a gap and shrinks it every pass. When the gap is one you are performing a bubble sort. At the end of the bubble sort the list is sorted. 

There is a variant of the Comb sort called the Comb Sort 11, which says if the gap is either 10 or 9, set it to 11 instead. This improves end game efficiency slightly.

    var gap = a.length;
    while(gap > 1)
    {
        gap = gap / 1.247340350103979 | 0; // Trial and error
        if(gap == 9 || gap == 10)
        {
            gap = 11;
        }
        
        for(i = 0; i < a.length - gap + 1; i++)
        {
            j = i + gap;
            if(a[i] > a[j])
            {
                swap(a, i, j);
            }
        }
    }
    
Another way to run a Comb sort is to alter the ending. Especially on larger data sets, when the data is mostly sorted it can be more efficient to run an different sort. This is done by changing

    while(gap > 1)
    
to 

    limit = 10; // Or whatever gap size you want to stop at.
    while(gap > limit)
    
I use a gap size of 8 and show both an insertion sort ending and an O/E sort ending. Neither actually improves efficiency in this case, but with a larger data set it will. The worst case performance of *O(n<sup>2</sup>)*.

### Quick Sort

The infamous quick sort. Magic shit happens in this sort, though really it's a simple algorithm to understand. It involves selecting a decent "pivot" point and moving values to either side of it, then recursively "pivoting" those sides. Once a side has only one value, it's considered sorted and returns. Take the following array:

    2 | 5 | 3 | 1 | 4
    
Suppose we select `3` as the initial pivot. We now have to move all values greater then it to one side, and less then it to the other.

    2 | 1 | 3 | 5 | 4

Now we have two sides still unsorted. The algorithm wouldn't even know if they weren't sorted, it would simply continue on because it still has to check. This is a draw back of the Quick sort. If you don't have the memory to recursively go down *n* levels then you can't use it.

    2 | 1    5 | 4
    
For each array we would select a random pivot. Let's use the last element of each. Now we repeat the shuffle process.

    1 | 2    4 | 5
    
At this point we would try to "pivot" the remaining array, but our pivot function would let us know that it's unable to do so because there is only one item in this array. At this point that is sorted and it starts climbing back up joining the arrays together giving us the sorted array.

    1 | 2 | 3 | 4 | 5
    
The implementation I use pivots in place but still uses recursion to perform the sort. It's worth it to note at some point that the Quick sort is not a stable sort. If I have an array of [1<sup>1</sup>, 1<sup>2</sup>, 3<sup>1</sup>, 1<sup>3</sup>] it does not guarantee I will get [1<sup>1</sup>, 1<sup>2</sup>, 1<sup>3</sup>, 3<sup>1</sup>] back. I might get [1<sup>3</sup>, 1<sup>1</sup>, 1<sup>2</sup>, 3<sup>1</sup>] back instead. 

 > I'll put a link here to the code as it's actually a pair of functions
 
The average and best case performance for the Quick sort is *O(n log n)* however the worst case is *O(n<sup>2</sup>)*.

### Heap Sort

The Heap sort uses a heap to comparatively sort data. By building a binary heap you can reduce the time needed to find the next largest (or smallest) value from *n* to *log n*. In essence you have an selection sort that runs *much* quicker then normal. The algorithm first creates a binary heap out of the array and then proceeds to swap in the lowest (or highest) value depending on which way you are sorting. Then it re-heaps the remaining values and repeats.

The Heap sort's advantage over the Quick sort is it's worst case complexity is improved to match it's best and average case, clocking all three in at *O(n log n)*. 

> Code for this coming
 
### O/E Transition Sort

Reworked bubble sort that is generally better but with the same *O(n<sup>2</sup>)* worst case efficiency. The is typically implemented in parallel and lends itself well to that. Because of this my drawing indicates the speed as if it was. Of course I'm not going to write parallelization code in JavaScript, there is a limit to my endurance on this project.

### Radix Sort

> I would like to thank [Pointy](http://stackoverflow.com/users/182668/pointy) for allowing me to use 
> [his implementation](http://stackoverflow.com/questions/3817067/radix-sort-in-javascript/3817440#3817440) of the Radix sort 
> here because I just didn't want to wrap my brain in a knot this week.

As best I can explain it, the Radix sort works by sorting numbers into buckets based on their digit in a certain place. In this case it starts with the least significant digit.

Starting with the array

    42 | 51 | 39 | 63 | 45 | 11
    
You would go through and put the 42 in a bucket, 51 and 11 in a bucket, 39 in a bucket, 63 in a bucket, and 45 in a bucket.

    1 -> [51, 11]
    2 -> [42]
    3 -> [53]
    9 -> [39]

Then go through each bucket by the next digit if needed

    1 -> 
        [
            5 -> [51],
            1 -> [11]
        ]

Then recombine with a bit of magic and presto! A sorted array in *O(kn)*.

***

I hope that this is helpful to someone. If you notice an error or have a question just leave me a comment and I will attempt to help as best I can.