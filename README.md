# Logstash UDP stream for Bunyan

# Configuration options

<table>
  <tr>
    <th>level</th>
    <td>string</td>
    <td><code>info</code></td>
  </tr>
  <tr>
    <th>server</th>
    <td>string</td>
    <td><code>os.hostname()</code></td>
  </tr>
  <tr>
    <th>host</th>
    <td>string</td>
    <td><code>"127.0.0.1"</code></td>
  </tr>
  <tr>
    <th>port</th>
    <td>number</td>
    <td><code>9999</code></td>
  </tr>
  <tr>
    <th>application</th>
    <td>string</td>
    <td><code>process.title</code></td>
  </tr>
  <tr>
    <th>pid</th>
    <td>string</td>
    <td><code>process.pid</code></td>
  </tr>
  <tr>
    <th>tags</th>
    <td>array|string[]</td>
    <td><code>["bunyan"]</code></td>
  </tr>
</table>

# Adding the bunyan-logstash stream to Bunyan


	var log = bunyan.createLogger({
	  streams: [
	    {
	      type: "raw",
	      stream: require('bunyan-logstash').createStream({
	        host: '127.0.0.1',
	        port: 5505
	      })
	    }
	  ]
	});

## Updating Logging Level Naming Conventions with custom names

###Default Level Definition

    var levels = {
      10: 'trace',
      20: 'debug',
      30: 'info',
      40: 'warn',
      50: 'error',
      60: 'fatal'
    };
	
###Example: Changing the Level Names to Spanish
    var levels = {
      10: 'rastro',
      20: 'depurar',
      30: 'info',
      40: 'advertir',
      50: 'error',
      60: 'fatal'
    };

	var log = bunyan.createLogger({
	  streams: [
	    {
	      type: "raw",
	      stream: require('bunyan-logstash').createStream({
	        host: '127.0.0.1',
	        port: 5505,
			levels : levels
	      })
	    }
	  ]
	});

###Example: Leaving the level names as the numeric value

    var levels = {
      10: 10,
      20: 20,
      30: 30,
      40: 40,
      50: 50,
      60: 60
    };

	var log = bunyan.createLogger({
	  streams: [
	    {
	      type: "raw",
	      stream: require('bunyan-logstash').createStream({
	        host: '127.0.0.1',
	        port: 5505,
			levels : levels
	      })
	    }
	  ]
	});

