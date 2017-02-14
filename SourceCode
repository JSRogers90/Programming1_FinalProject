package lab4;

/**
 *
 * @author joshuarogers
 */

import java.util.*;
import java.io.*;

public class Lab4 {
    
    public static void main(String[] args) throws IOException
    {
        String[] playDeck;
        String rules;
        String cont;
        ArrayList<String> playerHand = new ArrayList<>();
        int playerValue;
        ArrayList<String> dealerHand = new ArrayList<>();
        int dealerValue;
        int deckPos;
        String hitStay;
        boolean bust = false;
        boolean containsAce = false;
        
        Scanner keyboard = new Scanner(System.in);
        
        System.out.println("BLACKJACK!");
        System.out.println();
        System.out.println("The object of the game is to get a combination");
        System.out.println("of cards that is closer to 21 than the dealers,");
        System.out.println("without going over 21.");
        System.out.println();
        System.out.println("Would you like to view the rules?");
        rules = keyboard.nextLine();
        
        if(rules.equalsIgnoreCase("YES"))
        {
            showRules();
        }
        else System.out.println();
        
        do
        {
            playDeck = shuffleDeck();
            deckPos = 0;
            playerHand.add(playDeck[deckPos]);
            deckPos ++;
            dealerHand.add(playDeck[deckPos]);
            deckPos ++;
            playerHand.add(playDeck[deckPos]);
            deckPos ++;
            dealerHand.add(playDeck[deckPos]);
            deckPos ++;
            playerValue = handValue(playerHand);
            dealerValue = handValue(dealerHand);
            if(playerValue == 21 && playerValue > dealerValue)
            {
                displayPlayerHand(playerHand, playerValue);
                displayDealerHand(dealerHand, dealerValue);
                System.out.println("BLACKJACK!");
                System.out.println("Congratulations, you have won!");
            }
            else if(playerValue == 21 && dealerValue == 21)
            {
                displayPlayerHand(playerHand, playerValue);
                displayDealerHand(dealerHand, dealerValue);
                System.out.println("Push");
            }
            else
            {    
                displayPlayerHand(playerHand, playerValue);
                displayShows(dealerHand);
                System.out.println("Hit or Stay?");
                hitStay = keyboard.nextLine();
                while(hitStay.equalsIgnoreCase("HIT"))
                {
                    playerHand.add(playDeck[deckPos]);
                    deckPos ++;
                    playerValue = handValue(playerHand);
                    if(playerValue <= 21)
                    {
                        displayPlayerHand(playerHand, playerValue);
                        displayShows(dealerHand);
                        System.out.println("Hit or Stay");
                        hitStay = keyboard.nextLine();
                    }
                    else
                    {
                        bust = true;
                        hitStay = "bust";
                    }
                }
                if (bust)
                {
                    displayPlayerHand(playerHand, playerValue);
                    displayDealerHand(dealerHand, dealerValue);
                    System.out.println("You Bust!");
                    System.out.println("Sorry, you have lost.");
                    bust = false;
                }
                else
                {
                    displayPlayerHand(playerHand, playerValue);
                    displayDealerHand(dealerHand, dealerValue);
                    while(dealerValue < 18)
                    {
                        for(int d = 0; d < dealerHand.size(); d ++)
                        {
                            String card = dealerHand.get(d);
                            if(card.contains("A"))
                            {
                                containsAce = true;
                            }
                        }
                        if(containsAce && dealerValue == 17)
                        {
                            System.out.println("Dealer Hits.");
                            dealerHand.add(playDeck[deckPos]);
                            deckPos ++;
                            dealerValue = handValue(dealerHand);
                            displayPlayerHand(playerHand, playerValue);
                            displayDealerHand(dealerHand, dealerValue);
                        }
                        else if(dealerValue < 17)
                        {
                            System.out.println("Dealer Hits.");
                            dealerHand.add(playDeck[deckPos]);
                            deckPos ++;
                            dealerValue = handValue(dealerHand);
                            displayPlayerHand(playerHand, playerValue);
                            displayDealerHand(dealerHand, dealerValue);
                        }
                        else break;
                    }
                    containsAce = false;
                    if((playerValue > dealerValue || dealerValue > 21) && playerValue <= 21)
                        System.out.println("You have won!");
                    else if(playerValue == dealerValue)
                        System.out.println("Push.");
                    else System.out.println("Sorry, you have lost.");
                }
            }    
            System.out.println();
            System.out.println("Would you like to play again?");
            cont = keyboard.nextLine();
            if (cont.equalsIgnoreCase("YES"))
            {
                playerHand = clearHand(playerHand);
                dealerHand = clearHand(dealerHand);
            }
        }while(cont.equalsIgnoreCase("YES"));
    }
 
    public static void showRules()
    {
        System.out.println();
        System.out.println("The cards are displayed as value-suit.");
        System.out.println("For example the ace of spades is displayed \"A-S\"");
        System.out.println("the ten of hearts is displayed \"10-H\", etc.");
        System.out.println();
        System.out.println("Aces count as either 11 or 1,");
        System.out.println("Face cards count as 10,");
        System.out.println("All other cards count as face value");
        System.out.println();
        System.out.println("The dealer will stay on 17 or higher,");
        System.out.println("except if the dealer has a soft 17.");
        System.out.println("This is any combination adding to 17 that");
        System.out.println("contains an ace counting as an 11.");
        System.out.println();
        System.out.println("There are no gambling house rules allowed:");
        System.out.println("These include actions such as splitting a pair");
        System.out.println("and \"doubling down\"");
        System.out.println("\n");
    }    
    
    public static int[] shuffleOrder()
    {
        final int deckSize = 52;
        int[] shuffleOrder = new int[deckSize];
        int s;
        Random rand = new Random();
        int hold;
        
        for(s = 0; s < deckSize; s++)
        {
            hold = rand.nextInt(deckSize) + 1;
            for(int h = 0; h <= s; h++)
            {
                if(shuffleOrder[h] == hold)
                {
                    hold = rand.nextInt(deckSize) + 1;
                    h = -1;
                }
            }
            shuffleOrder[s] = hold;
        }     
        
        return shuffleOrder;
        
    }
    
    public static String[] shuffleDeck()
    {
        final int deckSize = 52;
        String[] deck = {"A-D","2-D","3-D","4-D","5-D","6-D","7-D","8-D","9-D","10-D","J-D","Q-D","K-D","A-C","2-C","3-C","4-C","5-C","6-C","7-C","8-C","9-C","10-C","J-C","Q-C","K-C","A-H","2-H","3-H","4-H","5-H","6-H","7-H","8-H","9-H","10-H","J-H","Q-H","K-H","A-S","2-S","3-S","4-S","5-S","6-S","7-S","8-S","9-S","10-S","J-S","Q-S","K-S"};
        int[] deckIndex;
        String[] shuffleDeck = new String[deckSize];
        
        deckIndex = shuffleOrder();

        for(int d = 0; d < deckSize; d++)
        {
            shuffleDeck[d] = deck[deckIndex[d] - 1];
        }
        
        return shuffleDeck;
    }
    
    public static ArrayList<String> clearHand(ArrayList<String> hand)
    {
        int count = hand.size();
        for(int Index = 0; Index < count; Index++)
        {
            hand.remove(0);
        }
        
        return hand;
    }
    
    public static void displayPlayerHand(ArrayList<String> hand, int value)
    {
        System.out.println();
        System.out.println("Players Hand:");
        for(int Index = 0; Index < hand.size(); Index++)
        {
            System.out.print(hand.get(Index) + " ");
        }
        System.out.println();
        System.out.println("Player Total = " + value);
    }
    
    public static void displayShows(ArrayList<String> hand)
    {
        System.out.println("Dealer Shows:");
        System.out.println(hand.get(0));
    }

    public static void displayDealerHand(ArrayList<String> hand, int value)
    {
        System.out.println("Dealers Hand:");
        for(int Index = 0; Index < hand.size(); Index++)
        {
            System.out.print(hand.get(Index) + " ");
        }
        System.out.println();
        System.out.println("Dealer Total = " + value);
    }
    
    public static int handValue(ArrayList<String> hand)
    {
        int handValue = 0;
        String card;
        int cardValue;
        boolean containsAce = false;
        
        for(int Index = 0; Index < hand.size(); Index++)
        {
            card = hand.get(Index);
            if(card.contains("K") || card.contains("Q") || card.contains("J") || card.contains("10"))
            {
                cardValue = 10;
                handValue += cardValue;
            }
            else if (card.contains("9"))
            {
                cardValue = 9;
                handValue += cardValue;
            }
            else if (card.contains("8"))
            {
                cardValue = 8;
                handValue += cardValue;
            }
            else if (card.contains("7"))
            {
                cardValue = 7;
                handValue += cardValue;
            }
            else if (card.contains("6"))
            {
                cardValue = 6;
                handValue += cardValue;
            }
            else if (card.contains("5"))
            {
                cardValue = 5;
                handValue += cardValue;
            }
            else if (card.contains("4"))
            {
                cardValue = 4;
                handValue += cardValue;
            }
            else if (card.contains("3"))
            {
                cardValue = 3;
                handValue += cardValue;
            }
            else if (card.contains("2"))
            {
                cardValue = 2;
                handValue += cardValue;
            }
            else if (card.contains("A"))
            {
                containsAce = true;
            }            
        }
        if(containsAce)
        {
            if((handValue + 11) <= 21)
            {
                cardValue = 11;
                handValue += cardValue;
            }
            else
            {
                cardValue = 1;
                handValue += cardValue;
            }
        }
        
        return handValue;
    }
    
}
