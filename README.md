# *mxtsight*

*MXTsight* is an open-source Martexcoin blockchain explorer with complete REST and websocket APIs.
MXTsight runs in NodeJS, uses AngularJS for the front-end and LevelDB for storage.

Check some screenshots and more details at [mxtsight's project homepage](https://github.com/martexcoin/mxtsight).

*MXTsight* project is now split in two repositories. One for the [API](https://github.com/martexcoin/mxtsight-api)
and for the front-end. This repository is for the front-end, which will install the API as a NPM dependency.


## Prerequisites

* **Node.js v0.10.x** - Download and Install [Node.js](http://www.nodejs.org/download/).

* **NPM** - Node.js package manager, should be automatically installed when you get Node.js.


## Quick Install
  Check the Prerequisites section above before installing.

  To install mxtsight, clone the main repository:

    $ git clone https://github.com/martexcoin/mxtsight.git && cd mxtsight

  Install dependencies:

    $ npm install
    
  Run the main application:

    $ npm start
    
  Then open a browser and go to:

    http://localhost:3000

  If *mxtsight* reports problems connecting to **martexcoind** please check the CONFIGURATION section of 
  [mxtsight-api README](https://github.com/martexcoin/mxtsight-api/blob/master/README.md). To set the 
  environment variables run something like:
  
     $ INSIGHT_NETWORK=livenet BITCOIND_USER=user BITCOIND_PASS=pass INSIGHT_PUBLIC_PATH=public  npm start


  Please note that the app will need to sync its internal database
  with the blockchain state, which may take some time. You can check
  sync progress from within the web interface. More details about that process
  on [mxtsight-api README](https://github.com/martexcoin/mxtsight-api/blob/master/README.md). 
  
  
## Nginx Setup

To use Nginx as a reverse proxy for mxtsight, use the following base [configuration](https://gist.github.com/matiu/bdd5e55ff0ad90b54261)


## Development

To run mxtsight locally for development mode:

Install bower dependencies:

```
$ bower install
```

To compile and minify the web application's assets:

```
$ grunt compile
```

There is a convenient Gruntfile.js for automation during editing the code

```
$ grunt
```

In case you are developing *mxtsight* and *mxtsight-api* together, you can do the following:

* Install mxtsight and mxtsight-api on the same path ($IROOT)

```
  $ cd $IROOT/mxtsight
  $ grunt
```

in other terminal:

```
  $ cd $IROOT/mxtsight-api
  $ ln -s ../mxtsight/public
  $ INSIGHT_PUBLIC_PATH=public node insight.js 
```


``` 
INSIGHT_PUBLIC_PATH=mxtsight/public  grunt
```

at mxtsight-api's home path (edit the path according your setup).

**also** in the mxtsight-api path. (So you will have to grunt process running, one for mxtsight and one for mxtsight-api).


## Multilanguage support

mxtsight use [angular-gettext](http://angular-gettext.rocketeer.be) for
multilanguage support. 

To enable a text to be translated, add the ***translate*** directive to html tags. See more details [here](http://angular-gettext.rocketeer.be/dev-guide/annotate/). Then, run:

```
grunt compile
```

This action will create a template.pot file in ***po/*** folder. You can open
it with some PO editor ([Poedit](http://poedit.net)). Read this [guide](http://angular-gettext.rocketeer.be/dev-guide/translate/) to learn how to edit/update/import PO files from a generated POT file. PO file will be generated inside po/ folder.

If you make new changes, simply run **grunt compile** again to generate a new .pot template and the angular javascript ***js/translations.js***. Then (if use Poedit), open .po file and choose ***update from POT File*** from **Catalog** menu.

Finally changes your default language from ***public/src/js/config*** 

```
gettextCatalog.currentLanguage = 'es';
```

This line will take a look at any *.po files inside ***po/*** folder, e.g.
**po/es.po**, **po/nl.po**. After any change do not forget to run ***grunt
compile***.


## Note

For more details about the *mxtsight-api* configs and end-point, just go to [mxtsight-api github repository](https://github.com/martexcoin/mxtsight-api) or read the [documentation](https://github.com/martexcoin/mxtsight-api/blob/master/README.md)

## Contribute

Contributions and suggestions are welcomed at [mxtsight github repository](https://github.com/martexcoin/mxtsight).


## License
(The MIT License)

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
