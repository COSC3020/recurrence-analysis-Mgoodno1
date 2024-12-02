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
Intial analysis:
Each recursive call reduces the problem by a factor of 3
First Loop : n^2
Second Loop : n
Third Loop : n^2
Therefore total work inside loops is: n^5

Recurrence Relation:
T(n) = 3T (n/3) + (n^5)
Steps:
3^k(n/3k)^5 = 3^k (n^5/3^5k) = n^5/3^4k
T(n) = n^5 + n^5/3^4 + n^5/3^8 + ...
T(N) = n^5 (1 + 1/3^4 + 1/3^8 + ...)
Final Answer:
T(n) = O(n^5)
