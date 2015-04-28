Getting Started with ClientSuccess Usage Tracking
===================

ClientSuccess uses event/usage information to provide CSMs and Account Managers with views and insights into customer health.  This helps CSMs prioritize their time and act proactively to reduce customer churn.

We currently support two ways of sending event data into ClientSuccess:
> 1. Server-Side API
> 2. JavaScript Tracking Library

----------

###Server-Side API

You can send event information using simple `GET` requests.  Documentation for the server-side API can be found at [ClientSuccess Usage API Docs](http://docs.clientsuccessusage.apiary.io/).

----------

###JavaScript Tracking Library

####Quick Start

1. Include the `csTrack.js` library on your page.
	```
	<script src="//cdn.clientsuccess.com/csTrack.min.js"></script>
	```

2. Initialize the CSTrack library.
	```
	window.csTrack = new CSTrack('YOUR_PROJECT_ID', 'YOUR_API_KEY');
	
	// Add identification
	window.csTrack.identify({
	    client: {
	        id: 12345,                      // REQUIRED     A unique identifier for the client (may be string or number)
	        name: 'Widget Factory'          // REQUIRED     A human readable name for the client.
	    },
	    user: {
	        id: 456789,                     // OPTIONAL     A unique identifier for the user (may be the user's email address)
	        name: 'Bob Jones',              // OPTIONAL     The logged in user’s name
	        email: 'bob@widgetfactory.com'  // OPTIONAL     The logged in user’s email address
	    }
	});
	```

3. Track event.
	```
	window.csTrack.trackEvent('interaction - button pressed');
	// OR
	window.csTrack.trackEvent('subscription renewed', 1299.95);
	```


