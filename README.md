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

T(n) = 3^i (T)(n/3^i) + 3^i(n^5/3^i) + 3^i(n^5/3^i) + n^5
n/3^i = 1  => i = log3(n)

T(n)= nT(1)+ $$\left( \sum_{i=0}^log_3 n-1 n^5/3^4i \right)
​T(n) = nT(1) + n^5
T(n) ∈ O(n^5)

Sources:
https://stackoverflow.com/questions/30201391/how-to-write-a-recurrence-relation-for-a-given-piece-of-code
ChatGpt for understanding the patterns
Lecture Notes/Slides

# Plagarism Statement
All exercises must contain the following statement: “I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.”
