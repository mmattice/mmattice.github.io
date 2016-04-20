.. title: Quick Chip EMV
.. slug: quick-chip-emv
.. date: 2016-04-20 02:35:51 UTC
.. tags: EMV,Visa,tech
.. category: Commentary 
.. link: 
.. description: 
.. type: text

So Google Now cards notified me about Visa's "new" Quick Chip EMV spec today.  Apparently I've been profiled as someone interested in EMV.  Go figure.

From the `Quick Chip EMV Specification <https://www.visa.com/chip/merchants/grow-your-business/payment-technologies/credit-card-chip/docs/quick-chip-emv-specification.pdf>`_:

  `Note: Using Quick Chip, the insertion, reading, and subsequent removal of the card may occur while the sales transaction is being rung up; i.e., before the final amount is known.`

That's super cool!  It works much closer to the way a normal mag-stripe transaction would work in our stores.  Our customer service people do their thing while the customer does theirs in preparation for the end of the transaction and then the request happens as soon as the CS person is done and the customer verifies the amount.  This is much better than waiting for a response from the bank before you can pull your card.

Reading the specification, it seems that the terminal's EMV kernel tells the card "Yep, I can't go online, go ahead and give me stuff for a deferred authentication".  This will only work if the terminal is doing "Online" verification, which I'd guess most, if not all US retailers are doing with magstripe auths.

I started to wonder why Visa didn't come up with this years ago for everyone else that does EMV in the world. After reading the spec, it dawned on me.  This spec only works for *ONLINE* transactions.  The rest of the world used a lot of offline authentications because they've historically had to pay for individual phone calls and those communications were less reliable than the always online terminals the US has used for so many years.

What I find interesting is that Visa didn't bother fixing this problem 10 years ago for the UK.  Apparently the US consumer can't have anything get in the way of charging up their credit cards.
