# Web Monetization @ Solid
Discussions about Solid + Web Monetization

## Linking to a Payment Pointer
You can link from a WebID to a payment pointer using the
[`ilp:InterledgerPaymentPointer`](https://github.com/solid/webmonetization/issues/9) class.

You can link from a pod to a payment pointer using a
[Vanity Payment Pointer](https://community.webmonetization.org/michielbdejong/web-monetization-on-solid-2bbf).

## Requiring Payment for resources
You can require payment for access to a resource using the
[`acl:PayingAgent`](https://github.com/solid/acl-check/pull/38) class.

The WAC spec doesn't prescribe specific http response codes, but a server could
inform the client that paying could help to get access by responding with
`402 Payment Required` and including a `Pay` http response header, with payment
instructions.

A 402 would probably take preference over a 403 response when access is forbidden
for the currently authenticated agent, but not for paying agents. But a 402 would
probably not take preference over a 401 response.

We identified two approaches for access control: "guest list" and "tickets".
In the "guest list" approach, the server looks at some log of payments, and checks
whether a payment has been made that would give the current WebID access to the
current resource. This is the approach that is now
[implemented in NSS](https://github.com/solid/node-solid-server/pull/1577) and
[tested by the (experimental) monetization tests](https://github.com/solid/monetization-tests).

In the "tickest" approach, the client would send an additional http request header
containing a verifiable credential, that proves their status of paying agent. This
approach is currently blocked on
[W3C-VC support in WAC](https://github.com/solid/authorization-panel/issues/79).

# Projects
## understory.garden (formerly itme.online)
[_Tani Olhanoski and team, USA_](https://www.grantfortheweb.org/blog/2020-flagship-grantees)

Creating an open source Solid application that will let users easily publish, create, and monetize custom pages showcasing writing, music and video content hosted in their Solid Pod at a domain of their choosing. Existing platforms that allow users to monetize their content require either the skills and capitalization to maintain custom web infrastructure or a willingness to let a third party become a steward of both content and data about content creators. itme.online will provide a new option for users who would like to maintain full sovereignty over their content and monetize it without running a web server. Building on top of Solid and Web Monetization means that users will be free to move their content off of itme without interrupting the monetization of their content. In addition to Tani, the team includes Ian Davis and Travis Vachon, and is advised by [Dr Dédé Tetsubayashi and her team](https://incluu.us).

Progress report: https://community.webmonetization.org/itmeonline/itme-online-grant-report-1-1cfo
and: https://community.webmonetization.org/travis/itme-online-is-now-understory-garden-grant-report-2-1o0i

## Monetizing the user-centric read-write web with Solid
[_Michiel de Jong, Netherlands_](https://www.grantfortheweb.org/blog/2020-mid-grantees)

(See [WebMonetization Community](https://community.webmonetization.org/michielbdejong/comment/ec))

Enabling Web Monetization by default in all open source implementations of the Solid pod server specification. Also, making changes to Darcy Social, a Solid-based social space, so that payments end up at the actual creator of the content that is being viewed, even if it's embedded in a newsfeed.

Progress report: https://community.webmonetization.org/michielbdejong/web-monetization-on-solid-2bbf
## Web Monetization for Solid based Data Spaces
_[Ontola](https://ontola.io/) & [Dexes](https://www.dexes.nl/home-dexes/)_

(See [WebMonetization Community](https://community.webmonetization.org/joepio/comment/c8))

Standardizing the agreements for conditional data sharing between data owner and data user to allow Solid Pod owners to monetize their data. Pods re-decentralize the web by giving people a way to store their data, and make it available to others while keeping full data ownership. Interledger offers a perfect solution for micro-payments without the need for complex and centralized payment providers. 

Combining [ODRL](https://www.w3.org/TR/odrl-model/) + Interledger.

Grant report: https://community.webmonetization.org/wbsbds/web-monetization-for-solid-based-data-spaces-grant-report-1-4fal

## Reciprocal ecosystem for citizen science
_[Gijs van den Beucken](https://opengezondheid.nl/) & [Ontola](https://ontola.io/)_

Researching and building a proof of concept of a web-based platform to enable citizens to participate in citizen science, integrating interledger protocol and payment pointers so researchers can reimburse citizens for participation in for example environmental health research. Survey-data will be stored in linked data format and users can copy the data on their own SolidPod.

Grant report: https://community.webmonetization.org/refdhd/reciprocal-ecosystem-for-citizen-science-grant-report-1-3d27

## Incentivizing Decentralized Application Development within Solid through Web Monetization
_[KNoWS/IDLab – imec](https://github.com/KNowledgeOnWebScale/solid-web-monetization)_

The **Solid decentralization effort** decouples data from services, so that users are in full control over their personal data.
Since services can not primarily depend on data collection as a primary business model anymore, alternative forms of monetization,
such as **micropayments via Web Monetization** are essential for **incentivizing application development**.

See https://github.com/KNowledgeOnWebScale/solid-web-monetization for more information.

## Monetising Resources on a SoLiD Pod Using Blockchain Transactions (ESWC Demo)
_Hendrik Becker, [Hung Vu](https://github.com/bright-fox), Anett Katzenbach, [Christoph Braun](https://github.com/uvdsl) & [Tobias Käfer](https://www.aifb.kit.edu/web/Tobias_K%C3%A4fer), [Institute AIFB, Karlsruhe Institute of Technology (KIT), Germany](https://aifb.kit.edu/web/Hauptseite/en)_

**Abstract.** Our demo showcases a system that allows users to provide access to web resources in exchange for payments via the Ethereum blockchain. The system enables users to create offers for their resources or buy access rights for resources belonging to other users. Access rights can be granted only for a limited amount of time. We built our system as SoLiD Pods and Apps: We developed two server modules for SoLiD Pods that automatically (1) grant access for valid payments via the blockchain and (2) remove expired access rights. On top, we developed a SoLiD App that allows to offer resources, browse and request offered resources, and make payments via the blockchain.

| Resource | URI |
|---|---|
|Teaser (1 min) | https://www.youtube.com/watch?v=sqIeYRTrkEg |
| Demo Website (inkl. 3 min video) | http://people.aifb.kit.edu/co1683/2021/eswc-demo-solibra/ |
| Code | https://github.com/bright-fox/SolidBlockchain |
| Paper | http://people.aifb.kit.edu/co1683/2021/eswc-demo-solibra/solibra.pdf |
