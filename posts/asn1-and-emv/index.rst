.. title: ASN.1 and EMV
.. slug: asn1-and-emv
.. date: 2016-03-27 23:41:16 UTC
.. tags: ASN.1,EMV,specifications
.. category: Commentary
.. link: 
.. description: 
.. type: text

I've been tasked with making EMV work for the company I work for and more importantly, for our customers.  As I write python most of the time these days, I looked around for a tool to play with `ASN.1 <https://www.itu.int/ITU-T/studygroups/com17/languages/X.690-0207.pdf>`_.  A stupidly quick Google landed me on `pyasn1 <http://pyasn1.sf.net>`_.  I made a run at using it to manipulate the BER-TLV the `EMV 4.3 Book 3 <https://www.emvco.com/download_agreement.aspx?id=654>`_ requires.  This resulted in some difficulties.  I reported a `bug <https://sourceforge.net/p/pyasn1/mailman/message/34776952/>`_ via the mailing list.

Thinks have changed in the past two months.

pyasn1 moved to `github <https://github.com/etingof/pyasn1>`_.  I'd built some work arounds and submitted a `PR <https://github.com/etingof/pyasn1/pull/5>`_.  I ended up splitting the PR into `another <https://github.com/etingof/pyasn1/pull/6>`_ because that one could break extended tags everywhere.  The issues I saw with the EMV tags and how they decoded are in that first PR, and also in `emv-asn1 <https://github.com/mmattice/emv-asn1>`_, which I wrote with my assumptions I'd codified in `bugfix/emv <https://github.com/mmattice/pyasn1/tree/bugfix/emv>`_.

I did these things because I was sure EMVCo would surely stick to standards and that they had interpreted the ASN.1 spec correctly.  I now know I was wrong.

I've built, and am using, an internal version of pyasn1 and that allows me to encode/decode this EMV stuff 'properly'.  I've even made a decoder/encoder pair for our pinpad's odd text based format with these assumptions.

Now, however, I want to burn it all to the ground.

Today I found `grizzly_ber <https://github.com/Shopify/grizzly_ber>`_, which is the same workaround in Ruby.  I realized it wasn't just me that was having trouble with this.

From `ASN.1 <https://www.itu.int/ITU-T/studygroups/com17/languages/X.690-0207.pdf>`_:

  8.1.2.2 For tags with a number ranging from zero to 30 (inclusive), the identifier octets shall comprise a single octet encoded as follows:
    a) bits 8 and 7 shall be encoded to represent the class of the tag as specified in Table 1;
    b) bit 6 shall be a zero or a one according to the rules of 8.1.2.5;
    c) bits 5 to 1 shall encode the number of the tag as a binary integer with bit 5 as the most significant bit. 

  8.1.2.4 For tags with a number greater than or equal to 31, the identifier shall comprise a leading octet followed by one or more subsequent octets.

  8.1.2.4.1 The leading octet shall be encoded as follows:
    a) bits 8 and 7 shall be encoded to represent the class of the tag as listed in Table 1;
    b) bit 6 shall be a zero or a one according to the rules of 8.1.2.5;
    c) bits 5 to 1 shall be encoded as 11111.

`82 <http://www.emvlab.org/emvtags/show/t82/>`_ and `9F02 <http://www.emvlab.org/emvtags/show/t9f02>`_ are an example of how EMVCo failed.  9F02 decodes to (80 + 1F) with a tag number of (02); 82 decodes to (80) tagno (02).  That 1F is only supposed to be there **For tags with a number greater than or equal to 31**.  The EMV standard even refers to the ASN.1 spec correctly in Book 3 Annex B1.

  Table 36 defines the coding rules of the subsequent bytes of a BER-TLV tag when tag numbers ≥ 31 are used (that is, bits b5 - b1 of the first byte equal '11111').

The EMV standard claims to use BER-TLV encoding.  It does not.  How can we fix this?  Is it fixable?  What's the right approach?

I personally like to do things "The Right Way".  Doing so would require billions of cards to be replaced and many instances of software to be updated.  I just don't see that happening any time soon.

I've `asked <https://www.emvco.com/PublicComments.aspx>`_ EMVCo how 9F** tags (and the rest of the extended tags) follow the standard they claim to follow.  I'm not guaranteed a response without `subscribing for $2500 <https://www.emvco.com/about_emvco.aspx?id=161>`_.  We'll see if I get a response.
