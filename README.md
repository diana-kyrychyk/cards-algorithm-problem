# Algorithm problem

## Choosing the strongest card set

### Problem overview
You are given N cards. Each card consists of a suit and a rank.
There are four suits: **S** (Spades), **H** (Hearts), **D** (Diamonds), and **C** (Clubs), and thirteen ranks, ordered (from the lowest to the highest) **2, 3, 4, 5, 6, 7, 8, 9, 10, J (Jack), Q (Queen), K (King), and A (Ace)**.

Each card is represented by a string in the format **<rank><suit>**.
For example, 10 of Spades is described as **"10S"**, and Queen of Hearts as **"QH"**.

There are six ranked card sets (described in detail below). Sets are ordered by their strength from the weakest to the strongest. Your task is to detect the card sets that can be formed from the given cards. Detecting each card set is scored separately and is worth an equal number of points. If you detect more than one set, select the strongest one.

#### Write a function:

`class Solution { public Results solution(String[] cards); }`
that given an array of strings `cards`, returns a **Results** object representing the strongest card set that can be formed.

Assume that the following declarations are given:

```
class Results { 
public String set_name;
public String[] selected_cards;
}
```

* `set_name` is a string which should be the name of detected set (see below);
* `selected_cards` is a list of strings, which should be made of cards that form the detected set. Cards can be listed in any order.

#### Card Sets

There are six card sets ordered by their strength from the weakest (single card) to the strongest (a triple and a pair).

##### Set 1: Single Card

* **Name**: `single card`
* **Description**: A single card of the highest rank; the suit does not matter.

For example, for cards = ["2H", "4H", "7C", "9D", "10D", "KS"], your function should return:
```
{ 
"set_name" = "single card",
"selected_cards" = ["KS"]
}
```


##### Set 2: Pair

* **Name**: `pair`
* **Description**: Two cards sharing the same rank; suits do not matter. If there are multiple pairs, return any one with the highest rank.

For example, for cards = ["AS", "10H", "8H", "10S", "8D"], one of the correct results is:
```
{ 
"set_name" = "pair",
"selected_cards" = ["10H", "10S"]
}
```

##### Set 3: Triple

* **Name**: `triple`
* **Description**: Three cards sharing the same rank; suits do not matter. If there are multiple ways to choose a triple, return any with the highest rank.

For example, for cards = ["AS", "JS", "AH", "AD", "10D", "AC"], one of the correct results is:
```
{ 
"set_name" = "triple",
"selected_cards" = ["AH", "AD", "AC"]
}
```

##### Set 4: Five in a Row

* **Name**: `five in a row`
* **Description**: Five cards of consecutive ranks starting with the highest possible rank; suits do not matter. If there are multiple ways to choose five such cards, return any.

For example, for cards = ["6H", "7S", "8S", "9S", "10S", "JD", "JC", "KC", "AC"], one of the correct results is:
```
{ 
"set_name" = "five in a row",
"selected_cards" = ["7S", "8S", "9S", "10S", "JC"]
}
```

##### Set 5: Suit

* **Name**: `suit`
* **Description**: Five cards sharing the same suit; the ranks do not matter. If there are multiple ways to choose five cards with the same suit, choose any set with the highest suit. The order of the suits (from the highest to the lowest) is S, H, D, C.

For example, for cards = ["2D", "4D", "6D", "8D", "9D", "AC", "KC", "QC", "JC", "7C"], one of the correct results is:
```
{ 
"set_name" = "suit",
"selected_cards" = ["2D", "4D", "6D", "8D", "9D"]
}
```

##### Set 6: Triple and a Pair

* **Name**: `a triple and a pair`
* **Description**: Five cards, consisting of a triple (three cards of the same rank) and a pair (two cards of the same rank). If there are multiple ways to choose this set, choose one with the highest rank of the triple, then one with the highest rank of the pair. The suits do not matter.

For example, for cards = ["10D", "10H", "10C", "2S", "2H", "2D", "JH", "JC"], one of the correct results is:
```
{ 
"set_name" = "a triple and a pair",
"selected_cards" = ["10D", "10H", "10C", "JH", "JC"]
}
```

#### Constraints
* N is an integer within the range [1..10);
* The elements of `cards` are all distinct;
* Each string in array `cards` is a correct representation of a card in "`<rank><suit>`" format.
