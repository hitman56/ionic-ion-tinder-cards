Ionic Contrib: Swipeable Cards
===================

Swipeable card based layout for Ionic and Angular. As seen in apps like [Jelly](http://jelly.co/)

[Demo](http://codepen.io/ionic/pen/nxEdH)

## Usage

Include `ionic.tdcards.js` after the rest of your Ionic and Angular includes. Then use the following AngularJS directives:

```html
<td-cards>
  <td-card ng-repeat="card in cards" on-destroy="cardDestroyed($index)" on-swipe="cardSwiped($index)">
    Card content here
  </td-card>
</td-cards>
```

To add new cards dynamically, just add them to the cards array:

```javascript
$scope.cards = [
  { // card 1 },
  { // card 2 }
];

$scope.cardDestroyed = function(index) {
  $scope.cards.splice(index, 1);
};

$scope.cardSwiped = function(index) {
  var newCard = // new card data
  $scope.cards.push(newCard);
};
```

### Programatically swipe cards

It is possible to swipe cards programatically.
See this [Codepen demo](http://codepen.io/julienroubieu/pen/mJeJJE).

You will need first to add an object in your scope to receive the swipe functions:

```javascript
$scope.cardsControl = {}
```

Then, pass this object to the td-cards element, through the `control` attribute.

```html
<td-cards control="cardsControl">
  <td-card ng-repeat="card in cards" on-destroy="cardDestroyed($index)" on-swipe="cardSwiped($index)">
    Card content here
  </td-card>
</td-cards>
```

You can now swipe the top card from your controller or HTML elements:

```javascript
$scope.cardsControl.swipeLeft()
$scope.cardsControl.swipeRight()
```