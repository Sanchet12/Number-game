# Task-1 Number-game

import java.util.Random;
import java.util.Scanner;

public class NumberGame {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        int rounds = 0;
        int totalAttempts = 0;

        while (true) {

            Random random = new Random();
            int randomNumber = random.nextInt(100) + 1;

            int attempts = 0;
            boolean correctGuess = false;

            System.out.println("Round " + (rounds + 1));
            while (!correctGuess && attempts < 5) { // Limiting to 5 attempts per round
                System.out.print("Enter your guess (between 1 and 100): ");

                int userGuess = scanner.nextInt();

                if (userGuess == randomNumber) {
                    System.out.println("Congratulations! Your guess is correct.");
                    correctGuess = true;
                } else if (userGuess < randomNumber) {
                    System.out.println("Too low. Try again!");
                } else {
                    System.out.println("Too high. Try again!");
                }

                attempts++;
            }


            if (correctGuess) {
                System.out.println("You guessed the number in " + attempts + " attempts.\n");
                totalAttempts += attempts;
            } else {
                System.out.println("Sorry! The correct number was " + randomNumber + ".\n");
            }

            System.out.print("Do you want to play another round? (yes/no): ");
            String playAgain = scanner.next().toLowerCase();

            if (playAgain.equals("no")) {
                break;
            }

            rounds++;
        }

        System.out.println("Thanks for playing! Your total score is based on the number of attempts: " + totalAttempts);

        scanner.close();
    }
}

