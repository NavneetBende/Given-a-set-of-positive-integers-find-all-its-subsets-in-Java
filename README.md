# Given-a-set-of-positive-integers-find-all-its-subsets-in-Java

Set of Positive integers, find all its subsets in Java
Here, in this page we will discuss the program in which we are given with the set of positive integers find all its subset in Java Programming Language.

Set of Positive integers find all its subsets in Java
Algorithm :
Create a recursive function with the following parameters, input array, current index, output array, or current subset;
If all subsets must be stored, a vector of the array is required,
If only the subsets must be printed, this space can be discarded.
If the current index equals the array’s size, print the subset or output array, or insert the output array into the vector of arrays (or vectors),
And then return.
For very index, there are just two options.
Ignore the current element and use the current subset and next index, I + 1, to call the recursive function.
Code in Java
Run
import java.io.*;
import java.util.*;
class Main {
    public static void
    findSubsets(List<List<Integer>> subset, ArrayList<Integer> nums, ArrayList<Integer> output, int index)
    {
        if (index == nums.size()) {
            subset.add(output);
            return;
        }
       
        findSubsets(subset, nums, new ArrayList<>(output), index + 1);
 
        output.add(nums.get(index));
        findSubsets(subset, nums, new ArrayList<>(output), index + 1);
    }
 
    public static void main(String[] args) {
       
      List<List<Integer>> subset = new ArrayList<>();
       
      ArrayList input = new ArrayList<>();
      input.add(1);
      input.add(2);
      input.add(3);
       
      findSubsets(subset, input, new ArrayList<>(), 0);
 
        Collections.sort(subset, (o1, o2) -> {
            int n = Math.min(o1.size(), o2.size());
            for (int i = 0; i < n; i++) {
                if (o1.get(i) == o2.get(i)){
                    continue;
                }else{
                    return o1.get(i) - o2.get(i);
                }
            }
            return 1;
        });
       
       
      for(int i = 0; i < subset.size(); i++){
          for(int j = 0; j < subset.get(i).size(); j++){
              System.out.print(subset.get(i).get(j) + " ");
          }
          System.out.println();
      }
       
    }
}
Output :
1 
1 2 
1 2 3 
1 3 
2 
2 3 
3 
