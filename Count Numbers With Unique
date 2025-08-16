class Solution {
    public int countNumbersWithUniqueDigits(int n) {
        return solve(n);

    }
    public int solve(int n) {
        if(n==0) return 1;
        if(n==1) return 10;
        int x = 9;
        for(int i=9;i>9-n+1;i--) {
            x*= i;
        }
        return x + solve(n-1);
    }
}
