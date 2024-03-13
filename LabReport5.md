# Milan Suresh Lab Report 5 - Putting it All Together

# Part 1

1. Student's post

Hello, sir! I have a pressing issue :O

<img width="476" alt="Screenshot 2024-03-12 at 8 22 26 PM" src="https://github.com/MilanSuresh2468/cse15l-lab-reports/assets/73302110/1e852389-5b10-44b6-a875-75ccf5602d01">

My `comprun.sh` file is supposed to compile the Sieve.java file and then run it with the arguments given. However, when I run `comprun.sh`, my code isn't printing `"Success! Input another integer to check if it's a prime."` like it's supposed to. Why is this happening? Is it because `comprun.sh` is failing?

2. TA response

Hi, so it looks like your `comprun.sh` file ran the code as required, so it most likely is an issue with the code in `Sieve.java`. Could it be that the required message is only printing within a specific `if` statement? Try running `comprun.sh 3` to see what happens with prime numbers rather than `1`.

3. Student Perspective

<img width="463" alt="Screenshot 2024-03-12 at 8 29 42 PM" src="https://github.com/MilanSuresh2468/cse15l-lab-reports/assets/73302110/49cbc98c-2dca-4f01-af24-468518ee2bf5">

It looks like that the code works as required with `3`, a prime number. If the `if` statement to check if the given input is a unit succeeds, it looks like the line to output the required message never runs since is not included in the `if` statement.

4. Setup
<img width="152" alt="Screenshot 2024-03-12 at 8 45 16 PM" src="https://github.com/MilanSuresh2468/cse15l-lab-reports/assets/73302110/6c510239-e9c0-413e-b54b-c0d2a47a1938">
   


Contents of comprun.sh 
```
javac Sieve.java
java Sieve "$@"
```

Contents of Sieve.java
```
import java.math.*;

public class Sieve {
    public static void main(String[] args) {
        if(args.length==0 || args.length >1){
            throw new IllegalArgumentException("Please input a single integer");
        }else{
            try{
                int given = Integer.parseInt(args[0]);
                if(given==1){
                    System.out.println("Unit!");
                    return;
                }
                for (int x = 2; x < Math.sqrt(given);x++){
                    if(given%x==0){
                        System.out.println("Not a prime!");
                        System.out.println("Success! Input another integer to check if it's a prime.");
                    }
                }
                System.out.println("Prime!");
                System.out.println("Success! Input another integer to check if it's a prime.");
            }catch (NumberFormatException e){
                throw new IllegalArgumentException("Please input a single integer");
            }
        }
    }
}
```
Lines that triggers the bug: 
```
int given = Integer.parseInt(args[0]);
if(given==1){
  System.out.println("Unit!");
  return;
}
```
To fix the bug, add `System.out.println("Success! Input another integer to check if it's a prime.");` within the `if` statement after 
`System.out.println("Unit!");`, so it prints the required message.

# Part 2: Reflection

I learned how to use `Vim`, which is very useful when working within a couple files. `Vim` isn't really a time-save when working
with a ton of files and complex file structures, but it is a really cool tool and fun to use. Now, instead of opening VSCode when I'm working with a single file, I often just open the file in `Vim`. Epic.
