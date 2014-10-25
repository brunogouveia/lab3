Lab 3
====

### Group:
- Bruno Guovela
- Dillon Drenzek

##Question 1

######(A)
Consider the following code:
```scala
const x = 2;

const f = function(a) {
	return x;
}

const g = function(b) {
	const x = 1;
	return f(1);
}

g(1);
```
**Static scope**: f(a) will always return 2, because the use of x in statement `return x;` is binded to the first line. Therefore, g(b) will always return 2 as well.

**Dynamic scope**: f(a) might return 2 or not, depends of the scope that called f. For instance, the scope of function g binds x to value 1, then when f is called from g, f(a) will return 1.

##Question 2

######(C)
The evaluation order is deterministic. Due to the fact that for all expression (e<sub>1</sub> *bop* e<sub>2</sub>), we know exactly which of the expressions we must evaluate firts.


## Question 3 
The evaluation order is from left to right, which means that first evaluates e<sub>1</sub> to a value and after that evaluate e<sub>2</sub> to a value. 

So first, the only rule that can be applied is SearchBinary<sub>1</sub>, and this rule will be applied until e<sub>1</sub> evaluates to a value v<sub>1</sub>. Now, the only rule applicable is SearchBinaryArith<sub>2</sub>, and it will be aplied until e<sub>2</sub> evaluates to v<sub>2</sub>. Then finally we can apply one of the three do rules: DoPlusString<sub>1</sub> (if v<sub>1</sub> is a string), DoPlusString<sub>2</sub> (if v<sub>2</sub> is a string) or DoPlusNumber otherwise.

To obtain the opposite evaluation order, we must change the following search rules:

|          |**SearchBinary<sub>1</sub>** |  **SearchBinaryArith<sub>2</sub>**|    
| :--:     |:-------: | :------: |
| Premise  | e<sub>2</sub> ==> e'<sub>2</sub> | e<sub>1</sub> ==> e'<sub>1</sub> *bop* in {`+,-,*,/,</<=,>,>=`} |
|Conclusion| e<sub>1</sub> *bop* e<sub>2</sub> ==> e<sub>1</sub> *bop* e'<sub>2</sub> | e<sub>1</sub> *bop* v<sub>2</sub> ==> e'<sub>1</sub> *bop* v<sub>2</sub>|

## Question 4

######(A)
For instance, we need to evaluate the expression (e<sub>1</sub> && e<sub>2</sub>). If we are using a short-circuit evaluation, then we will first evaluate e<sub>1</sub> to a value v<sub>1</sub>. If v<sub>1</sub> is **false**,  we don't need to look at e<sub>2</sub>, we just need to return v<sub>1</sub>.

######(B)
Yes, because by rule **DoAndFalse**, if v<sub>1</sub> is **false**, then we don't need to evaluate e<sub>2</sub>.

