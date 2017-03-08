# Ex_KadanesAlgorithm
Find subarray with the max sum.

    @Test
    public void test() {
        int [] a1 = {-2, -3, 4, -1, -2, 1, 5, -3, -1, -5, 1, 7, -1, 1};
        int [] a2 = {-2, -3, -1, -2, -3};
        System.out.print("Array: ");
        Arrays.stream(a1).forEach(value -> System.out.print(value + ", "));
        System.out.println();
        System.out.println("Maximum contiguous sum is " + maxSubArraySum(a1));
        System.out.print("Array: ");
        Arrays.stream(a2).forEach(value -> System.out.print(value + ", "));
        System.out.println();
        System.out.println("Maximum contiguous sum is " + maxSubArraySum(a2));

    }
    static int maxSubArraySum(int a[]) {
        int size = a.length;
        int max_so_far = Integer.MIN_VALUE, max_ending_here = 0;
        int start = -1;
        int end = -1;
        for (int i = 0; i < size; i++) {
            if (max_ending_here <= 0 && a[i] > 0) {
                start = i;
            }
            max_ending_here = max_ending_here + a[i];
            if (max_so_far < max_ending_here) {
                end = i;
                max_so_far = max_ending_here;
                if (max_ending_here < 0) {
                    start = i;
                }
            }
            if (max_ending_here < 0) {
                max_ending_here = 0;
            }
        }
        if (end == -1) {
            end = size -1;
        }
        System.out.println("Maximum contiguous range is: " + start + " : " + end);
        return max_so_far;
    }
    
// the output is 
Array: -2, -3, 4, -1, -2, 1, 5, -3, -1, -5, 1, 7, -1, 1, 
Maximum contiguous range is: 10 : 11
Maximum contiguous sum is 8
Array: -2, -3, -1, -2, -3, 
Maximum contiguous range is: 2 : 2
Maximum contiguous sum is -1
