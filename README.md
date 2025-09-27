
import java.util.Scanner;

public class BalancedNumberChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Read input
        int n = scanner.nextInt();
        scanner.close();

        // Convert number to string to process digits by position
        String numStr = String.valueOf(n);
 
        int sumOdd = 0;

 
        int sumEven = 0; 

        // Loop through digits using 1-based indexing
        for (int i = 0; i < numStr.length(); i++) {
            int digit = numStr.charAt(i) - '0';

            if ((i + 1) % 2 == 0) {
                sumEven += digit; // even position (1-based)
            } else {
                sumOdd += digit; // odd position (1-based)
            }
        }

        // Check if balanced
        if (sumOdd == sumEven) {
            System.out.println("Balanced");
        } else {
            System.out.println("Not Balanced");
        }
    }
}
