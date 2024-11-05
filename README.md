import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Random random = new Random();
        int rndmNum = random.nextInt(100) + 1;
        Scanner scanner = new java.util.Scanner(System.in);
        int attempts = 0;
        boolean CorrectGuesses = false;

        System.out.println("Hello! This is the Improved Guessing Game!");
        System.out.println("In my mind I have chosen a random number between 1 and 100. Try and guess it!");
        System.out.println("Enter 'quit' whenever you want to exit the game.");

        while (!CorrectGuesses) {
            System.out.print("Type in your first guess: ");
            String input = scanner.nextLine();

            if (input.equalsIgnoreCase("stop")) {
                System.out.println("Good job! The chosen number is " + rndmNum + ".");
                break;
            }

            int guess = Integer.parseInt(input);
            attempts++;

            if (guess < 1 || guess > 100) {
                System.out.println("Think of a number between 1 and 100 and type it in.");
            } else if (guess < rndmNum) {
                System.out.println("My chosen number is bigger than " + guess + "! You should try again!");
            } else if (guess > rndmNum) {
                System.out.println("My chosen number is smaller than " + guess + "! You should try again.");
            } else {
                CorrectGuesses = true;
                System.out.println("Bravo! You now know the chosen number You did it in only " + attempts + " attempts.");
            }

            if (!CorrectGuesses && attempts == 10) {
                if (rndmNum % 2 == 0) {
                    System.out.println("You get a hint: My chosen number is even.");
                } else {
                    System.out.println("You get a hint: My chosen number is odd.");
                }
            }
        }
    }
}
