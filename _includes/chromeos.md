### Chrome OS

 * Connection manager for Chrome OS attempts to retrieve the web page [http://clients3.google.com/generate_204](http://clients3.google.com/generate_204). This well known URL is known to return an empty page with an HTTP status 204. If for any reason the web page is not returned, or an HTTP response other than 204 is received, then shill marks the service as being in the portal state.

 * Other captive portals, sometimes run by cellular carriers, provide absolutely no IP connectivity other than to their own servers, but they use a standard DNS server and do not intercept HTTP requests. When a Chrome Book connects to this type of network, the HTTP requests fail because the TCP connection to clients3.google.com can never be established. The portal code tries multiple times for up to 10 seconds to connect to clients3.google.com. If it cannot connect it marks the service as being in a captive portal. This determination is somewhat unreliable because very high latency connections, lossy connections and other network issues can also result in failure to connect to clients3.google.com. All of these are indicative of a network that is not fully functional, but they do not necessarily indicate that the machine is stuck in a captive portal.