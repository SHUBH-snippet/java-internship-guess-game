# java-internship-guess-game
 
import java.util.Random;
import java.util.Scanner;

public class Main{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int lowerBound = 1;
        int upperBound = 100;
        int numberToGuess = random.nextInt(upperBound - lowerBound + 1) + lowerBound;

        int maxGuesses = 10;
        int remainingGuesses = maxGuesses;
        int userScore = 0;

        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("I have selected a number between " + lowerBound + " and " + upperBound + ". You have " + maxGuesses + " attempts to guess it.");

        while (remainingGuesses > 0) {
            System.out.print("Enter your guess: ");
            int userGuess = scanner.nextInt();

            if (userGuess < lowerBound || userGuess > upperBound) {
                System.out.println("Please enter a number between " + lowerBound + " and " + upperBound + ".");
                continue;
            }

            if (userGuess == numberToGuess) {
                System.out.println("Congratulations! You guessed the correct number.");
                userScore += remainingGuesses;
                break;
            } else if (userGuess < numberToGuess) {
                System.out.println("Try a higher number.");
            } else {
                System.out.println("Try a lower number.");
            }

            remainingGuesses--;
            if (remainingGuesses > 0) {
                System.out.println("You have " + remainingGuesses + " guesses left.");
            } else {
                System.out.println("You've run out of guesses. The correct number was " + numberToGuess + ".");
            }
        }

        System.out.println("Your score: " + userScore);
        System.out.println("Thanks for playing!");

        scanner.close();
    }
}
