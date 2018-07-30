# deckLibraryJS

JS library for a deck of cards.

- Generate the deck of cards.

```javascript
generate_deck() {
    let card = (suit, value) => {
      this.name = value + ' of ' + suit;
      this.suit = suit;
      this.value = value;

      return { name: this.name, suit: this.suit, value: this.value };
    };

    let values = [
      '1',
      '2',
      '3',
      '4',
      '5',
      '6',
      '7',
      '8',
      '9',
      '10',
      'J',
      'Q',
      'K',
      'A'
    ];
    let suits = ['Clubs', 'Diamonds', 'Spades', 'Hearts'];

    for (let s = 0; s < suits.length; s++) {
      for (let v = 0; v < values.length; v++) {
        this.deck.push(card(suits[s], values[v]));
      }
    }
  }
```

- Print the array of card objects in the deck.

```javascript
print_deck() {
    if (this.deck.length == 0) {
      console.log('The deck has not been generated');
    } else {
      for (let c = 0; c < this.deck.length; c++) {
        console.log(this.deck[c]);
      }
    }
```

- Shuffle the deck randomly.

```javascript
shuffle() {
    let current_ind = this.deck.length,
      temp_val,
      rand_ind;

    while (0 != current_ind) {
      rand_ind = Math.floor(Math.random() * current_ind);
      current_ind -= 1;
      temp_val = this.deck[current_ind];
      this.deck[current_ind] = this.deck[rand_ind];
      this.deck[rand_ind] = temp_val;
    }
  }
```

- Deal a card - returns card object.

```javascript
deal() {
    let dealt_card = this.deck.shift();
    this.dealt_cards.push(dealt_card);
    return dealt_card;
  }
```

- Put most recently dealt card back on top of deck.

```javascript
  replace() {
    this.deck.unshift(this.dealt_cards.shift());
  }
```

- Remove the current deck.

```javascript
  clear_deck() {
    this.deck = [];
  }
```
