[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=8786037&assignment_repo_type=AssignmentRepo)
## Fibonacci sequence
**name: Luna Eyad Khaled
BN: 8    SEC: 2**

Here is some different ways to find the Nth Fibonacci number:
### The first solution:
*Using recursion*

````````````````````
 #include <iostream>
using namespace std;
     int fib (int n)
    { 
      if (n<=1)
        return n;
      
      else
      return fib(n-1)+fib(n-2);   
      }
      
 int main()
{
    int x;
    cin >>x;
    cout << fib(x) << endl;
    return 0;
} 

`````````````````````````````````

### The second solution :
*using recursion with memoization to prevent the redundant calls* 

````````````````````
#include<iostream>
using namespace std;
int Fibonacci(int n) {
   int fibo[n+2]; //array to store fibonacci values
   
   fibo[0] = 0;
   fibo[1] = 1;
   for (int i = 2; i <= n; i++) {
      fibo[i] = fibo[i-1] + fibo[i-2]; 
   }
   return fibo[n];
}
int main () {
   int n;
   cout << "give me n : "; cin >>n;
   cout << Fibonacci(n) <<endl;
}
`````````````````````````````````



### The third solution:
*using loop*
 ````````````````````````````````

#include<iostream>
using namespace std;

int fib(int n)
{
	int a = 0, b = 1, c, i;
	if( n == 0)
		return a;
	for(i = 2; i <= n; i++)
	{
	c = a + b;
	a = b;
	b = c;
	}
	return b;
}

int main()
{
	int x;
   cin >>x;
   cout << fib(x) << endl;
    return 0;
}
`````````````````````````````````

###the 4th solution:
*using matrix multiplication; if we multiply the matrix [[1, 1], [1, 0]],  
n-1 times then the element at index [0][0] will be the nth Fibonacci number*

!(https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTOuZHagByevaH8lgEJ5Mumzxc7l4r6OlBtMw&usqp=CAU)
This  is a [YouTube video ](https://youtu.be/QtFVY7ffl_s) deriving this equation
`````````````````````````````````
#include<iostream>
using namespace std;
void power(int F[2][2], int n);
void multiply(int F[2][2], int M[2][2]);



int fib(int n)
{
  int F[2][2] = { { 1, 1 }, { 1, 0 } };
  
 if (n==0)
  return 0;
  
power(F, n-1);
 return F[0][0];
 
}

void power(int F[2][2], int n)

{ 
    
int M[2][2] = { { 1, 1 }, { 1, 0 } };

 for (int i=2 ; i<=n ; i++)
     multiply (F, M);
}


void multiply(int F[2][2], int M[2][2])
{
 int x = F[0][0] * M[0][0] + F[0][1] * M[1][0];
 int y = F[0][0] * M[0][1] + F[0][1] * M[1][1];
 int z = F[1][0] * M[0][0] + F[1][1] * M[1][0];
 int w = F[1][0] * M[0][1] + F[1][1] * M[1][1];
     
    F[0][0] = x;
    F[0][1] = y;
    F[1][0] = z;
    F[1][1] = w;

}

int main () {
   int n;
   cout << "give me n : "; cin >>n;
   cout <<fib(n)<<endl;
}
`````````````````````````````````

##summary to compare the time and space complexity :
1. recursion                           
2. recursion with memoization         
3. Iterative Method
4. matrix multiplication

num    | time complexity | space complexity
------ | ------|----------
1     |    O(2^n)  | O(n)
2      |  O(n)  | O(n)
3      |   O(n)    |  O(1)
4       |   O(n)    | O(1)