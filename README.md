// Blackjack Game
// By: Austin Wilwayco

// Scanner
import java.util.Scanner;

public class Blackjack {
    public static void main (String args[]) {

        // Variables
        int option = 1;
        int game = 1;
        int tieGames = 0;
        int dealerWins = 0;
        double playerWins = 0;
        int playerWin = 0;
        double gamesPlayed = 0;
        int gamePlayed = 0;

        //Scanner
        Scanner Scanner = new Scanner(System.in);

        // Random Numbers
        P1Random rng = new P1Random();

        // Loop
        while (option == 1) {

            // Hand Variable
            int hand = 0;

            // Start Game
            System.out.println("START GAME #" + (game) + "\n");

            // Random Number Given to Player (First Card)
            int myNumber = rng.nextInt(13) + 1;

            // Value Card
            // 1 ACE!
            // 2-10 (correspond to their face values)
            // 11 JACK! = 10
            // 12 QUEEN! = 10
            // 13 KING! = 10
            if (myNumber == 1) {
                System.out.println("Your card is a ACE!");
                hand = hand + 1;
                System.out.println("Your hand is: " + (hand));
            } else if (myNumber == 11) {
                System.out.println("Your card is a JACK!");
                hand = hand + 10;
                System.out.println("Your hand is: " + (hand));
            } else if (myNumber == 12) {
                System.out.println("Your card is a QUEEN!");
                hand = hand + 10;
                System.out.println("Your hand is: " + (hand));
            } else if (myNumber == 13) {
                System.out.println("Your card is a KING!");
                hand = hand + 10;
                System.out.println("Your hand is: " + (hand));
            } else {
                System.out.println("Your card is a " + (myNumber) + "!");
                hand = hand + (myNumber);
                System.out.println("Your hand is: " + (hand));
            }
            while (hand < 21) {
                // Menu Selection
                System.out.println(
                        "\n1. Get another card\n" +
                                "2. Hold hand\n" +
                                "3. Print statistics\n" +
                                "4. Exit\n" +
                                "\n" +
                                "Choose an option:"
                );
                int choice;
                choice = Scanner.nextInt();

                if (choice == 1) {
                    // Get another card
                    myNumber = rng.nextInt(13) + 1;
                    if (myNumber == 1) {
                        System.out.println("Your card is a ACE!");
                        hand = hand + 1;
                        System.out.println("Your hand is: " + (hand));
                    } else if (myNumber == 11) {
                        System.out.println("Your card is a JACK!");
                        hand = hand + 10;
                        System.out.println("Your hand is: " + (hand));
                    } else if (myNumber == 12) {
                        System.out.println("Your card is a QUEEN!");
                        hand = hand + 10;
                        System.out.println("Your hand is: " + (hand));
                    } else if (myNumber == 13) {
                        System.out.println("Your card is a KING!");
                        hand = hand + 10;
                        System.out.println("Your hand is: " + (hand));
                    } else {
                        System.out.println("Your card is a " + (myNumber) + "!");
                        hand = hand + (myNumber);
                        System.out.println("Your hand is: " + (hand));
                    }

                } else if (choice == 2) {
                    // Hold Hand
                    int myValue = rng.nextInt(11) + 16;
                    System.out.println("Dealer's hand: " + (myValue));
                    System.out.println("Your hand is: " + (hand) + "\n");
                    if (myValue > 21) {
                        System.out.println("You win!" + "\n");
                        playerWins = playerWins + 1;
                        playerWin = playerWin + 1;
                        gamesPlayed = gamesPlayed + 1;
                        gamePlayed = gamePlayed + 1;
                        break;
                    } else if (myValue < hand) {
                        System.out.println("You win!" + "\n");
                        playerWins = playerWins + 1;
                        playerWin = playerWin + 1;
                        gamesPlayed = gamesPlayed + 1;
                        gamePlayed = gamePlayed + 1;
                        break;
                    } else if (myValue == hand) {
                        System.out.println("It's a tie! No one wins!" + "\n");
                        tieGames = tieGames + 1;
                        gamesPlayed = gamesPlayed + 1;
                        gamePlayed = gamePlayed + 1;
                        break;
                    } else if (myValue > hand) {
                        System.out.println("Dealer wins!" + "\n");
                        dealerWins = dealerWins + 1;
                        gamesPlayed = gamesPlayed + 1;
                        gamePlayed = gamePlayed + 1;
                        break;
                    }

                } else if (choice == 3) {
                    // Print Statistics
                    System.out.println("Number of Player wins: " + (playerWin));
                    System.out.println("Number of Dealer wins: " + (dealerWins));
                    System.out.println("Number of tie games: " + (tieGames));
                    System.out.println("Total # of games played is: " + (gamePlayed));
                    System.out.println("Percentage of Player wins: " + ((playerWins / gamesPlayed) * 100) + "%");

                } else if (choice == 4) {
                    // Exit
                    option = 0;
                    break;

                } else {
                    // Invalid Input
                    System.out.println(
                            "\n" +
                                    "Invalid input!\n" +
                                    "Please enter an integer value between 1 and 4."
                    );
                }

            }

            // Special Cases Outside Loop (Hand >= 21)
            if (hand == 21) {
                System.out.println("\nBLACKJACK! You win!" + "\n");
                playerWins = playerWins + 1;
                playerWin = playerWin + 1;
                gamesPlayed = gamesPlayed + 1;
                gamePlayed = gamePlayed + 1;
            } else if (hand > 21) {
                System.out.println("\nYou exceeded 21! You lose." + "\n");
                dealerWins = dealerWins + 1;
                gamesPlayed = gamesPlayed + 1;
                gamePlayed = gamePlayed + 1;
            }

            // Game Variable
            game = game + 1;
        }
    }

    // P1Random
    public static class P1Random
    {
        private long next;

        public P1Random()
        {
            next = 0;
        }

        private short nextShort()
        {
            return nextShort(Short.MAX_VALUE);
        }

        private short nextShort(short limit)
        {
            next = next * 1103515245 + 12345;
            return (short) Math.abs(((next / 65536) % limit));
        }

        private int nextInt()
        {
            return nextInt(Integer.MAX_VALUE);
        }

        public int nextInt(int limit)
        {
            return ((((int) nextShort()) << 16) | ((int) nextShort())) % limit;
        }

        private double nextDouble()
        {
            return (double) nextInt() / (double) Integer.MAX_VALUE;
        }
    }
}

