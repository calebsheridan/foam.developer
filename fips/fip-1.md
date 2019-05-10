---
FIP: 1
title: FIP Purpose and Guidelines
status: draft
type: Meta
author: open_positions :)
        https://github.com/f-o-a-m/foam.developer/fips/fip-1.md
created: 2019-05-09
---

## What is an FIP?

FIP stands for FOAM Improvement Proposal. A FIP is a design document providing information to the FOAM community, or describing a new feature for FOAM or its processes or environment. The FIP should provide a concise technical specification of the feature and a rationale for the feature. The FIP author is responsible for building consensus within the community and documenting dissenting opinions.

## FIP Rationale

We intend FIPs to be the primary mechanisms for proposing new features, for collecting community technical input on an issue, and for documenting the design decisions that have gone into FOAM. Because the FIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal.

For FOAM implementers, FIPs are a convenient way to track the progress of their implementation. Ideally each implementation maintainer would list the FIPs that they have implemented. This will give end users a convenient way to know the current status of a given implementation or library.

## FIP Types

There are three types of FIP:

- A **Standard Track FIP** describes any change that affects most or all FOAM implementations, such as a change to the the network protocol, a change in block or transaction validity rules, proposed application standards/conventions, or any change or addition that affects the interoperability of applications using FOAM. Furthermore Standard FIPs can be broken down into the following categories. Standards Track FIPs consist of three parts, a design document, implementation, and finally if warranted an update to the [formal specification].
  - **Core** - improvements requiring a consensus fork (e.g. reference future FIPs here), as well as changes that are not necessarily consensus critical but may be relevant to [“core dev” discussions](https://gitter.im/f-o-a-m).
  - **Networking** - includes improvements as well as proposed improvements to network protocol specifications.
  - **Interface** - includes improvements around client [API/RPC] specifications and standards, and also certain language-level standards like method names and [contract ABIs]. The label “interface” aligns with the [interfaces repo] and discussion should primarily occur in that repository before an FIP is submitted to the FIPs repository.
- An **Informational FIP** describes a FOAM design issue, or provides general guidelines or information to the FOAM community, but does not propose a new feature. Informational FIPs do not necessarily represent FOAM community consensus or a recommendation, so users and implementers are free to ignore Informational FIPs or follow their advice.
- A **Meta FIP** describes a process surrounding FOAM or proposes a change to (or an event in) a process. Process FIPs are like Standards Track FIPs but apply to areas other than the FOAM protocol itself. They may propose an implementation, but not to FOAM's codebase; they often require community consensus; unlike Informational FIPs, they are more than recommendations, and users are typically not free to ignore them. Examples include procedures, guidelines, changes to the decision-making process, and changes to the tools or environment used in FOAM development. Any meta-FIP is also considered a Process FIP.

It is highly recommended that a single FIP contain a single key proposal or new idea. The more focused the FIP, the more successful it tends to be. A change to one client doesn't require an FIP; a change that affects multiple clients, or defines a standard for multiple apps to use, does.

A FIP must meet certain minimum criteria. It must be a clear and complete description of the proposed enhancement. The enhancement must represent a net improvement. The proposed implementation, if applicable, must be solid and must not complicate the protocol unduly.

## FIP Work Flow

Parties involved in the process are you, the champion or *FIP author*, the [*FIP editors*](#FIP-editors), and the [*FOAM Core Developers*](fix link).

:warning: Before you begin, vet your idea, this will save you time. Ask the FOAM community first if an idea is original to avoid wasting time on something that will be be rejected based on prior research (searching the Internet does not always do the trick). It also helps to make sure the idea is applicable to the entire community and not just the author. Just because an idea sounds good to the author does not mean it will work for most people in most areas where FOAM is used. Examples of appropriate public forums to gauge interest around your FIP include [FOAM Discourse](https://discourse.foam.space/), [the Issues section of this repository], and [one of the FOAM Gitter chat rooms](https://gitter.im/f-o-a-m). In particular, [the Issues section of this repository] is an excellent place to discuss your proposal with the community and start creating more formalized language around your FIP.

Your role as the champion is to write the FIP using the style and format described below, shepherd the discussions in the appropriate forums, and build community consensus around the idea. Following is the process that a successful FIP will move along:

```
[ WIP ] -> [ DRAFT ] -> [ LAST CALL ] -> [ ACCEPTED ] -> [ FINAL ]
```

Each status change is requested by the FIP author and reviewed by the FIP editors. Use a pull request to update the status. Please include a link to where people should continue discussing your FIP. The FIP editors will process these requests as per the conditions below.

* **Active** -- Some Informational and Process FIPs may also have a status of “Active” if they are never meant to be completed. E.g. FIP 1 (this FIP).
* **Work in progress (WIP)** -- Once the champion has asked the FOAM community whether an idea has any chance of support, they will write a draft FIP as a [pull request]. Consider including an implementation if this will aid people in studying the FIP.
  * :arrow_right: Draft -- If agreeable, FIP editor will assign the FIP a number (generally the issue or PR number related to the FIP) and merge your pull request. The FIP editor will not unreasonably deny an FIP.
  * :x: Draft -- Reasons for denying draft status include being too unfocused, too broad, duplication of effort, being technically unsound, not providing proper motivation or addressing backwards compatibility, or not in keeping with the [FOAM philosophy](link to Whitepaper ??? ).
* **Draft** -- Once the first draft has been merged, you may submit follow-up pull requests with further changes to your draft until such point as you believe the FIP to be mature and ready to proceed to the next status. An FIP in draft status must be implemented to be considered for promotion to the next status (ignore this requirement for core FIPs).
  * :arrow_right: Last Call -- If agreeable, the FIP editor will assign Last Call status and set a review end date (`review-period-end`), normally 14 days later.
  * :x: Last Call -- A request for Last Call status will be denied if material changes are still expected to be made to the draft. We hope that FIPs only enter Last Call once, so as to avoid unnecessary noise on the RSS feed.
* **Last Call** -- This FIP will listed prominently on the https://fips.foam.space/ website (subscribe via RSS at [last-call.xml](/last-call.xml)).
  * :x: -- A Last Call which results in material changes or substantial unaddressed technical complaints will cause the FIP to revert to Draft.
  * :arrow_right: Accepted (Core FIPs only) -- A successful Last Call without material changes or unaddressed technical complaints will become Accepted.
  * :arrow_right: Final (Not core FIPs) -- A successful Last Call without material changes or unaddressed technical complaints will become Final.
* **Accepted (Core FIPs only)** -- This FIP is in the hands of the FOAM client developers.  Their process for deciding whether to encode it into their clients as part of a hard fork is not part of the FIP process.
  * :arrow_right: Final -- Standards Track Core FIPs must be implemented in at least three viable FOAM clients before it can be considered Final. When the implementation is complete and adopted by the community, the status will be changed to “Final”.
* **Final** -- This FIP represents the current state-of-the-art. A Final FIP should only be updated to correct errata.

Other exceptional statuses include:

* **Deferred** -- This is for core FIPs that have been put off for a future hard fork.
* **Rejected** -- An FIP that is fundamentally broken or a Core FIP that was rejected by the Core Devs and will not be implemented.
* **Active** -- This is similar to Final, but denotes an FIP which may be updated without changing its FIP number.
* **Superseded** -- An FIP which was previously final but is no longer considered state-of-the-art. Another FIP will be in Final status and reference the Superseded FIP.

## What belongs in a successful FIP?

Each FIP should have the following parts:

- Preamble - RFC 822 style headers containing metadata about the FIP, including the FIP number, a short descriptive title (limited to a maximum of 44 characters), and the author details. See [below](#FIP-header-preamble) for details.
- Simple Summary - “If you can’t explain it simply, you don’t understand it well enough.” Provide a simplified and layman-accessible explanation of the FIP.
- Abstract - a short (~200 word) description of the technical issue being addressed.
- Motivation (*optional) - The motivation is critical for FIPs that want to change the FOAM protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the FIP solves. FIP submissions without sufficient motivation may be rejected outright.
- Specification - The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current FOAM platforms (list FOAM implementations here, [and others](link to FOAM Clients...).
- Rationale - The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.
- Backwards Compatibility - All FIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The FIP must explain how the author proposes to deal with these incompatibilities. FIP submissions without a sufficient backwards compatibility treatise may be rejected outright.
- Test Cases - Test cases for an implementation are mandatory for FIPs that are affecting consensus changes. Other FIPs can choose to include links to test cases if applicable.
- Implementations - The implementations must be completed before any FIP is given status “Final”, but it need not be completed before the FIP is merged as draft. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of “rough consensus and running code” is still useful when it comes to resolving many discussions of API details.
- Copyright Waiver - All FIPs must be in the public domain. See the bottom of this FIP for an example copyright waiver.

## FIP Formats and Templates

FIPs should be written in [markdown] format.
Image files should be included in a subdirectory of the `assets` folder for that FIP as follow: `assets/FIP-X` (for FIP **X**). When linking to an image in the FIP, use relative links such as `../assets/FIP-X/image.png`. It is preferable that diagrams be generated as ascii such as [svgbob](https://github.com/ivanceras/svgbob). This allows git versioning and collaboration with a renderable high-resolution image.


## FIP Header Preamble

Each FIP must begin with an RFC 822 style header preamble, preceded and followed by three hyphens (`---`). The headers must appear in the following order. Headers marked with "*" are optional and are described below. All other headers are required.

` FIP:` <FIP number> (this is determined by the FIP editor)

` title:` <FIP title>

` author:` <a list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below.>

` * discussions-to:` \<a url pointing to the official discussion thread\>

` status:` <Draft | Last Call | Accepted | Final | Active | Deferred | Rejected | Superseded>

`* review-period-end:` <date review period ends>

` type:` <Standards Track (Core, Networking, Interface, ERC)  | Informational | Meta>

` * category:` <Core | Networking | Interface | ERC>

` created:` <date created on>

` * updated:` <comma separated list of dates>

` * requires:` <FIP number(s)>

` * replaces:` <FIP number(s)>

` * superseded-by:` <FIP number(s)>

` * resolution:` \<a url pointing to the resolution of this FIP\>

Headers that permit lists must separate elements with commas.

Headers requiring dates will always do so in the format of ISO 8601 (yyyy-mm-dd).

#### `author` header

The `author` header optionally lists the names, email addresses or usernames of the authors/owners of the FIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

> Random J. User &lt;address@dom.ain&gt;

or

> Random J. User (@username)

if the email address or GitHub username is included, and

> Random J. User

if the email address is not given.

#### `resolution` header

The `resolution` header is required for Standards Track FIPs only. It contains a URL that should point to an email message or other web resource where the pronouncement about the FIP is made.

#### `discussions-to` header

While an FIP is a draft, a `discussions-to` header will indicate the mailing list or URL where the FIP is being discussed. As mentioned above, examples for places to discuss your FIP include [FOAM topics on Gitter](https://gitter.im/FOAM/), an issue in this repo or in a fork of this repo.

No `discussions-to` header is necessary if the FIP is being discussed privately with the author.

As a single exception, `discussions-to` cannot point to GitHub pull requests.

#### `type` header

The `type` header specifies the type of FIP: Standards Track, Meta, or Informational. If the track is Standards please include the subcategory (core, networking, interface, or ERC).

#### `category` header

The `category` header specifies the FIP's category. This is required for standards-track FIPs only.

#### `created` header

The `created` header records the date that the FIP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

#### `updated` header

The `updated` header records the date(s) when the FIP was updated with "substantional" changes. This header is only valid for FIPs of Draft and Active status.

#### `requires` header

FIPs may have a `requires` header, indicating the FIP numbers that this FIP depends on.

#### `superseded-by` and `replaces` headers

FIPs may also have a `superseded-by` header indicating that an FIP has been rendered obsolete by a later document; the value is the number of the FIP that replaces the current document. The newer FIP must have a `replaces` header containing the number of the FIP that it rendered obsolete.

## Auxiliary Files

FIPs may include auxiliary files such as diagrams. Such files must be named FIP-XXXX-Y.ext, where “XXXX” is the FIP number, “Y” is a serial number (starting at 1), and “ext” is replaced by the actual file extension (e.g. “png”). It is preferable that diagrams be generated as ascii such as [svgbob](https://github.com/ivanceras/svgbob). This allows git versioning and collaboration.

## Transferring FIP Ownership

It occasionally becomes necessary to transfer ownership of FIPs to a new champion. In general, we'd like to retain the original author as a co-author of the transferred FIP, but that's really up to the original author. A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the FIP process, or has fallen off the face of the 'net (i.e. is unreachable or isn't responding to email). A bad reason to transfer ownership is because you don't agree with the direction of the FIP. We try to build consensus around an FIP, but if that's not possible, you can always submit a competing FIP.

If you are interested in assuming ownership of an FIP, send a message asking to take over, addressed to both the original author and the FIP editor. If the original author doesn't respond to email in a timely manner, the FIP editor will make a unilateral decision (it's not like such decisions can't be reversed :)).

## FIP Editors

The current FIP editors are

` * John Smith (@twitter_address_here)`

## FIP Editor Responsibilities

For each new FIP that comes in, an editor does the following:

- Read the FIP to check if it is ready: sound and complete. The ideas must make technical sense, even if they don't seem likely to get to final status.
- The title should accurately describe the content.
- Check the FIP for language (spelling, grammar, sentence structure, etc.), markup (Github flavored Markdown), code style

If the FIP isn't ready, the editor will send it back to the author for revision, with specific instructions.

Once the FIP is ready for the repository, the FIP editor will:

- Assign an FIP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this FIP)

- Merge the corresponding pull request

- Send a message back to the FIP author with the next step.

Many FIPs are written and maintained by developers with write access to the FOAM codebase. The FIP editors monitor FIP changes, and correct any structure, grammar, spelling, or markup mistakes we see.

The editors don't pass judgment on FIPs. We merely do the administrative & editorial part.

## History

This document was derived heavily from [EIP](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1.md), and [Bitcoin's BIP-0001] written by Amir Taaki which in turn was derived from [Python's PEP-0001]. In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use in the FOAM Improvement Process, and should not be bothered with technical questions specific to FOAM or the FIP. Please direct all comments to the FIP editors.

Enter history here...

See [the revision history for further details](https://github.com/f-o-a-m/foam.developer/master/FIPS/FIP-1.md), which is also available by clicking on the History button in the top right of the FIP.

### Bibliography

[one of the FOAM Gitter chat rooms]: https://gitter.im/FOAM/
[pull request]: https://github.com/f-o-a-m/foam.developer/pulls
[formal specification]: linked needed to technical whitepaper?
[the Issues section of this repository]: https://github.com/f-o-a-m/foam.developer/FIPs/issues
[markdown]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet


## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
