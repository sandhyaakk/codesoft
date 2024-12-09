# codesoft
number game
import java.util.Random;
import java.util.Scanner;

public class number {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int score = 0;
        boolean playAgain = true;

        System.out.println("Welcome to the Number Guessing Game!");

        while (playAgain) {
            int lowerBound = 1;
            int upperBound = 100;
            int number = random.nextInt(upperBound - lowerBound + 1) + lowerBound;

            System.out.println("\nI've picked a number between " + lowerBound + " and " + upperBound + ". Can you guess it?");
            int attempts = 0;
            int maxAttempts = 10;
            boolean guessedCorrectly = false;

            while (attempts < maxAttempts && !guessedCorrectly) {
                System.out.print("Attempt " + (attempts + 1) + "/" + maxAttempts + ": Enter your guess: ");
                int guess = scanner.nextInt();
                attempts++;

                if (guess == number) {
                    System.out.println("Congratulations! You guessed the number in " + attempts + " attempts.");
                    score++;
                    guessedCorrectly = true;
                } else if (guess < number) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }
            }

            if (!guessedCorrectly) {
                System.out.println("Sorry, you've used all your attempts. The correct number was: " + number);
            }

            System.out.println("Your current score is: " + score);

            System.out.print("Do you want to play another round? (yes/no): ");
            String response = scanner.next();
            playAgain = response.equalsIgnoreCase("yes");
        }

        System.out.println("Thank you for playing! Your final score is: " + score);
        scanner.close();
    }
}
