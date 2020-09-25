---
#
# Here you can change the text shown in the Home page before the Latest Posts section.
#
# Edit jekyll-theme-simple-blog's home layout in _layouts instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
#
layout: home
permalink: /index.html
title: Multipath Transport Protocols Tutorial @ MobiCom 2020
header:
  image: /assets/img/home-header.jpg
tagline: > # this means to ignore newlines until "repository:"
  Fri. Sept. 25, 2020 ~ 4:00 pm - 7:30 pm CEST
ref: home
lang: en
---

# Call For Participation

This tutorial aims at summarizing the lessons learned during the last ten years with multipath transport to enable MobiCom attendees to correctly apply those emerging protocols. More precisely, our tutorial’s objectives are the following:

* Understand the benefits and challenges of using multiple paths in the transport layer
* Understand the design assumptions and principles of Multipath TCP
* Understand how the security and flexibility features of QUIC have enabled a cleaner design for Multipath QUIC
* Discover the impact of the algorithms that implementations use to manage the different paths: path manager, packet scheduler and the required adaptations to the congestion control scheme

At the end of the tutorial, the attendees will be able to determine when and how multipath transport can be applied to their use cases. They will also have a more in-depth understanding of the impact of the packet scheduling, congestion control and path management mechanisms on the performance of these protocols.

## [Link to the Slack channel](https://app.slack.com/client/T018NQGMDQE/C01BDECHEV6)

# Tutorial Program

| 4:00 pm - 5:30 pm CEST | Session I: Multipath TCP |
|:----------------------:|:------------------------:|
| 4:00 pm - 5:00 pm CEST | The design of Multipath TCP and the influence of the middleboxes |
| 5:00 pm - 5:30 pm CEST | Hands-on labs: The impact of multi-path algorithms |
| **5:30 pm - 6:00 pm CEST** | **Coffee Break** |
| **6:00 pm - 7:30 pm CEST** | **Session II: Multipath QUIC** |
| 6:00 pm - 7:00 pm CEST | Applying Multipath principles to a cleaner transport protocol: Multipath QUIC |
| 7:00 pm - 7:30 pm CEST | Hands-on labs: Multipath QUIC in action and tweaking its packet scheduler |

# Outline

This tutorial consists in two lectures and two hands-on labs.

* **The design of Multipath TCP and the influence of the middleboxes:** After introducing why using multiple paths can be desirable and which challenges such protocols face, this lecture explains how TCP can be extended through TCP options to support the simultaneous usage of multiple paths and reports deployment experiences that led to the current design
* **Hands-on labs: the impact of Multipath algorithms:** This hands-on lab is based on a vagrant box that enables participants to figure out the importance of the multipath algorithms (path manager, packet scheduler,...) depending on the network conditions and the network traffics
* **Applying multipath principles to a cleaner transport protocol: Multipath QUIC:** This lecture introduces the main features of the QUIC protocol and then explains how Multipath QUIC got rid of many design issues that affects Multipath TCP. It also briefly discusses its envisionned use cases, such as ATSSS [ATSSS]
* **Hands-on labs: Multipath QUIC in action and tweaking its packet scheduler:** This second hands-on lab reuses the vagrant box to observe how a Multipath QUIC implementation behaves and allows participants to hack with its packet scheduler, one of the key multipath algorithms

# Background

While in the early days of the Internet computers were connected using a single wire, most of the devices have now the ability to connect to various networks. Nowadays, laptops and desktops typically have Wi-Fi and Ethernet connectivities, while smartphones and tablets can attach to Wi-Fi and cellular access points. Still, the classical Internet protocols such as TCP, UDP and the emerging QUIC assume that hosts only use one network interface.

With the proliferation of mobile devices, there is a growing number of hosts that are “physically” able to use two or more network interfaces. However, these paths are rarely exposed and used by the applications. The standardization of Multipath TCP [RFC6824] changed the situation. With Multipath TCP, a smartphone can use both Wi-Fi and cellular networks to exchange data. 9 months after the publication of RFC6824, Apple deployed Multipath TCP on all iPhones to support their Siri voice recognition application. Indeed, Siri suffered from handovers when the users walk away from Wi-Fi access points. Over the years, supporting seamless handovers became more and more important to provide a smooth application experience and third-party applications as well as Apple Maps and Apple Music also use Multipath TCP.

Another use case for Multipath TCP is the aggregation of the bandwidth of the different network paths. This use case has been deployed on smartphones (Korean Telecom) where it allows combining 4G and Wi-Fi [BS16] and also in Hybrid Access Networks [KHB20] that combine xDSL and 4G. Last year, 3GPPP has adopted Multipath TCP as the basis for the new Access Traffic Steering, Switch and Splitting that will combine Wi-Fi and 5G [ATSSS].

The two main implementations of Multipath TCP are the reference implementation in the Linux kernel [MPTCPLK] and Apple’s one. The Linux implementation has been used for many of these use cases but was not officially integrated in the mainline Linux kernel. There is an ongoing effort to merge Multipath TCP in the mainline Linux kernel with a basic support included in Linux 5.6. The availability of Multipath TCP in the official Linux kernel will even more encourage the adoption of this protocol. In parallel, the IETF is finalizing the design of QUIC version 1 that aims at replacing the traditional TCP/TLS/HTTP/2 stack [Lan+17, QUIC-ID]. Many companies participate in this effort and there are more than a dozen implementations [QUIC-impl]. Once QUIC will be finalized, the working group will work on the multipath extensions to QUIC [QUIC-wg, MPQUIC].

These multipath protocols provide various benefits when they are used and deployed correctly. However, their basic principles are not always known by network operators and using them naively can even worsen the service experienced by applications [Den+14].

# Audience Expectations and Prerequisites

Anyone with basic understanding of TCP can participate in this tutorial. An overview of QUIC will be provided during the Multipath QUIC lecture. While active participation is not required, participants can experiment with multipath transport protocols during the hands-on labs thanks to a [vagrant box available here](https://github.com/qdeconinck/sigcomm20_mptp_tutorial). For an optimal experience, participants should install it before the tutorial.

# Organizers

## Quentin De Coninck (UCLouvain, Belgium)

[Quentin De Coninck](https://qdeconinck.github.io) received his Master degree in Computer Engineering at UCLouvain, Belgium in 2015 and finalized his Ph.D. thesis about "Flexible Multipath Transport Protocols" this year under the supervision of Olivier Bonaventure. He proposed improvements to Multipath TCP on smartphones and then designed, implemented and evaluated Multipath QUIC. He currently works on developing new techniques to better extend the QUIC protocol.

## Olivier Bonaventure (UCLouvain, Belgium)

[Olivier Bonaventure](https://perso.uclouvain.be/olivier.bonaventure) is professor at UCLouvain (Belgium) where he leads the [IP Networking Lab](https://inl.info.ucl.ac.be). Together with the Ph.D. students and postdocs of the lab, he has contributed to various networking protocols including BGP, LISP, Multipath TCP, IPv6 Segment Routing, and QUIC. He is active within the IETF and the lab has produced open-source implementations of important protocols including Multipath TCP, IPv6 Segment Routing, LISP, and more. He was editor in chief of SIGCOMM CCR and is the main author of the award-winning and open-source Computer Networking: Principles, Protocols and Practice e-book. He co-founded the Tessares company that pioneers the deployment of Hybrid Access Networks using Multipath TCP. Researchers from the IP Networking Lab received various awards including an INFOCOM best paper award, a SIGCOMM best paper award, an ICNP best paper award, a USENIX NSDI community award, several Applied Networking Research awards and the 2019 SIGCOMM Networking Systems Award for the development of the open-source implementation of Multipath TCP.

## References

[RFC6824] A. Ford, C. Raiciu, M. Handley, and O. Bonaventure. TCP Extensions for Multipath Operation with Multiple Addresses. Request for Comments 6824. Published: RFC 6824. IETF, Jan. 2013. https://datatracker.ietf.org/doc/rfc6824/

[BS16] O. Bonaventure and S. Seo. Multipath TCP Deployments. In: IETF Journal. Vol. 12. 2. Nov. 2016, pp. 24–27.

[KHB20] N. Keukeleire, B. Hesmans, and O. Bonaventure, Increasing Broadband Reach with Hybrid Access Networks, IEEE Communications Standards Magazine, March 2020

[ATSSS] 3GPP. Study on access traffic steering, switch and splitting support in the 5G system architecture (Release 16). https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=3254

[MPTCPLK] C. Paasch, S. Barre, et al. Multipath TCP in the Linux Kernel. http://www.multipath-tcp.org

[Lan+17] A. Langley et al. "The QUIC Transport Protocol: Design and Internet-Scale Deployment". In: Proceedings of the Conference of the ACM Special Interest Group on Data Communication - SIGCOMM ’17. Los Angeles, CA, USA: ACM Press, 2017, pp. 183–196.

[QUIC-ID] J. Iyengar and M. Thomson. QUIC: A UDP-Based Multiplexed and Secure Transport. Internet-Draft draft-ietf-quic-transport-27. IETF Secretariat, Feb. 2020. https://datatracker.ietf.org/doc/draft-ietf-quic-transport/

[QUIC-impl] Implementations. https://github.com/quicwg/base-drafts/wiki/Implementations

[QUIC-wg] QUIC. https://datatracker.ietf.org/wg/quic/about/

[MPQUIC] Q. De Coninck and O. Bonaventure. Multipath Extensions for QUIC (MP-QUIC). Internet-Draft draft-deconinck-quic-multipath-04. IETF Secretariat, Mar. 2020. https://datatracker.ietf.org/doc/draft-deconinck-quic-multipath/

[Den+14] S. Deng, R. Netravali, A. Sivaraman, and H. Balakrishnan. WiFi, LTE, or Both?: Measuring Multi-Homed Wireless Internet Performance. In: Proceedings of the 2014 Conference on Internet Measurement Conference - IMC ’14. Vancouver, BC, Canada: ACM Press, 2014, pp. 181–194.]
