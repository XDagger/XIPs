# XIPs 
XDAG Improvement Proposals (XIPs) describe standards for the XDAG platform, including core protocol specifications, client APIs, and contract standards.

A browsable version of all current and draft XIPs can be found on [the official XIP site](http://xdag.io/xips).

# Contributing

 1. Review [XIP-1](XIPS/xip-1.md).
 2. Fork the repository by clicking "Fork" in the top right.
 3. Add your XIP to your fork of the repository. There is a [template XIP here](xip-X.md).
 4. Submit a Pull Request to XDAG's [XIPs repository](https://github.com/xdagger/XIPs).

Your first PR should be a first draft of the final XIP. It must meet the formatting criteria enforced by the build (largely, correct metadata in the header). An editor will manually review the first PR for a new XIP and assign it a number before merging it. Make sure you include a `discussions-to` header with the URL to a discussion forum or open GitHub issue where people can discuss the XIP as a whole.

If your XIP requires images, the image files should be included in a subdirectory of the `assets` folder for that XIP as follow: `assets/xip-X` (for xip **X**). When linking to an image in the XIP, use relative links such as `../assets/xip-X/image.png`.

Once your first PR is merged, we have a bot that helps out by automatically merging PRs to draft XIPs. For this to work, it has to be able to tell that you own the draft being edited. Make sure that the 'author' line of your XIP contains either your Github username or your email address inside <triangular brackets>. If you use your email address, that address must be the one publicly shown on [your GitHub profile](https://github.com/settings/profile).

When you believe your XIP is mature and ready to progress past the draft phase, you should do one of two things:

 - **For a Standards Track XIP of type Core**, ask to have your issue added to [the agenda of an upcoming All Core Devs meeting](https://github.com/XDagger/management/issues), where it can be discussed for inclusion in a future hard fork. If implementers agree to include it, the XIP editors will update the state of your XIP to 'Accepted'.
 - **For all other XIPs**, open a PR changing the state of your XIP to 'Final'. An editor will review your draft and ask if anyone objects to its being finalised. If the editor decides there is no rough consensus - for instance, because contributors point out significant issues with the XIP - they may close the PR and request that you fix the issues in the draft before trying again.

# XIP Status Terms
* **Draft** - an XIP that is open for consideration.
* **Accepted** - an XIP that is planned for immediate adoption, i.e. expected to be included in the next hard fork (for Core/Consensus layer XIPs).
* **Final** - an XIP that has been adopted in a previous hard fork (for Core/Consensus layer XIPs).
* **Deferred** - an XIP that is not being considered for immediate adoption. May be reconsidered in the future for a subsequent hard fork.

# Preferred Citation Format

The canonical URL for a XIP that has achieved draft status at any point is at https://xdag.io/xips/.