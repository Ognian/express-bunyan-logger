# Express-bunyan-logger

A express logger middleware powered by [bunyan](https://github.com/trentm/node-bunyan).

[![Build Status](https://travis-ci.org/villadora/express-bunyan-logger.png?branch=master)](https://travis-ci.org/villadora/express-bunyan-logger)


## Installation

    npm install express-bunyan-logger
   
## Usage

To use the logger: 

    app.use(require('express-bunyan-logger')());

To use the errorLogger:

    app.use(require('express-bunyan-logger').errorLogger());

And you can also pass bunyan logger options to the logger middleware:

    app.use(require('express-bunyan-logger')({
        name: 'logger', 
        streams: [{
            level: 'info',
            stream: process.stdout
            }]
        }));

Change default format:

    app.use(require('express-bunyan-logger')({
        format: ":remote-address - :user-agent[major] custom logger"
    });
    

## Configuration

### options.format

Format string, please go the source code to the metadata. ":name" will print out meta.name; ":name[key]" will print out the property 'key' of meta.name.

Or you can pass a function to _options.format_. This function accept a object as argument and return string.

### options.parseUA

Whether to parse _user-agent_ in logger, default is =true=.

### options.levelFn

Function that translate statusCode into log level.

```
function(status, err /* only will work in error logger */) {
     // return string of level
     return "info";
}
```

### options.immediate

Write log line on request instead of response (for response times)

## License

(The BSD License)

    Copyright (c) 2013, Villa.Gao <jky239@gmail.com>;
    All rights reserved.

    Redistribution and use in source and binary forms, with or without
    modification, are permitted provided that the following conditions are met:
    1. Redistributions of source code must retain the above copyright
       notice, this list of conditions and the following disclaimer.
    2. Redistributions in binary form must reproduce the above copyright
       notice, this list of conditions and the following disclaimer in the
       documentation and/or other materials provided with the distribution.
    3. All advertising materials mentioning features or use of this software
       must display the following acknowledgement:
       This product includes software developed by the villa.gao.
    4. Neither the name of the villa.gao nor the
       names of its contributors may be used to endorse or promote products
       derived from this software without specific prior written permission.
                     
    THIS SOFTWARE IS PROVIDED BY <COPYRIGHT HOLDER> ''AS IS'' AND ANY
    EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
    WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
    DISCLAIMED. IN NO EVENT SHALL <COPYRIGHT HOLDER> BE LIABLE FOR ANY
    DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
    (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
    LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
    ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
    (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
    SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
