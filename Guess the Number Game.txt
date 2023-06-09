import java.util.Random;
import java.util.Scanner;

public class GuessTheNumberGame {
    public static void main(String[] args) {
        int minRange = 1;
        int maxRange = 100;
        int maxAttempts = 5;
        int score = 0;
        

        Scanner scanner = new Scanner(System.in);

        while (true) {
            int targetNumber = generateRandomNumber(minRange, maxRange);
            int attempts = 0;
            int remaining = 5;

            System.out.println("Welcome to Guess the Number game!");
            System.out.println("I have chosen a number between " + minRange + " and " + maxRange + ". Can you guess it?");
            System.out.println("You have " + maxAttempts + " attempts to guess the number ");

            while (true) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempts++;
                 remaining = (maxAttempts - attempts);

                if (userGuess == targetNumber) {
                    System.out.println("Congratulations! You guessed the correct number.");
                    score += (maxAttempts - attempts) + 1;
                    break;
                } else if (userGuess < targetNumber) {
                    if (remaining > 0) {
                    System.out.println("Too low! Try a higher number.");
                    System.out.println("you have attempts " + remaining + " to guess the number");
                    }
                } else {
                    if (remaining > 0) {
                    System.out.println("Too high! Try a lower number.");
                    System.out.println("you have attempts " + remaining + " to guess the number");
                    }
                }

                if (attempts == maxAttempts) {
                    System.out.println("Sorry, you've reached the maximum number of attempts.");
                    System.out.println("The number is " + targetNumber );
                    break;
                }
            }

            System.out.print("Do you want to play again? (yes/no): ");
            String choice = scanner.next();
            if (!choice.equalsIgnoreCase("yes")) {
                System.out.println("Thanks for playing! Your final score is: " + score);
                break;
            }
        }
        scanner.close();
    }

    private static int generateRandomNumber(int min, int max) {
        Random random = new Random();
        return random.nextInt(max - min + 1) + min;
    }
}