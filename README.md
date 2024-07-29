# count-number-of-teams
class Solution {
    public int numTeams(int[] rating) {
       int n = rating.length;
        int count = 0;

        for (int j = 0; j < n; j++) {
            int leftSmaller = 0, leftLarger = 0;
            int rightSmaller = 0, rightLarger = 0;

            // Count elements smaller and larger than rating[j] to the left of j
            for (int i = 0; i < j; i++) {
                if (rating[i] < rating[j]) {
                    leftSmaller++;
                } else if (rating[i] > rating[j]) {
                    leftLarger++;
                }
            }

            // Count elements smaller and larger than rating[j] to the right of j
            for (int k = j + 1; k < n; k++) {
                if (rating[k] < rating[j]) {
                    rightSmaller++;
                } else if (rating[k] > rating[j]) {
                    rightLarger++;
                }
            }

            // Count valid teams
            count += leftSmaller * rightLarger + leftLarger * rightSmaller;
        }

        return count;  
    }
}
