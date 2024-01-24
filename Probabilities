import random as rd

from collections import Counter

import pandas as pd

def deck():
    
    cards_deck = [1,1,1,1,2,2,2,2,3,3,3,3,4,4,4,4,5,5,5,5,6,6,6,6,7,7,7,7,8,8,8,8,9,9,9,9,10,10,10,10,11,11,11,11,12,12,12,12,13,13,13,13]
    rd.shuffle(cards_deck)
    
    return cards_deck



def delete_random(desire_list, times ): #????
    
    list_of_desire_numbers = rd.sample(desire_list, times)
    
    for i in list_of_desire_numbers:
        desire_list.remove(i)
    
    return list_of_desire_numbers
    
    

def hand_construction(playing_deck,hand_list):
    
    hand_list.append(playing_deck[0])
    
    playing_deck.pop(0)
    


def card_output(players):  #Counting the dealer as a player
    
    table_deck = deck()
    
    my_hand = []
    
    for i in range(2):
    
        hand_construction(table_deck,my_hand)
        
        for i in range(players):
            table_deck.pop(0)
    
    table_deck.pop(0)
    
    for i in range(3):
        hand_construction(table_deck, my_hand)
        
    table_deck.pop(0)
    hand_construction(table_deck,my_hand)
    table_deck.pop(0)
    hand_construction(table_deck,my_hand) 
    
    return my_hand

    

def color_output(all_players):
    
    color_deck = [1,1,1,1,1,1,1,1,1,1,1,1,1,2,2,2,2,2,2,2,2,2,2,2,2,2,3,3,3,3,3,3,3,3,3,3,3,3,3,4,4,4,4,4,4,4,4,4,4,4,4,4]
    rd.shuffle(color_deck)
    
    
    color_hand = []
    
    for i in range(2):
    
        hand_construction(color_deck,color_hand)
        
        for i in range(all_players):
            color_deck.pop(0)
    
    color_deck.pop(0)
    
    for i in range(3):
        hand_construction(color_deck, color_hand)
        
    color_deck.pop(0)
    hand_construction(color_deck,color_hand)
    color_deck.pop(0)
    hand_construction(color_deck,color_hand) 
    
    color_hand_counter = list((Counter(color_hand)).values())
    
    return color_hand
 
  
    
def rules(my_hand_possibilities,contestants):
    
    counter_hand = Counter(my_hand_possibilities)
    counter_hand = counter_hand.values()
    counter_hand = list(counter_hand)

    full_house = [3,2]
    double_pairs = list((Counter(counter_hand)).values())    
    straight = [[1,2,3,4,5],[2,3,4,5,6],[3,4,5,6,7],[4,5,6,7,8],[5,6,7,8,9],[6,7,8,9,10],[7,8,9,10,11],[8,9,10,11,12],[9,10,11,12,13],[10,11,12,13,1]]
    
    hand_color = color_output(contestants)
    hand_color =  list((Counter(hand_color)).values())
    
    if 4 in counter_hand:

        return "Poker"
 
    elif all(x in counter_hand for x in full_house) == True:

        return "Full_House"
        
    elif 3 in counter_hand:

        return "Three_of_a_kind"
        
    
    elif 2 in double_pairs:

        return "Double_Pairs"
    
    elif 3 in double_pairs:

        return "Double_Pairs"
        
    elif 2 in counter_hand:

        return "Pair"
    
    elif 5 in  hand_color:
        for i in straight:
            if all(x in my_hand_possibilities for x in i) == True:

                return "Straight_flush"

        return "Color"
    
    elif 6 in  hand_color:
        
        for i in straight:
            if all(x in my_hand_possibilities for x in i) == True:

                return "Straight_flush"

        return "Color"
    
    elif 7 in  hand_color:
        for i in straight:
            if all(x in my_hand_possibilities for x in i) == True:
                
                return "Straight_flush"

        return "Color"

    
    for i in straight:
        if all(x in my_hand_possibilities for x in i) == True: 
            return "Straight"
    
    else:

        return "High_card"
    
  


recording = []

for i in range(10000000):
    recording.append(rules(card_output(4),4))
    
    
recording_record = Counter(recording)


for item, count in recording_record.items():
    recording_record[item] /= 10000000



print(recording_record)



df = pd.DataFrame.from_dict(recording_record, orient= "index").reset_index()


df.to_excel("Poker_Hands.xlsx")
