# Magic Mirror
A smart mirror is an innovative device that integrates a reflective surface with a digital display, providing real-time information such as weather updates and news. It also provides extensive customization opportunities, allowing you to display all sorts of information. This incorporates the use of a mirror with the usefull features of electronic devices.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Sean A | Leonia High School | Electrical Engineering | Incoming Junior |

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone 

# First Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/CaCazFBhYKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

My project is the MagicMirror, which combines the use of a mirror with a personal assistant. The initial components that I used were a Raspberry Pi 4, which is used to power the Mirror, and a 7" LCD Screen, to display it on. The LCD Screen connects to the Raspberry Pi via an HDMI connection. So far, I managed to install the MagicMirror Operating System on the Raspberry Pi itself, with both Node.js and npm. I also managed to connect the Pi to the screen and have customized the display to include useful information such as the weather, the time, and CPU information.

One challenge that I faced arose when I tried to use the `MMM-Touch` module, as it seemed that even though the display came with touchscreen capabilities, the module wouldn't receive or recognize any of the inputs I gave (by touching the screen). I decided to just go through without using `MMM-Touch`, as there were other modules that also used touch-recognition that worked fine. I plan to try and experiment with it a little more in future milestones; however, for now, I am at a good place.

I plan to add at least a couple of modifications to my MagicMirror, such as motion sensing capabilities, Bluetooth, and possibly more.

# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

Below is the `./config/config.js` file
```js
/* Config Sample
 *
 * For more information on how you can configure this file
 * see https://docs.magicmirror.builders/configuration/introduction.html
 * and https://docs.magicmirror.builders/modules/configuration.html
 *
 * You can use environment variables using a `config.js.template` file instead of `config.js`
 * which will be converted to `config.js` while starting. For more information
 * see https://docs.magicmirror.builders/configuration/introduction.html#enviromnent-variables
 */
let config = {
	address: "localhost",	// Address to listen on, can be:
							// - "localhost", "127.0.0.1", "::1" to listen on loopback interface
							// - another specific IPv4/6 to listen on a specific interface
							// - "0.0.0.0", "::" to listen on any interface
							// Default, when address config is left out or empty, is "localhost"
	port: 8080,
	basePath: "/",	// The URL path where MagicMirror² is hosted. If you are using a Reverse proxy
									// you must set the sub path here. basePath must end with a /
	ipWhitelist: ["127.0.0.1", "::ffff:127.0.0.1", "::1"],	// Set [] to allow all IP addresses
									// or add a specific IPv4 of 192.168.1.5 :
									// ["127.0.0.1", "::ffff:127.0.0.1", "::1", "::ffff:192.168.1.5"],
									// or IPv4 range of 192.168.3.0 --> 192.168.3.15 use CIDR format :
									// ["127.0.0.1", "::ffff:127.0.0.1", "::1", "::ffff:192.168.3.0/28"],

	useHttps: false,			// Support HTTPS or not, default "false" will use HTTP
	httpsPrivateKey: "",	// HTTPS private key path, only require when useHttps is true
	httpsCertificate: "",	// HTTPS Certificate path, only require when useHttps is true

	language: "en",
	locale: "en-US",   // this variable is provided as a consistent location
			   // it is currently only used by 3rd party modules. no MagicMirror code uses this value
			   // as we have no usage, we  have no constraints on what this field holds
			   // see https://en.wikipedia.org/wiki/Locale_(computer_software) for the possibilities

	logLevel: ["INFO", "LOG", "WARN", "ERROR"], // Add "DEBUG" for even more logging
	timeFormat: 12,
	units: "imperial",

	modules: [
		{
			module: "alert",
			positition: "top_bar",
		},
		{
			module: "updatenotification",
			position: "top_center"
		},
		{
			module: "clock",
			position: "top_left"
		},
		{
			module: "calendar",
			header: "US Holidays",
			position: "top_left",
			config: {
				calendars: [
					{
						fetchInterval: 7 * 24 * 60 * 60 * 1000,
						symbol: "calendar-check",
						url: "https://ics.calendarlabs.com/76/mm3137/US_Holidays.ics"
					}
				]
			}
		},
		{
			module: "MMM-Pollen",
			position: "top_left",
			header: "Pollen Forecast",
			config: {
				zipCode: "07605",
				updateInterval: 60 * 60 * 1000, // Update every hour
			}
		},
		{
			module: "weather",
			position: "top_right",
			config: {
				weatherProvider: "openmeteo",
				type: "current",
				roundTemp: true,
				degreeLabel: true,
				lat: 40.86190216978815,
				lon: -73.98366785585593
			}
		},
		{
			module: "weather",
			position: "top_right",
			header: "Weather Forecast",
			config: {
				weatherProvider: "openmeteo",
				type: "forecast",
				lat: 40.86190216978815,
				lon: -73.98366785585593
			}
		},
		{
			module: 'MMM-AQI',
			position: 'top_right',
			header: 'Air Quality Index (AQI)',
			config: {
				token: "YOUR API TOKEN HERE",
				city: "here",
				iaqi: true,
				updateInterval: 30 * 60 * 1000, // Every half hour.
				initialLoadDelay: 0,
				animationSpeed: 1000,
				debug: false
			}
		},
		{
			module: "MMM-PiTemp",
			position: "bottom_right",
			config: {
				tempUnit: "F",
				high: 196,
				low: 158,
				label: "CPU: "
			}
		},
		{
			module: "MMM-HideAll",
			position: "bottom_left",
			config: {
				hidetext: "",
				showtext: "",
				fadespeed: 1000,
				vishidden: 0.3,
				symbolhide: "toggle-off",
				symbolshow: "toggle-on"
			}
		},
/* 		{
			module: "MMM-pages",
			config: {
				timings: {
					default: 5000,
					0: 10000,
				},
				modules: [
					[]
				],
				fixed: [
					// "clock",
					"weather",
					"MMM-HideAll",
				]

			}
		},
		{
			module: "MMM-page-indicator",
			position: "bottom_bar",
			config: {
				activeBright: true,
				inactiveHollow: false,
			}
		} */
		{
			module: "MMM-quote-of-the-day",
			position: "bottom_bar",
			config: {
				feeds: {
					langauge: "en",
					updateInterval: "1d"
				},
			}
		},
/* 		{
			module: "MMM-Touch",
			position: "fullscreen_above",
			config: {
				gestureCommands: {

				},
				onIdle: () => { this.sendNotification("TOUCH_IDLE_TRIGGERED", {}); console.log("Touch Idle Triggered"); },
			},
		}, */
	]
};

/*************** DO NOT EDIT THE LINE BELOW ***************/
if (typeof module !== "undefined") { module.exports = config; }
```

And here is the `./css/custom.css` file (can be used for further customizing the look of modules):
```css
.hide-toggle{
	border: 0px solid #FFF;
}

.hide-toggle div{
	position: absolute;
		top: 0px;
		right: 0px;
		bottom: 0px;
		left: 0px;
	font-size: 55px;
}

#pi_temp{
	font-size: 40px;
}
```


# Bill of Materials

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Raspberry Pi 4 Starter Kit | Power's the display for the smart mirror | $96.99 | <a href="https://www.amazon.com/RasTech-Raspberry-Starter-Heatsink-Screwdriver/dp/B0C8LV6VNZ"> Link </a> |
| (7") LCD Display | Used for displaying the MagicMirror | $45.99 | <a href="https://www.amazon.com/Hosyond-Display-1024%C3%97600-Capacitive-Raspberry/dp/B09XKC53NH/"> Link </a> |
| Wireless Keyboard and Mouse | (Optional) Used to interact with the Raspberry Pi directly without having to go through SSH / navigating the mirror directly | $29.99 | <a href="https://www.amazon.com/Logitech-MK270-Wireless-Keyboard-Mouse/dp/B079JLY5M5"> Link </a> |

# Other Resources
- [MagicMirror Docs/Guide](https://docs.magicmirror.builders/)
- [MagicMirror Wiki](https://github.com/MagicMirrorOrg/MagicMirror/wiki)
- [3rd Party Modules](https://github.com/MagicMirrorOrg/MagicMirror/wiki/3rd-party-modules)
