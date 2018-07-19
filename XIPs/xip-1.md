---
xip: 1
title: XIP Purpose and Guidelines
status: Active
type: Meta
author: Unknown <unknown@xdag.io>, and others  
        https://github.com/XDAG/XIPs/blob/master/XIPS/xip-1.md
created: 2018-07-19
---

## What is an XIP?

XIP stands for XDAG Improvement Proposal. An XIP is a design document providing information to the xDagger community, or describing a new feature for XDAG or its processes or environment. The XIP should provide a concise technical specification of the feature and a rationale for the feature. The XIP author is responsible for building consensus within the community and documenting dissenting opinions.

## XIP Rationale

We intend XIPs to be the primary mechanisms for proposing new features, for collecting community input on an issue, and for documenting the design decisions that have gone into XDAG. Because the XIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal.

For XDAG implementers, XIPs are a convenient way to track the progress of their implementation. Ideally each implementation maintainer would list the XIPs that they have implemented. This will give end users a convenient way to know the current status of a given implementation or library.

## XIP Types

There are three types of XIP:

- A **Standard Track XIP** describes any change that affects most or all XDAG implementations, such as a change to the the network protocol, a change in block or transaction validity rules, proposed application standards/conventions, or any change or addition that affects the interoperability of applications using XDAG. Furthermore Standard XIPs can be broken down into the following categories. Standards Track XIPs consist of three parts, a design document, implementation, and finally if warranted an update to the [formal specification].
  - **Core** - improvements requiring a consensus fork, as well as changes that are not necessarily consensus critical but may be relevant to [“core dev” discussions](https://github.com/XDAG/management).
  - **Networking** - includes improvements around [devp2p] ([XIP8]) and [Light XDAG Subprotocol], as well as proposed improvements to network protocol specifications of [whisper] and [swarm].
  - **Interface** - includes improvements around client [API/RPC] specifications and standards, and also certain language-level standards like method names ([XIP59], [XIP6]) and [contract ABIs]. The label “interface” aligns with the [interfaces repo] and discussion should primarily occur in that repository before an XIP is submitted to the XIPs repository.
  - **ERC** - application-level standards and conventions, including contract standards such as token standards ([ERC20]), name registries ([ERC26], [ERC137]), URI schemes ([ERC67]), library/package formats ([XIP82]), and wallet formats ([XIP75], [XIP85]).
- An **Informational XIP** describes an XDAG design issue, or provides general guidelines or information to the XDAG community, but does not propose a new feature. Informational XIPs do not necessarily represent XDAG community consensus or a recommendation, so users and implementers are free to ignore Informational XIPs or follow their advice.
- A **Meta XIP** describes a process surrounding XDAG or proposes a change to (or an event in) a process. Process XIPs are like Standards Track XIPs but apply to areas other than the XDAG protocol itself. They may propose an implementation, but not to XDAG's codebase; they often require community consensus; unlike Informational XIPs, they are more than recommendations, and users are typically not free to ignore them. Examples include procedures, guidelines, changes to the decision-making process, and changes to the tools or environment used in XDAG development. Any meta-XIP is also considered a Process XIP.

It is highly recommended that a single XIP contain a single key proposal or new idea. The more focused the XIP, the more successful it tends to be. A change to one client doesn't require an XIP; a change that affects multiple clients, or defines a standard for multiple apps to use, does.

An XIP must meet certain minimum criteria. It must be a clear and complete description of the proposed enhancement. The enhancement must represent a net improvement. The proposed implementation, if applicable, must be solid and must not complicate the protocol unduly.

## XIP Work Flow

Parties involved in the process are you, the champion or *XIP author*, the [*XIP editors*](#xip-editors), and the [*XDAG Core Developers*](https://github.com/XDAG/management).

:warning: Before you begin, vet your idea, this will save you time. Ask the XDAG community first if an idea is original to avoid wasting time on something that will be be rejected based on prior research (searching the Internet does not always do the trick). It also helps to make sure the idea is applicable to the entire community and not just the author. Just because an idea sounds good to the author does not mean it will work for most people in most areas where XDAG is used. Examples of appropriate public forums to gauge interest around your XIP include [the XDAG subreddit], [the Issues section of this repository], and [one of the XDAG Gitter chat rooms]. In particular, [the Issues section of this repository] is an excellent place to discuss your proposal with the community and start creating more formalized language around your XIP.

Your role as the champion is to write the XIP using the style and format described below, shepherd the discussions in the appropriate forums, and build community consensus around the idea. Following is the process that a successful XIP will move along:

```
[ WIP ] -> [ DRAFT ] -> [ LAST CALL ] -> [ ACCEPTED ] -> [ FINAL ]
```

Each status change is requested by the XIP author and reviewed by the XIP editors. Use a pull request to update the status. Please include a link to where people should continue discussing your XIP. The XIP editors will process these requests as per the conditions below.

* **Work in progress (WIP)** -- Once the champion has asked the XDAG community whether an idea has any chance of support, they will write a draft XIP as a [pull request]. Consider including an implementation if this will aid people in studying the XIP.
  * :arrow_right: Draft -- If agreeable, XIP editor will assign the XIP a number (generally the issue or PR number related to the XIP) and merge your pull request. The XIP editor will not unreasonably deny an XIP.
  * :x: Draft -- Reasons for denying draft status include being too unfocused, too broad, duplication of effort, being technically unsound, not providing proper motivation or addressing backwards compatibility, or not in keeping with the [XDAG philosophy](https://github.com/XDAG/wiki/wiki/White-Paper#philosophy).
* **Draft** -- Once the first draft has been merged, you may submit follow-up pull requests with further changes to your draft until such point as you believe the XIP to be mature and ready to proceed to the next status. An XIP in draft status must be implemented to be considered for promotion to the next status (ignore this requirement for core XIPs).
  * :arrow_right: Last Call -- If agreeable, the XIP editor will assign Last Call status and set a review end date, normally 14 days later.
  * :x: Last Call -- A request for Last Call status will be denied if material changes are still expected to be made to the draft. We hope that XIPs only enter Last Call once, so as to avoid unnecessary noise on the RSS feed. Last Call will be denied if the implementation is not complete and supported by the community.
* **Last Call** -- This XIP will listed prominently on the http://xips.XDAG.org/ website (subscribe via RSS at [last-call.xml](/last-call.xml)).
  * :x: -- A Last Call which results in material changes or substantial unaddressed complaints will cause the XIP to revert to Draft.
  * :arrow_right: Accepted (Core XIPs only) -- After the review end date, the XDAG Core Developers will vote on whether to accept this change. If yes, the status will upgrade to Accepted.
  * :arrow_right: Final (Not core XIPs) -- A successful Last Call without material changes or unaddressed complaints will become Final.
* **Accepted (Core XIPs only)** -- This is being implemented by XDAG Core Developers.
  * :arrow_right: Final -- Standards Track Core XIPs must be implemented in at least three viable XDAG clients before it can be considered Final. When the implementation is complete and supported by the community, the status will be changed to “Final”.
* **Final** -- This XIP represents the current state-of-the-art. A Final XIP should only be updated to correct errata.

Other exceptional statuses include:

* Deferred -- This is for core XIPs that have been put off for a future hard fork.
* Rejected -- An XIP that is fundamentally broken and will not be implemented.
* Active -- This is similar to Final, but denotes an XIP which which may be updated without changing its XIP number.
* Superseded -- An XIP which was previously final but is no longer considered state-of-the-art. Another XIP will be in Final status and reference the Superseded XIP.

## What belongs in a successful XIP?

Each XIP should have the following parts:

- Preamble - RFC 822 style headers containing metadata about the XIP, including the XIP number, a short descriptive title (limited to a maximum of 44 characters), and the author details. See [below](https://github.com/XDAG/XIPs/blob/master/XIPS/xip-1.md#xip-header-preamble) for details.
- Simple Summary - “If you can’t explain it simply, you don’t understand it well enough.” Provide a simplified and layman-accessible explanation of the XIP.
- Abstract - a short (~200 word) description of the technical issue being addressed.
- Motivation (*optional) - The motivation is critical for XIPs that want to change the XDAG protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the XIP solves. XIP submissions without sufficient motivation may be rejected outright.
- Specification - The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current XDAG platforms (cpp-XDAG, go-XDAG, parity, XDAGJ, XDAGjs-lib, [and others](https://github.com/XDAG/wiki/wiki/Clients).
- Rationale - The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.
- Backwards Compatibility - All XIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The XIP must explain how the author proposes to deal with these incompatibilities. XIP submissions without a sufficient backwards compatibility treatise may be rejected outright.
- Test Cases - Test cases for an implementation are mandatory for XIPs that are affecting consensus changes. Other XIPs can choose to include links to test cases if applicable.
- Implementations - The implementations must be completed before any XIP is given status “Final”, but it need not be completed before the XIP is merged as draft. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of “rough consensus and running code” is still useful when it comes to resolving many discussions of API details.
- Copyright Waiver - All XIPs must be in the public domain. See the bottom of this XIP for an example copyright waiver.

## XIP Formats and Templates

XIPs should be written in [markdown] format.
Image files should be included in a subdirectory of the `assets` folder for that XIP as follow: `assets/xip-X` (for xip **X**). When linking to an image in the XIP, use relative links such as `../assets/xip-X/image.png`.

## XIP Header Preamble

Each XIP must begin with an RFC 822 style header preamble, preceded and followed by three hyphens (`---`). The headers must appear in the following order. Headers marked with "*" are optional and are described below. All other headers are required.

` xip:` <XIP number> (this is determined by the XIP editor)

` title:` <XIP title>

` author:` <a list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below.>

` * discussions-to:` <url>

` status:` <Draft | Last Call | Accepted | Final | Active | Deferred | Rejected | Superseded>

`* review-period-end: YYYY-MM-DD

` type: `<Standards Track (Core, Networking, Interface, ERC)  | Informational | Meta>

` * category:` <Core | Networking | Interface | ERC>

` created:` <date created on, in ISO 8601 (yyyy-mm-dd) format>

` * requires:` <XIP number(s)>

` * replaces:` <XIP number(s)>

` * superseded-by:` <XIP number(s)>

` * resolution:` <url>

#### Author header

The author header optionally lists the names, email addresses or usernames of the authors/owners of the XIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

Random J. User &lt;address@dom.ain&gt;

or

Random J. User (@username)

if the email address or GitHub username is included, and

Random J. User

if the email address is not given.

Note: The resolution header is required for Standards Track XIPs only. It contains a URL that should point to an email message or other web resource where the pronouncement about the XIP is made.

The type header specifies the type of XIP: Standards Track, Meta, or Informational. If the track is Standards please include the subcategory (core, networking, interface, or ERC).

The category header specifies the XIP's category. This is required for standards-track XIPs only.

The created header records the date that the XIP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

XIPs may have a requires header, indicating the XIP numbers that this XIP depends on.

XIPs may also have a superseded-by header indicating that an XIP has been rendered obsolete by a later document; the value is the number of the XIP that replaces the current document. The newer XIP must have a Replaces header containing the number of the XIP that it rendered obsolete.

Headers that permit lists must separate elements with commas.

## Auxiliary Files

XIPs may include auxiliary files such as diagrams. Such files must be named XIP-XXXX-Y.ext, where “XXXX” is the XIP number, “Y” is a serial number (starting at 1), and “ext” is replaced by the actual file extension (e.g. “png”).

## Transferring XIP Ownership

It occasionally becomes necessary to transfer ownership of XIPs to a new champion. In general, we'd like to retain the original author as a co-author of the transferred XIP, but that's really up to the original author. A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the XIP process, or has fallen off the face of the 'net (i.e. is unreachable or isn't responding to email). A bad reason to transfer ownership is because you don't agree with the direction of the XIP. We try to build consensus around an XIP, but if that's not possible, you can always submit a competing XIP.

If you are interested in assuming ownership of an XIP, send a message asking to take over, addressed to both the original author and the XIP editor. If the original author doesn't respond to email in a timely manner, the XIP editor will make a unilateral decision (it's not like such decisions can't be reversed :)).

## XIP Editors

The current XIP editors are

` * Evgeniy (@jonano614)`

` * Frozen (@xrdavies)`


## XIP Editor Responsibilities

For each new XIP that comes in, an editor does the following:

- Read the XIP to check if it is ready: sound and complete. The ideas must make technical sense, even if they don't seem likely to get to final status.
- The title should accurately describe the content.
- Check the XIP for language (spelling, grammar, sentence structure, etc.), markup (Github flavored Markdown), code style

If the XIP isn't ready, the editor will send it back to the author for revision, with specific instructions.

Once the XIP is ready for the repository, the XIP editor will:

- Assign an XIP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this XIP)

- Merge the corresponding pull request

- Send a message back to the XIP author with the next step.

Many XIPs are written and maintained by developers with write access to the XDAG codebase. The XIP editors monitor XIP changes, and correct any structure, grammar, spelling, or markup mistakes we see.

The editors don't pass judgment on XIPs. We merely do the administrative & editorial part.

## History

This document was derived heavily from [Bitcoin's BIP-0001] written by Amir Taaki which in turn was derived from [Python's PEP-0001]. In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use in the XDAG Improvement Process, and should not be bothered with technical questions specific to XDAG or the XIP. Please direct all comments to the XIP editors.

See [the revision history for further details](https://github.com/xdagger/XIPs/commits/master/XIPS/xip-1.md), which is also available by clicking on the History button in the top right of the XIP.

### Bibliography   
[API/RPC](https://github.com/XDagger/xdag/wiki/JSON-RPC-API)  
[pull request](https://github.com/xdagger/XIPs/pulls)  
[the Issues section of this repository](https://github.com/xdagger/XIPs/issues)  
[markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)  
[Bitcoin's BIP-0001](https://github.com/bitcoin/bips)  
[Python's PEP-0001](https://www.python.org/dev/peps/)  

## Copyright

Copyright and related rights are discribed in [MIT license](LICENSE).