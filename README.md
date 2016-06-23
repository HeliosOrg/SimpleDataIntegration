![helios banner](http://i.imgur.com/S16v4Ux.png)

#Simple Data Integration in UE4 by Helios
Integrating external data sources (i.e Twitter's API, data from an AWS server) into UE4 can be a real hassle for even the most experienced of developers. And for developers who primarily use Blueprints visual-scripting to build applications, this hassle becomes a near impossibility. More often than not, developers well-versed in handling web requests via simple AJAX calls must write vanilla C++ in UE4 to replicate the same functionality. Yuck!

Enter the **Helios Simple Data Integration (SDI) Plugin**.

The **Helios SDI Plugin** allows you to integrate external data into your UE4 client by interfacing directly with a web server using auto-generated Blueprints nodes (no more ugly C++ code!). With it, you can do things like:

- Control an in-game experience via an internet-connected device (e.g. changing lighting, weather, etc.) such as an iPad

- Send data to server, to be consumed by a separate client (e.g. web app showing heat-maps of kill locations, live match-tracking tickers, etc.)

- Communicate with third-party APIs such as Twitter, Facebook, Youtube, etc. from inside your UE4 client

Facilitating the server-client interaction between a web server and UE4 Blueprints is critical for developers who want to enrich their in-game experience by pulling in (or pushing out) data sources external to UE4. The Helios SDI Plugin allows you to do this without ever writing a line of C++!

![get_decal](http://i.imgur.com/oWyfee6.png)

#Getting Started

### 1) Download and setup the server
1. Clone `HeliosServer`from our Github https://github.com/HeliosOrg/HeliosServer onto your server (AWS, Digital Ocean, etc.).
2. Install Node on this computer if you haven’t already.
3. Run `npm install .` in the `HeliosServer` folder.
4. Run `npm install forever -g`

### 2) Set up the JSON file
The Helios SDI nodes in both the client (Blueprints) and the server (in this case, a node server) are generated from an `input.json` file as follows:
	
1. In the `input.json` file inside the `HeliosServer` folder, specify the name (in upper camel case) and type (`int`, `bool`, `FString`, or `float`) of each variable you want to create a simple interface in UE4. These names will correspond to both your server endpoints as well as the node headers in your Blueprints client. 
2. Add your server URL to the start of `input.json`

```
\\\ Example input.json

{
  "server_url": "http://ec2-54-100-240-19.us-west-1.compute.amazonaws.com/helios/",
  "single_instance_variables": [
    {
      "name": "IsLightOn",
      "type":"bool" 
    },
    {
      "name": "NumKills",
      "type":"int"
    },
    {
      "name": "UserName",
      "type": "FString"
    },
    {
      "name": "WinPercentage",
      "type": "float"
    }
  ]
}

```
3. Run `node createServer.js` This creates a server.js file that you can then fire up by running `forever server.js` or `node server.js`


### 3) Download and setup the UE4 Plugin
************ @Derin or @Ryan, please fill this part in ************

1. Clone `HeliosPlugin`from our Github https://github.com/HeliosOrg/HeliosPlugin into your `Plugins` folder inside your UE4 project folder.
2. Make a copy of your `input.json` file and move it from the `HeliosServer` folder into the `HeliosPlugin` folder.
3. Add an empty C++ class to your UE4 project. File > New C++ Class. Choose None as your parent class. This adds a number of files and folders to your project folder.
4. Open the `Source` folder in your project. Then open the folder titled with your project name, in our case this folder is called `HeliosFinal`. Open up the file with `Build.cs` in its name, i.e. for us this is `HeliosFinal.Build.cs`. Inside this file, add `"SimpleDataIntegration"` to the following line: `PrivateDependencyModuleNames.AddRange(new string[] { "SimpleDataIntegration" });`
![heliosfinal.build1](http://i.imgur.com/kuIOFuc.png)
![heliosfinal.build](http://i.imgur.com/K0ckYQe.png)
5. Open `DefaultEngine.ino` in the project's `Config` folder and add to the `[Plugins]` section like so:
`[Plugins]
+EnabledPlugins=SimpleDataIntegration`
![default_engine](http://i.imgur.com/TOSyWpg.png)

************ @Derin or @Ryan, please fill this part in ************
### 4) Use the Blueprint nodes in your UE4 project
Sending and retrieving data to and from an external server that you control is as easy as dragging out the appropriate getter or setter node into Blueprints.

1. Restart your project if it is open.
2. Right-click within a Blueprints Event Graph and type in the name of whatever variable you wish to GET or SET. For example, for the `DecalColor` variable, there are two types of nodes, `Get DecalColor` and `Set DecalColor`.
![nodes_right_click](http://i.imgur.com/yzeKPwr.png)
3. Select the appropriate Blueprint nodes and use them to GET and SET your variables!

An example of pulling from the server: Event Tick > Delay (0.3) > Get DecalColor
![get_decal](http://i.imgur.com/oWyfee6.png)

An example of posting to the server:
Keyboard Event 1 > Set DecalColor ("green")
![set_decal](http://i.imgur.com/k8AJAwc.png)


#More Details
######How are the nodes automatically generated?

When you right-click within a Blueprint’s ‘Event Graph’, a dropdown menu of all the available node options appears.

[Derin, I need a detailed technical explanation here of how the dropdown menu looks among K2Node meta data to generate these nodes]

Helios nodes appear under the Networking section of this dropdown.

###### Using the plugin with third party servers

 
######Implications for virtual reality
 
 
### The Team

| ![Derin Dutz profile](http://i.imgur.com/Y36vNH9.png) | ![Dennis Xu profile](http://i.imgur.com/txhQ4W2.png) | ![Ash Ngu profile](http://i.imgur.com/Lc5IIkR.png) | ![Ryan Davies profile](http://i.imgur.com/a7XueIR.png) |
|:---:|:---:|:---:|:---:|
| Derin Dutz | Dennis Xu | Ash Ngu | Ryan Davies |

