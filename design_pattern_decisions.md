# Design pattern decisions

## Design patterns used in this project:

1. Circuit Breaker - I implemeted this in multiple ways one so that certain owners in particaular parts of the contract has abbilies to stop state changing functionalities for example to make sure that the person who does get tipped gets the ether to their account from the insta feed. For example:

```
address payable _author = _image.author;
    // Pay the author by sending them Ether
    address(_author).transfer(msg.value);
    // Increment the tip amount
    _image.tipAmount = _image.tipAmount + msg.value;
```

2. Fail Early and Fail Loud - I take advantage of using the `require ` keywords to throw as early as possible whenever certain conditions are not met. For example in the `uploadImage()`once the user uploaded an image it has to have the required amount of text in the fields. For example :

```
    // Make sure the image hash exists
    require(bytes(_imgHash).length > 0);
    // Make sure image description exists
    require(bytes(_description).length > 0);
    // Make sure uploader address exists
    require(msg.sender!=address(0));`
    ``
```
