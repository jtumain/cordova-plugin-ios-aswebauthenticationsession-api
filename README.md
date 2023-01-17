## I am no longer making updates to this fork. Please refer to the original repository, or fork this one in order to maintain it.

# cordova-plugin-ios-aswebauthenticationsession-api
Cordova Plugin for iOS 13 ASWebAuthenticationSession API. Originally forked from [https://github.com/jwelker110/cordova-plugin-ios-aswebauthenticationsession-api](https://github.com/jwelker110/cordova-plugin-ios-aswebauthenticationsession-api).

This fork clears the session before starting a new one. So each time the user attempts to login, they should be presented with a login screen, rather than the session being remembered. This was achieved by setting "prefersEphemeralWebBrowserSession" to true, before starting the ASWebAuthSession.

## usage
    window.plugins.ASWebAuthSession.start("myappurlscheme", 'https://api.auth.com/authenticate',
    function(msg){
      console.log("Success ", msg);
    }, function (err) {
        console.log("Error " + msg);
    });

#### Additional information

iOS 13 introduced a requirement that ASWebAuthenticationSession needs a [presentationContextProvider](https://developer.apple.com/documentation/authenticationservices/aswebauthenticationsession/3237232-presentationcontextprovider) to provide a "display context in which the system can present an authentication session to the user."

The changes in this plugin should address an error that was thrown when trying to use ASWebAuthenticationSession after updating to iOS 13:
"Cannot start ASWebAuthenticationSession without providing presentation context. Set presentationContextProvider before calling -start."
