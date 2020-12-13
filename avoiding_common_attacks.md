# Avoiding Common Attacks

## Forcibly Sending Ether to a contract and Out of Gas exepction

1. Forcibly Sending Ether to a contract - A point of proable vulnerablity would be to send a tip to a picture if it wasn't either there. I made sure that my contract logic disaalowed payments to the contract if something wasn't there.A way I avoided this in my async function :

```
      await decentragram.tipImageOwner(99, { from: tipper, value: web3.utils.toWei('1', 'Ether')}).should.be.rejected;
```

2. Out of Gas expection - A point of propable vunerablity in smart contract would have been the `tipImageOwner` function. Without the tests it didn't check the ether amount of the person who is tipping the author of the picture.The call function will end up in an out-of-gas execption if not enough gas units are available from the person who is tipping. A way I avoived this:

```let newAuthorBalance
      newAuthorBalance = await web3.eth.getBalance(author)
      newAuthorBalance = new web3.utils.BN(newAuthorBalance)

      let tipImageOwner
      tipImageOwner = web3.utils.toWei('1', 'Ether')
      tipImageOwner = new web3.utils.BN(tipImageOwner)

      const expectedBalance = oldAuthorBalance.add(tipImageOwner)

      assert.equal(newAuthorBalance.toString(), expectedBalance.toString())
```
