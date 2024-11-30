# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

Answer: 
T(n)=a⋅T(n/b)+O(n^d)

In our case:
    a=3 (since there are 3 recursive calls),
    b=3 (since the problem size is reduced by a factor of 3),
    d=5 (the work done by the loops is O(n^5)).
    
Now, we calculate log_⁡b(a):
Log_⁡b(a) = log_⁡3(3)= 1

Next, we compare d (which is 5) with log_⁡b a (which is 1):
If d > log⁡_b(​a), the solution is O(n^d).

Since 5 > 1, the solution to the recurrence is dominated by the work done in the loops, and the overall complexity is O(n^5).
