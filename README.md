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
Each recursive call reduces the problem by a factor of 3
First Loop : n^2
Second Loop : n
Third Loop : n^2
Therefore total work inside loops is: O(n^2 x n x n^2)
So T(n) = 3T (n/3) + O(n^5)
Steps:
T(n) = 3(3T(n/9) + O((n/3)^5)) + O(n^5)
T(n) = 3^2(T)(n/9) + O(n^5)
T(n) = 3^3(T)(n/27) + O(n^5)
T(n) = 3^k(T)(n/3k) + O(n^5)
T(n) = 3^log3 n(T)(1) + O(n^5)
T(n) = O(n) + O(n^5)
Final Answer:
O(n^5) grows much fater than O(n) as n increases, there T(n) = O(n^5)
