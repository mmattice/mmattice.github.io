.. title: EMVCo's response
.. slug: emvcos-response
.. date: 2016-05-02 15:13:33 UTC
.. tags: ASN.1,EMV,EMVCo,specifications,ISO-8825,X.690,tech
.. category: 
.. link: 
.. description: 
.. type: text

A little more than a month later, I got a response from EMVCo to `my request <link://slug/emvco-request>`_.  It's about what I expected.  I'm not sure they've read their own specification.

.. TEASER_END

..

  Response:

  Thank you for your query.

  There is a slight difference between ISO and EMV tag coding. According to the EMV Book3 requirement, bit7 ~ bit1 of the first byte would not be part of tag number when these bits equals '11111', the tag number begins at the second byte in this case.
 
  As the example tag "9F02", is an valid EMV tag, but not an ISO tag. This also means that you might consider the AIP and Amount, Authorised (numeric) to both have tag number 02; it is not helpful to refer to manage tags in this way, and hence EMV uses the full tag throughout.

  Sincerely,

  The EMVCo Secretariat 

  Message ID: 1007

For starters, bit7 ~ bit1?  Suddenly it's grown a couple.
