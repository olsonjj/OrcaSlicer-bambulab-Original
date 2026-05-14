<h2 align="center">Thank you for the support</h2>

<p align="center">
  Thank you everyone for the support - especially those who supported the project through Ko-fi and Revolut.
</p>

<p align="center">
  A lot is happening right now, and I am not always able to reply to everyone individually, but I truly appreciate everything you are doing.
</p>

<p align="center">
  This gave open-source development a huge push. I am already working on BMCU for Klipper, and I also have plans for new open MMU solutions.
</p>

<p align="center">
  Thank you again - this really helps push open-source projects forward.
</p>

<p align="center">
  The AGPL license violation issue is still ongoing, as is the issue of limiting the functionality of already purchased printers through updates that introduce device authorization and force the use of Bambu Lab hardware only.
</p>

## Update 09.05.2026

Bambu Lab published a statement on their blog. That statement does not give me any direct way to answer the accusations in the same place.

In that statement, Bambu Lab described the modification as something that:

- injected "falsified identity metadata",
- "pretended to be the official Bambu Studio client",
- "crosses into impersonation",
- was "bypassing a technical limitation",
- could create infrastructure problems comparable to service overload caused by unauthorized traffic.

These are very serious public accusations.

Bambu Lab did not write to me with these specific public claims first. They also refused my request to publish the full correspondence. Instead, they published a one-sided public statement where I cannot reply directly.

In practice, this presents me to the public as someone bypassing security, impersonating their client, and creating a risk to their infrastructure. I reject that characterization.

Below is the code fragment Bambu Lab referred to:

![Code referenced by Bambu Lab](./code.jpg)

User-Agent is not authentication. It is only self-declared client metadata. Any program can set any User-Agent.

The most important part is this: the User-Agent construction comes directly from Bambu Lab's own public AGPL Bambu Studio code.

Bambu Studio AGPL code:

https://github.com/bambulab/BambuStudio/blob/master/src/slic3r/Utils/Http.cpp#L175

```cpp
::curl_easy_setopt(curl, CURLOPT_USERAGENT, SLIC3R_APP_NAME "/" SLIC3R_VERSION);
```

The constants are defined here:

https://github.com/bambulab/BambuStudio/blob/master/version.inc

```cmake
set(SLIC3R_APP_NAME "BambuStudio")
set(SLIC3R_VERSION "02.06.01.55")
```

After compilation, this is logically equivalent to:

```cpp
CURLOPT_USERAGENT = "BambuStudio/02.06.01.55";
```

So what exactly is the problem here?

This User-Agent construction is not reverse engineered. It is not taken from a proprietary binary. It is not hidden. It is directly present in Bambu Studio's public AGPL source code.

So on what basis can anyone claim that I am not allowed to use this specific part of AGPL-licensed code under the AGPL license?

Bambu Studio on Linux can be used as-is, without any changes from me, and this code path already exists there.

If Bambu Lab separates its optional network plugin from the AGPL code by saying that the plugin is optional and not part of the AGPL source, because otherwise they would have an AGPL problem themselves, then they cannot also claim that my fork, based only on AGPL Bambu Studio code, suddenly becomes responsible for that optional plugin or violates the ToS because that plugin exists.

The user decides whether to install and use the optional plugin. My fork cannot be responsible for how an external optional plugin behaves or for what a user chooses to do through it.

That responsibility belongs to the plugin, the user, and the system it connects to - not to an AGPL fork of Bambu Studio.

I also want to add one personal note. I previously helped Bambu Studio users with Linux and Wayland issues, including on Bambu Lab's own GitHub. That makes it especially absurd to me that I am now being publicly presented as someone dangerous to their infrastructure.

These claims are now being repeated publicly. Since I cannot reply under Bambu Lab's blog post, I am publishing this response here.


<h1 align="center">Support</h1>

<p align="center">
  Bambu Lab continues tightening compatibility around BMCU, and there is a growing risk that BMCU may eventually become unusable in that ecosystem.
</p>

<p align="center">
  To prepare for that, I want to build BMCU support for open-source Klipper-based printers.
</p>

<p align="center">
  I am currently raising funds to buy a test printer for this work.
</p>

<p align="center">
  The $500 goal does not need to be reached in full. If I manage to save the remaining amount myself, I will cover the rest out of my own pocket.
</p>

<p align="center">
  <a href="https://ko-fi.com/jarczakpawel/goal?g=0">
    <img src="./banner-klipper.png" alt="Want BMCU on Klipper? Click the links below to support development." width="460">
  </a>
</p>

<p align="center">
  <a href="https://ko-fi.com/jarczakpawel/goal?g=0"><strong>Support on Ko-fi</strong></a>
  ·
  <a href="https://revolut.me/paweqxdkx"><strong>Support via Revolut</strong></a>
</p>

<p align="center">
  Direct Revolut support avoids Ko-fi fees, so more of your contribution goes directly to the project.
</p>

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
