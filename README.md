![helios banner](http://i.imgur.com/S16v4Ux.png)

# Simple Data Integration in UE4 by Helios

### About
Integrating external data sources (i.e Twitter's API, data from an AWS server) into UE4 can be a real hassle for even the most experienced of developers. And for developers who primarily use Blueprints visual-scripting to build applications, this hassle becomes a near impossibility. More often than not, developers well-versed in handling web requests via simple AJAX calls must write vanilla C++ in UE4 to replicate the same functionality. Yuck!

Enter the **Helios Simple Data Integration (SDI) Plugin**.

The **Helios SDI Plugin** allows you to integrate external data into your UE4 client by interfacing directly with a web server using auto-generated Blueprints nodes (no more ugly C++ code!). With it, you can do things like:

- Control an in-game experience via an internet-connected device (e.g. changing lighting, weather, etc.) such as an iPad

- Send data to server, to be consumed by a separate client (e.g. web app showing heat-maps of kill locations, live match-tracking tickers, etc.)

- Communicate with third-party APIs such as Twitter, Facebook, Youtube, etc. from inside your UE4 client

Facilitating the server-client interaction between a web server and UE4 Blueprints is critical for developers who want to enrich their in-game experience by pulling in (or pushing out) data sources external to UE4. The Helios SDI Plugin allows you to do this without ever writing a line of C++!

### Usage Notes
See the [plugin usage article](https://github.com/HeliosOrg/SimpleDataIntegration/wiki/Plugin-Usage) for information on how to use the nodes and for usage examples.

### Installation Notes
1. First, follow the [server setup article](https://github.com/HeliosOrg/SimpleDataIntegration/wiki/Server-Setup).
2. Then, follow the [plugin setup article](https://github.com/HeliosOrg/SimpleDataIntegration/wiki/Plugin-Setup).

### Technical Details
To create such simple Blueprint nodes, we had to do bunch of non-inuitive work behind the scenes. If you want to learn how the plugin works and/or help contribute to this open source project, check out our [technical details article](https://github.com/HeliosOrg/SimpleDataIntegration/wiki/Technical-Details)! Also, we learned a lot while building this plugin, so in that article, we've also shared some of the questions we had and roadblocks we ran into in case they're of any help to you.
 
### The Team

| ![Derin Dutz profile](http://i.imgur.com/Y36vNH9.png) | ![Dennis Xu profile](http://i.imgur.com/txhQ4W2.png) | ![Ash Ngu profile](http://i.imgur.com/Lc5IIkR.png) | ![Ryan Davies profile](http://i.imgur.com/a7XueIR.png) |
|:---:|:---:|:---:|:---:|
| [Derin Dutz](http://derindutz.com/) | Dennis Xu | Ash Ngu | Ryan Davies |

