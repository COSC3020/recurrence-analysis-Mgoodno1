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
T(n/3) = 3T(n/9) + (n/3)^5
T(n) = 9T(n/9) + 3(n^5/3^5) + n^5 (Subsistue T(n/3))

T(n/9) = 3T(n/27) + (n/9)^5
T(n) = 9(3T(n/27) + (n/9)^5) + 3(n^5/3^5) + n^5 (Subsistue T(n/9))
T(n) = 27T(n/27) + 9(n^5/9^5) + 3(n^5/ 3^5) + n^5

Pattern emerging, we will use k:
T(n) = 3^kT(n/3^k) + $$\left( \sum_{i=0}^k-1 3^i \right) * n^5/3^5i
T(n) = 3^kT(n/3^k) + n^5  $$\left( \sum_{i=0}^k-1 1/3^4i \right)

when n/3^k = 1. k = log_3 n
 $$\left( \sum_{i=0}^log_3 n-1 1/3^4i \right)

Sum of geometric series converges to a constant value:
 T(n) = nT(1) + n^5 * constant
 T(n) = n^5 * constant


Final Answer:
T(n) = O(n^5)


Sources:
https://stackoverflow.com/questions/30201391/how-to-write-a-recurrence-relation-for-a-given-piece-of-code
ChatGpt for understanding the patterns
Lecture Notes/Slides
