# Ember CLI

As for Ember, read [the Ember CLI guide](http://www.ember-cli.com/) 2 or 3 times. Every time you'll spot something that you didn't fully understand the previous time.


### Development

#### Load resources from different servers

Sometimes you need to poll an external API, or load a script from a third-party CDN.

Ember CLI comes bundled with the [`ember-cli-content-security-policy`](https://github.com/rwjblue/ember-cli-content-security-policy) addon which enables the Content Security Policy in modern browsers when running the development server.

Here is an example of configuration you can add to your `environment/config.js` file:

```
module.exports = function(environment) {
    var ENV = {
        ...

        contentSecurityPolicy: {
            'default-src': "'none'",
            'script-src': "'self' https://cdn.mxpnl.com", // Allow scripts from https://cdn.mxpnl.com
            'font-src': "'self' http://fonts.gstatic.com", // Allow fonts to be loaded from http://fonts.gstatic.com
            'connect-src': "'self' https://api.mixpanel.com http://custom-api.local", // Allow data (ajax/websocket) from api.mixpanel.com and custom-api.local
            'img-src': "'self'",
            'style-src': "'self' 'unsafe-inline' http://fonts.googleapis.com", // Allow inline styles and loaded CSS from http://fonts.googleapis.com 
            'media-src': "'self'"
        }
    };
```

More information at [`ember-cli-content-security-policy repository`](https://github.com/rwjblue/ember-cli-content-security-policy).


### Windows

Ember CLI can make your Windows machine a little bit busy while building and watching files. To improve performance of `ember build` and `ember serve` commands you can use the tool [`ember-cli-windows`](https://github.com/felixrieseberg/ember-cli-windows) on Github (by Microsoft).

Alternatively, you can manually disable the `tmp` folder of your project repository from both [Windows Defender](http://answers.microsoft.com/en-us/protect/wiki/protect_defender-protect_scanning/how-to-exclude-a-filefolder-from-windows-defender/f32ee18f-a012-4f02-8611-0737570e8eee) and [Windows Search Index](http://windows.microsoft.com/en-us/windows/improve-windows-searches-using-index-faq#1TC=windows-7).

I personally exluded the whole project repository folder from both Windows tools, since I don't really take advantage of neither one.