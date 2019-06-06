Add your answers to the Algorithms exercises here.
## Exercise 1 
a) The computes to O(n), because our while loop's size is dependent on the input of n. As n increase so will the run time of our while loop. So as N goes so does our function.

    a = 0   # O(c)
    while(a < n* n * n):  #O(n)
        a = a + n * n   

b) When I first saw these nested loops I immediately thought of Quadratic time complexity. As we continue to multiple O(n), the time complexity of the for loops, we begin to see this exponentially balloon, resulting in O(n^4). I did read over the week that if different variables are involved this can impact the way we calculate this, but because each variable is dependent on the previous I don't think that applies here. 


    sum = 0
        for i in range(n): #O(n)
        i += 1
        for j in range(i + 1, n): #O(n)
            j += 1
            for k in range(j + 1, n): #O(n)
            k += 1
            for l in range(k + 1, 10 + k): #O(n)
                l += 1
                sum += 1

            # O(n) * O(n) * O(n) * O(n) = O(n^4)

c)  When we call a function recursively, this creates a branching pattern that can increase time complexity. Every time our parameters aren't met, we are initiating another instance of our function, which is repeating until we meet our n case.These evaluates to  O(2^n) because everytime we call our function is doubling in size, by recalling our function, therefore creating the exponential O(2^n) relationship. 

    def bunnyEars(bunnies):
      if bunnies == 0: #O(c)
        return 0 #O(c)

      return 2 + bunnyEars(bunnies-1) #O(2^n)



##Exercise 2:
POLYA APPROACH:

1.) Plan
Values: 
 - N = Height of Building
 - Eggs = Infinite
 - F = Floor Eggs break when dropped
 - if current floor > F The egg will break
 - if current floor < F The egg will NOT break

 What do they want returned?
 - Determine which floor breaks the egg without destroying too many eggs.

 Immediate Questions?
 - How do we determine if an egg is broken, how do we know that we're at floor F 
 - What floor do we start on? 
 - Do we assume all eggs break evenly?

 First Pass: Linear 
 - Start from the ground level until a single egg breaks. Therefore, we only break one egg in finding which breaks. 
 - This approach is slightly flawed if we a 1,000 floor building and these alien eggs only crack on the 999th floor, our runtime would be heavy

 Second Pass: Binary
 - Start from the middle floor, if the egg breaks try again using the bottom half of floors as the range, including the midpoint. And repeat our function here until an egg does not break.
 - If the egg doesn't break. Try again using the top half of floors as the range. Continue until an egg breaks.


Our Pseudo Code would look something like this:
First Pass:
def egg_break(n_floors):
    for i in n_floors:
        CHECK IF EGG BROKE 
            return i
    
def egg_break(n_floors):
    base = 0
    while Egg is true:
        DROP EGG/CHECK IN TACK
        Base += 1


Second Pass;
def egg_break(n_floors):
    mid = len(n_floors) //2
    Store the Broken Floor
    DROP EGG from mid
    if len(n_floors) < 2:
        return n_floors # Base Case 
    elif (EGG BROKE):
        egg_break(:mid) # Top Half
    else:
        egg_break(mid+1:) # Bottom Half

4 is the floor
 1, 2, 3, [4], 5
 Drop from 3rd floor -> Egg didn't break
 Run from floors [4] and 5
[4], 5 
Drop from 5th floor breaks:
run with floor [4] Returns 4.


