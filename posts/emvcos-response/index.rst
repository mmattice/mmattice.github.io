.. title: EMVCo's response
.. slug: emvcos-response
.. date: 2016-05-02 15:13:33 UTC
.. tags: ASN.1,EMV,EMVCo,specifications,ISO-8825,X.690,tech
.. category: Commentary
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

For starters, bit7 ~ bit1?  I'd say it's grown a bit, but it's grown two.  Perhaps they're confused and referring to the second byte.  Who knows.

My response to them (Comment ID 12106):

  If there is a slight difference, then that difference should be documented instead of the ISO-8825 spec quoted directly by Annex B1.  Repeatedly calling your data transport method BER-TLV, quoting ISO-8825 and mis-implementing ISO-7816 (which clarifies the above better than 8825 and is quite specific to ICCs) when both ISO standards are referred to as 'Normative References' is confusing to implementation teams and is blatantly false.

    `According to ISO/IEC 8825, Table 36 defines the coding rules of the subsequent bytes of a BER-TLV tag when tag numbers >= 31 are used (that is, bits b5 - b1 of the first byte equal '11111')`

  This is an exact quote (barring the inability to reproduce the greater than or equal to) of your spec.  "When tag numbers >= 31 are used".  That means that 9F02 should have a tag number >= 31.  It does not.  If you want to go the route that '9F02' is >= 31, then ALL EMV tags are >= 31.

  I understand the desire to stick to ones guns about something that affects billions of devices in the field, but this is not assisting anyone trying to implement your broken specification.

  Sincerely,

  Mike Mattice

I very surprised I got a response at all, but not surprised they continue to misunderstand what they, themselves, have published.  They have an internalized idea of what it should communicate, but that doesn't match what's on the paper.  Having had to work with other vendors and their broken specs before, I'm not sure why it still surprises me when this happens.
