# Encode and decode Tender Multipass tokens

This project is based on a fork of the Tender node multipass implementation by David Wood, which can be found at https://github.com/davidwood/node-multipass.  UserVoice uses a multipass implementation that is very similar to Tender (and likely one is based on the other) except that the encryption algorithm is slightly different.

## Installation
<pre>
    npm install uservoice
</pre>

## Usage

UserVoice multipass is constructed with two arguments: an API key and a site key.  These keys can be found within the Tender admin (Accounts & Settings > Extras > Single Sign-On).

``` js
  var Multipass = require('uservoice');

  // Construct the Multipass encoder / decoder
  var uservoice = new Multipass('API-KEY', 'SITE-KEY');

  // Encode a Multipass token
  var token = uservoice.encode({ email: 'test@example.com', display_name: 'test', guid: 'abc123' });

  // Decode a Multipass token
  var obj = uservoice.decode(token);
```

### encode(obj)

This function encodes the required `obj` argument.  This argument is a JavaScript object and contains the data that you want to pass to Tender.  A list of expected keys can be found [here](https://help.tenderapp.com/kb/setup-installation/share-your-own-sites-authentication-with-tender).

This function will return a string.  If an error occurs, the `undefined` will be returned.

### decode(token)

This function decodes the required `token` argument.  This argument is an encoded Multipass token and a JavaScript object is returned.  If decoding is not successful, `undefined` is returned.

