# CSC140-Graded-Exercise-0
package project1;
/**
 *
 * @author mshir
 */
public class project1 {
    /**
     * @param args the command line arguments
     */
    public static int seqSearch(int[] list, int target){
        /**
         * Method to search for a number in a list
         * Will return the index of that number or -1 if it's not there
         * @param args list of integers, target number
         */
        for (int j = 0; j < list.length; j++){
            if (list[j] == target){
                return j;
            }
        }
        return -1;
    }
    public static int binSearch(int[] list, int target){
        int firstIndex = 0;
        int lastIndex = list.length - 1;
        int middleIndex = (firstIndex + lastIndex) / 2;
        while (firstIndex <= lastIndex){
            if (list[middleIndex] < target){
                firstIndex = middleIndex + 1;
            }
            else if (list[middleIndex] == target){
                return middleIndex;
            }
            else{
                lastIndex = middleIndex - 1;
            }
            middleIndex = (firstIndex + lastIndex) / 2;
        }
        return -1;
    }
    
    public static int[] selSort(int[] list){
        for(int i = 0; i < list.length; i++){
            int minIndex = i;
            for(int j = i + 1; j < list.length; j++){
                if (list[j] < list[minIndex]){
                    minIndex = j;
                }
            }
            int temp = list[minIndex];
            list[minIndex] = list[i];
            list[i] = temp;
        }
        return list;
    }
    
    public static int[] insSort(int[] list){
        for (int i = 1; i < list.length; i++){
            int key = list[i];
            int j = i - 1;
            while (j >= 0 && key < list[j]){
                int temp = list[j];
                list[j] = list[j + 1];
                list[j+1] = temp;
                j--;
                }                               
            }
            return list;
        }
    
    public static int[] merSort(int[] list){
        if(list.length <= 1){
            return list;
        }
        int midpoint = list.length / 2;
        
        int[] left = new int[midpoint];
        int[] right;
        
        if(list.length % 2 == 0){
            right = new int[midpoint];
            
        }
        else {
            right = new int[midpoint + 1];
        }
        for(int i = 0; i < midpoint; i++){
            left[i] = list[i];
        }
        for(int j = 0; j < right.length; j++){
            right[j] = list[midpoint + j];
        }
        int[] result = new int[list.length];
        left = merSort(left);
        right = merSort(right);
        result = merge(left,right);
        return result;
    }
    public static int[] merge(int[] left, int[] right){
        int[] result = new int[left.length + right.length];
        
        int leftPointer, rightPointer, resultPointer;
        leftPointer = rightPointer = resultPointer = 0;
        while(leftPointer < left.length || rightPointer < right.length){
            if(leftPointer < left.length && rightPointer < right.length){
                if(left[leftPointer] < right[rightPointer]){
                    result[resultPointer++] = left[leftPointer++];          
                }
                else{
                    result[resultPointer++] = right[rightPointer++];
                }
            }
            else if(leftPointer < left.length){
                result[resultPointer++] = left[leftPointer++];
            }
            else if(rightPointer < right.length){
                result[resultPointer++] = right[rightPointer++];
            }
        }
        return result;
    }
        
    
    public static void main(String[] args) {
        int[] values = {25,42,50,64,75,100,100};
        int[] valuez = {21,13,68,47,113,223,103};
        int[] ualuez = {53,17,14,90,55,67,99,23};
        System.out.println(seqSearch(values, 100));
        System.out.println(binSearch(values,101));
        selSort(values);
        insSort(valuez);
        merSort(ualuez);
        for (int k = 0; k < values.length; k++){
            System.out.println(values[k]);
        }
        for (int m = 0; m < valuez.length; m++){
            System.out.println(valuez[m]);
        }
        for (int m = 0; m < ualuez.length; m++){
            System.out.println(ualuez[m]);
        }
    }
}

/*
Credit to Alex Lee,Bill Barnum, CFM_FuelGaming, McProgramming, Joe James,
Programming Tips & Tricks, Johnathon Kwisses
^All of these are youtube channels
*/
