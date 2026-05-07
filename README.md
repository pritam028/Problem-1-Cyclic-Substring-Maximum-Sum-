# Problem-1-Cyclic-Substring-Maximum-Sum-

import java.util.*;

public class Main {
    static int value(char ch) {
        return ch - 'a' + 1;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

   String s = sc.nextLine().trim();
        int n = s.length();
        String doubled = s + s
        Set<Character> set = new HashSet<>();
        int left = 0;
        int currentSum = 0;
        int maxSum = 0;
        for (int right = 0; right < doubled.length(); right++) {
            char ch = doubled.charAt(right);
            while (set.contains(ch)) {
                char removeChar = doubled.charAt(left);
                set.remove(removeChar);
                currentSum -= value(removeChar);
                left++;
            }
            while (right - left + 1 > n) {
                char removeChar = doubled.charAt(left);
                set.remove(removeChar);
                currentSum -= value(removeChar);
                left++;
            }
            set.add(ch);
            currentSum += value(ch);
            maxSum = Math.max(maxSum, currentSum);
        }
 System.out.println(maxSum);
 sc.close();
    }
}
