---
title: Web SDK FAQ
seo-title: Adobe Experience Platform Web SDK FAQ
description: Frequently asked questions about Adobe Experience Platform Web SDK
seo-description: Frequently asked questions about Adobe Experience Platform Web SDK
---

# Frequently asked questions

This FAQ includes questions that are often asked aboutthe Adobe Web SDK/

## What is Adobe Experience Platform Web SDK?

Adobe Experience Platform Web SDK is a client-side JavaScript library that allows customers of the Adobe Experience Cloud to interact with the various services in the Experience Cloud.

It sends data in a solution-agnostic way (XDM) to the Adobe Experience Platform Edge Network, which then maps the data to solution specific formats and destinations and sends it in real time. 

**More information** 
[Adobe Summit presentation](https://www.adobe.com/summit/2020/with-alloy-js-never-tag-for-an-evar-or-mbox-again.html)

## How does Adobe Experience Platform Web SDK differ from previous solutions?

### Prior to Adobe Experience Platform SDK

Currently, you have to deploy different JavaScript libraries based on each individual solution.

* Each solution has its own JavaScript library, schema, and domain.
* None of these libraries were built to work with each other.
* Cross-solution and Adobe Experience Platform use cases require these disparate libraries to be interdependent, causing deployment friction.

Although Adobe Experience Platform Launch makes it as easy as possible to deploy and manage these libraries, there are still issues with:

* Library size (too much Adobe code on a page)
* Performance (sites take too long to load)
* Multiple calls for a single use case 
* Waiting for ECID return before personalization calls (causes lag)
* Fractured data collection (what is an evar?)
* Schema confusion between solutions (A4T)
* Lots of other less optimal things

Also, there is currently no JavaScript library that sends data directly to Adobe Experience Platform.

### With Adobe Experience Platform Web SDK

The new Web SDK sends data for the following solutions to a single destination (AEP Edge Network) and solves for the most common aforementioned solution use cases. 

* Adobe Analytics
* Adobe Audience Manager
* Adobe Target
* Visitor ID
* Adobe Experience Platform 

Other solutions will follow later this year. 

Adobe Experience Platform Web SDK can also send data directly to Adobe Experience Platform. This data is in XDM and is mapped to the server-side solution schema. 

## What is the value of this new web SDK?

**Performance:** The web SDK is smaller than using all of the current Adobe libraries and provides significantly faster page loads. 

**Simplicity:** The combination of XDM, Web SDK, Launch, Experience Edge, Adobe Experience Cloud solutions, and Adobe Experience Platform creates an easy-to-understand and simple-to-follow data collection story. 

* **XDM:** The solution-agnostic schema you use to send data to Adobe. No more tagging for evars or mboxes.
* **Web SDK:** Makes it easy to send and receive data to the Adobe Experience Platform Edge Network. 
* **Launch:** Simplifies deployment and configuration of the Web SDK (and any other JavaScript tags) on a site.
* **Experience Edge:** Easily route the data to Adobe Experience Platform and solutions in the format they need.
* **Adobe Experience Platform and Adobe solutions:** Enable their value proposition.

**Control:** Because all of the data is using a single and connected stream of data, you can logically follow and control what the data looks like at every millisecond of its journey, to and from applications.

**Modern and ready for the future:** The Web SDK and its connection to the Experience Edge Network has enabled Adobe to significantly modernize how Adobe deals with data collection, personalization, consent and the future of 3rd party cookies. (It enables a first party domain, managed by Adobe.)

**Time-to-value:** Adobe has worked hard (and will continue) to make it as easy as possible to deploy the Web SDK via Launch and map client-side data to XDM.  After that work is done, all other Adobe solutions and Adobe Experience Platform services can be turned on or off server-side. For example, if you are using this for Adobe Analytics and you want to turn on Target or Experience Platform, you can simply flip a toggle on the Experience Edge configuration and light up those use cases. 

## What is `alloy.js`?

`Alloy.js` is the file name for the Adobe Experience Platform Web SDK. Adobe Experience Platform Web SDK is the official name, but many developers refer to it as "alloy."

## Do customers need to buy Adobe Experience Platform to use the Web SDK?

No. Any Adobe Digital Experience customer can use it. Totally free. Any customer wanting to use the Web SDK will be given access to create schemas and datasets in the Adobe Experience Platform UI.

## Who should use the Web SDK?

The Adobe Experience Platform Web SDK has been developed for the following people:

* Adobe Experience Platform users

    If you need to send data directly from a device to Adobe Experience Platform, this is the officially recommended way. 

    Adobe is aware that using the Adobe Analytics connector is faster if the customer already has Adobe Analytics, but it is not the long-term strategy for data collection. 
    
* Adobe Experience Cloud solution customers

    New Adobe Analytics, Adobe Audience Manager, and Adobe Target customers should start with the new Web SDK and not use legacy libraries.

    Existing customers who want to get the most optimized implementation possible should use the new Web SDK. 


## How do I get access to start using the Adobe Experience Platform Web SDK?

The Web SDK is currently available to the general public and can be used to send data to Adobe Experience Cloud products. The ability to send data to third party solutions is coming in the near future. If you would like to get access to the Web SDK contact your CSM to start the request process.

## What use cases are currently supported by the Web SDK?

The Web SDK is quickly evolving. More use cases are being worked on. You can find the [list of use cases currently supported here.](https://github.com/adobe/alloy/projects/5)

## Do current customers have to retag their sites?

It depends. The Adobe Experience Platform Web SDK can be deployed in two different styles. A future migration document will provide additional details.

* **Just another tag:** If the site is already tagged for solutions and you can't retag, but you want to send data to the Adobe Experience Platform Edge Network for Experience Platform use cases or the upcoming Launch server-side features (see below), you can add the `alloy.js` tag to the site, where it works as "just another tag."

* **The one and only tag:** If you want to use the Web SDK for an Experience Cloud solution, you must use it for _all_ of the solutions on that page. For example, if your site is already tagged for Analytics and you want to use it for Target, you need to use it for both, as well as for any others in the future.  

In other words, if you decide to use the Adobe Experience Platform Web SDK for non-solution use cases, you can tag the site with `alloy.js` and move on as if it's a new solution. If you want to use it for Adobe Analytics, Target, or Audience Manager, or for application use cases, you might have to remove any of the legacy code on your page. 

## Can I migrate the ECIDs when I start using Alloy so my website visitors don't start showing up as new visitors?

Yes, the Adobe Experience Platform Web SDK provides an Identity Migration feature. Follow the instructions in [this document](https://docs.adobe.com/content/help/en/experience-platform/edge/fundamentals/identity.html#id-migration) for more details.

## How is the Web SDK different than Adobe Experience Platform Launch?

* **Launch** is the device code manager. Use it to more easily deploy the code. It is free and powerful.

* **Adobe Experience Platform Web SDK** is the official name of the new code that would be deployed by Launch for Adobe use cases. It is also free and powerful.

* **`alloy.js`** is the file name of the Adobe Experience Platform Web SDK code.

## Do I have to use Adobe Experience Platform Launch to deploy the Web SDK?

No. You can download the `alloy.js` file yourself.

However:

* The Adobe Experience Platform Web SDK requires something called an Experience Edge configuration ID so the edge network can identify the stream and determine what to do with the data. This ID is created within Launch. This doesn't mean you have to use Launch to create properties or deploy the JavaScript code, but you do need to use Launch to create a configuration ID.

* Adobe Experience Platform Launch is not only the best available tag and SDK manager, it makes it very easy to deploy `alloy.js` and map data to XDM schemas. If you decide not to use Launch, you will have to manage deploying `alloy.js`, eventing, and mapping your data into XDM before sending it. This is a _much_ more difficult process than using Launch. 

* It is recommended that you use Launch to deploy `alloy.js`, even if it's the only tag you use it for. 

## What is XDM and do I have to use to the Web SDK?

XDM is the data format used to send data to the Adobe Experience Platform and the Web SDK. The [Web SDK documentation](https://docs.adobe.com/content/help/en/experience-platform/edge/get-started/quick-start-with-launch.html#prepare-a-schema) walks you through how to easily set up a schema that you can then customize to your specific needs.

## What is "Adobe Experience Platform Launch Server Side?

Later in 2020, Launch will release server-side forwarding features. If you use our SDKs and send XDM to the Experience Edge, these new features will allow you to install new server-side extensions and map that data to anything--and send it anywhere--from our edge network. Think of it as “data collection as a service”.  This will be available for a cost, as well as being bundled as part of the Adobe Experience Platform. 

**More information** 
[Adobe Summit presentation](https://adobe.bluejeans.com/playback/s/9LhauPOnRSUTYg6RMHAw4oJekhYfOQgdBLlNekVJdWevYktpxqX2IYyl5fz2Wxh9)

## What is a CNAME or First Party Domain and why does it matter?

More information about a CNAME is available in the [Adobe documentation](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html)

## Where can I get more info about Adobe Experience Platform Web SDK?

* [Documentation](https://docs.adobe.com/content/help/en/experience-platform/edge/home.html)
* [Source Code](https://github.com/adobe/alloy)
