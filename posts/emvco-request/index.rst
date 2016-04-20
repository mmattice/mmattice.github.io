.. title: EMVCo Request
.. slug: emvco-request
.. date: 2016-04-14 04:01:08 UTC
.. tags: ASN.1,EMV,specifications,ISO-8825,X.690,tech
.. category: Commentary
.. link: 
.. description: 
.. type: text

I sent the following to EMVCo via https://www.emvco.com/PublicComments.aspx on March 28th at about 0200UTC.

  Table 35 & 36 refer to ISO/IEC 8825 which is also ITU-T Rec. X.690.  The X.690 spec available at https://www.itu.int/ITU-T/studygroups/com17/languages/X.690-0207.pdf 

  Specifically, the document states "According to ISO/IEC 8825, Table 36 defines the coding rules of the subsequent bytes of a BER-TLV tag when tag numbers ≥ 31 are used (that is, bits b5 - b1 of the first byte equal '11111')."

  Please explain how 9F02 follows this?  The tag number for 9F02 is 2, which is clearly < 31.  

  IEC/ISO 8255 states:
    8.1.2.2 For tags with a number ranging from zero to 30 (inclusive), the identifier octets shall comprise a single octet encoded as follows:
    a) bits 8 and 7 shall be encoded to represent the class of the tag as specified in Table 1;
    b) bit 6 shall be a zero or a one according to the rules of 8.1.2.5;
    c) bits 5 to 1 shall encode the number of the tag as a binary integer with bit 5 as the most significant bit.

  That essentially tells me that every EMV tag that's two bytes with the second byte less than 31 is invalid and not capable of being encoded by BER.

  I look forward to your response.

I figure two weeks is plenty of time for them to respond to this simple inquiry.  Unfortunately, I got the only the following in response:

  \*\*\*\*\*Please do not reply to this email\*\*\*\*\*

  Dear Mike Mattice,

  Thank you for submitting your comment to EMVCo. EMVCo has received your comment and will review and respond as deemed necessary.

  Please note that EMVCo does not guarantee a response to public comments. EMVCo has implemented a new subscriber program through its website in order to facilitate dialog and interaction between EMVCo and its subscriber community. For more details, please find the service description in the EMVCo website "Contact Us" section.

  For your reference, a copy of your comment is included below.

  Thank you.

  The EMVCo Communication Secretariat
  Message ID:1001

  `-------------------`

  Comment ID: 12005

  `-------------------`

Perhaps I should start a gofundme to become an EMVCo subscriber so I can get a guaranteed answer.

In other news I sent this to customerservice@iso.org:

  Are there repercussions for claiming to follow ISO standards (like 8825) but not actually doing so?

  Thanks,
  Mike

A couple days later I got:

  ISO standards are voluntary, and as such, ISO does not carry out any assessment of conformity, nor does it monitor the implementation of its standards.

  A number of ISO standards - mainly those concerned with health, safety or the environment - have been adopted in some countries as part of their regulatory framework, or are referred to in legislation for which they serve as the technical basis. However, such adoptions are decisions by the regulatory authorities or governments of the countries concerned. ISO itself does not regulate or legislate.

  Cordially,

  joseph martinez

  Information Expert | marketing and sales services | marketing, communication & information | iso central secretariat | phone: +41 22 749 03 17

So, no repercussions for saying you follow ISO-8825, but not actually doing so.
