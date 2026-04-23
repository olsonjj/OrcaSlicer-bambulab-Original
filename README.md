# Repository Notice

This repository no longer contains the previously published implementation.

The code, releases, tags, and related materials were removed in full, and this solution will not be distributed further.

I made that decision after direct contact from Bambu Lab regarding the removed network integration path.

I asked whether I could publish the private correspondence in full for transparency. That request was refused. Because of that, I am not publishing the conversation itself here. What follows is my own summary of the situation and my own position.

## What happened

Bambu Lab contacted me directly and demanded removal of the solution.

In that correspondence, they alleged, among other things, that the removed implementation:

- impersonated Bambu Studio,
- bypassed their authorization controls,
- violated their Terms of Use,
- involved "reverse engineering",
- and could allow modified forks to send arbitrary commands to printers.

They also referred to legal materials and stated that a cease and desist letter had been prepared.

I do not accept those allegations as established facts.

## What I asked them to clarify

I asked Bambu Lab to identify, precisely and concretely:

- the exact repository files, commits, or code paths they considered problematic,
- the exact legal or contractual basis they were relying on,
- and the exact Terms / EULA basis if their objection was primarily about service access rather than copyright.

I also made clear that the repository did not contain or redistribute their proprietary networking plugin binaries.

I did not receive the precise technical and legal clarification I had asked for. Instead, after I disputed their characterization and asked for specifics, I received further broad accusations, including repeated references to "reverse engineering".

## Important technical clarifications

The removed repository did not redistribute Bambu Lab's proprietary networking plugin binaries.

My work was based on publicly available Bambu Studio source code together with my own integration layer.

That distinction is important.

Bambu Studio is publicly released under the AGPL-3.0 license, and Bambu Lab's own public repository describes the networking plugin as an optional component based on non-free libraries. Bambu Lab also publicly announced a newer authorization-control model for critical printer operations and publicly presented Bambu Connect as their intended path for third-party workflows under that updated model.

## Why I disputed their characterization

One of the more serious allegations made to me was the suggestion that this implementation could allow unauthorized commands to be sent to printers.

I explicitly pointed out that, according to Bambu Lab's own explanation, the reason the method still worked was simply that they had not disabled that path yet. In other words, the behavior they objected to was, by their own description, still possible within the Linux-side workflow they had not yet changed.

For that reason, I did not accept the attempt to frame this as though I had created some entirely separate hidden capability or some novel printer-side command path.

I also did not accept the repeated suggestion that this should simply be described as "reverse engineering" in the way it was presented to me, especially since I had already explained that the work was based on public Bambu Studio source code and that I had not used or redistributed their proprietary plugin binaries.

I asked them to explain why they continued to frame it that way after this had been pointed out. I did not receive a substantive answer to that question.

## Why the repository was removed anyway

I removed the repository voluntarily.

That removal should not be interpreted as an admission that all legal or technical allegations made against the project were correct.

I removed it because I have no interest in maintaining a prolonged dispute around this particular implementation, and no interest in continuing to distribute it.

## Transparency note

Bambu Lab refused consent for publication of the private correspondence itself.

I therefore am not reproducing the full exchange here.

However, I retain the full correspondence. If any further dispute arises, I reserve all rights regarding the preservation, use, and disclosure of relevant records to the extent permitted by applicable law.

## Current status

This repository remains only as a historical notice explaining why the original contents disappeared.

No code, releases, or technical materials for the removed solution are distributed here anymore.
