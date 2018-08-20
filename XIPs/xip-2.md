---
xip:  4
title: XDAG URI Scheme
author: solar <feiin@qq.com>
discussions-to: 
status: Draft
type: Interface
created: 2018-08-20
---


## Simple Summary

XDAG payment schema proposal 

## Abstract

This XIP proposes a URI scheme for making XDAG payments.

## Motivation

The purpose of this URI scheme is to enable users to easily make payments by simply clicking links on webpages or scanning QR Codes.


## Specification

### General rules for handling

XDAG clients MUST NOT act on URIs without getting the user's authorization. They SHOULD require the user to manually approve each payment individually, though in some cases they MAY allow the user to automatically make this decision.

### Operating system integration

Graphical XDAG clients SHOULD register themselves as the handler for the "xdag:" URI scheme by default, if no other handler is already registered. If there is already a registered handler, they MAY prompt the user to change it once when they first run the client.

### General Format

XDAG URIs follow the general format for URIs as set forth in RFC 3986. The path component consists of a xdag address, and the query component provides additional payment options.

Elements of the query component may contain characters outside the valid range. These must first be encoded according to UTF-8, and then each octet of the corresponding UTF-8 sequence must be percent-encoded as described in RFC 3986.

### grammar

```
 xdagurn     = "xdag:" xdagaddress [ "?" xdagparams ]
 xdagaddress = *base64
 xdagparams  = xdagparam [ "&" xdagparams ]
 xdagparam   = [ amountparam / labelparam / messageparam / otherparam / reqparam ]
 amountparam    = "amount=" *digit [ "." *digit ]
 abelparam     = "label=" *qchar
 messageparam   = "message=" *qchar
 otherparam     = qchar *qchar [ "=" *qchar ]
 reqparam       = "req-" qchar *qchar [ "=" *qchar ]

```

Here, "qchar" corresponds to valid characters of an RFC 3986 URI query component, excluding the "=" and "&" characters, which this XIP takes as separators.

The scheme component ("xdag:") is case-insensitive, and implementations must accept any combination of uppercase and lowercase letters. The rest of the URI is case-sensitive, including the query parameter keys.

#### Query Keys

- label: Label for that address (e.g. name of receiver)
- address: xdag address
- message: message that describes the transaction to the user (see examples below)
- size: amount of base xdag units (see below)
(others): optional, for future extensions

## Rationale

### Payment identifiers, not person identifiers

Current best practices are that a unique address should be used for every transaction. Therefore, a URI scheme should not represent an exchange of personal information, but a one-time payment.


### Accessibility (URI scheme name)

Should someone from the outside happen to see such a URI, the URI scheme name already gives a description. A quick search should then do the rest to help them find the resources needed to make their payment. Other proposed names sound much more cryptic; the chance that someone googles that out of curiosity are much slimmer. Also, very likely, what he will find are mostly technical specifications - not the best introduction to xdag.

## Forward compatibility

Variables which are prefixed with a req- are considered required. If a client does not implement any variables which are prefixed with req-, it MUST consider the entire URI invalid. Any other variables which are not implemented, but which are not prefixed with a req-, can be safely ignored.




## Backwards Compatibility

As this XIP is written, several clients already implement a xdag: URI scheme similar to this one, however usually without the additional "req-" prefix requirement. Thus, it is recommended that additional variables prefixed with req- not be used in a mission-critical way until a grace period of 6 months from the finalization of this XIP has passed in order to allow client developers to release new versions, and users of old clients to upgrade.

## Appendix

### Simpler syntax

This section is non-normative and does not cover all possible syntax. Please see the grammar above for the normative syntax.

[foo] means optional, <bar> are placeholders

```
 xdag:<address>[?amount=<amount>][?label=<label>][?message=<message>]
```


### Examples

Just the address:

```
  xdag:4f1Sp/UD55JX5+kQCevUCpyenaPwqmpC

```
Address with name:

```
 xdag:4f1Sp/UD55JX5+kQCevUCpyenaPwqmpC?label=Solar
```
Request 10.5 XDAG to "Solar":

```
 xdag:4f1Sp/UD55JX5+kQCevUCpyenaPwqmpC?amount=10.5&label=Solar
```
Request 50 XDAG with message:

```
 xdag:4f1Sp/UD55JX5+kQCevUCpyenaPwqmpC?amount=50&label=Solar&message=Donation%20for%20project%20xyz
```

Some future version that has variables which are (currently) not understood and required and thus invalid:

```
 xdag:4f1Sp/UD55JX5+kQCevUCpyenaPwqmpC?req-somethingyoudontunderstand=50&req-somethingelseyoudontget=999
```
Some future version that has variables which are (currently) not understood but not required and thus valid:

```
 xdag:4f1Sp/UD55JX5+kQCevUCpyenaPwqmpC?somethingyoudontunderstand=50&somethingelseyoudontget=999
```
Characters must be URI encoded properly.


## Test Cases



## Implementation

### XDAG clients

- [xdag-ios](https://github.com/XDagger/xdag-ios) supports the xdag URIs 

### Libraries


## Copyright
Copyright and related rights are discribed in [MIT license](LICENSE).
