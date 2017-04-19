# npmdoc-hapi-authorization

#### api documentation for  [hapi-authorization (v3.0.2)](https://github.com/toymachiner62/hapi-authorization)  [![npm package](https://img.shields.io/npm/v/npmdoc-hapi-authorization.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-hapi-authorization) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-hapi-authorization.svg)](https://travis-ci.org/npmdoc/node-npmdoc-hapi-authorization)

#### ACL support for hapijs apps

[![NPM](https://nodei.co/npm/hapi-authorization.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/hapi-authorization)

- [https://npmdoc.github.io/node-npmdoc-hapi-authorization/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-hapi-authorization/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-hapi-authorization/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-hapi-authorization/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-hapi-authorization/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-hapi-authorization/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "bugs": {
        "url": "https://github.com/toymachiner62/hapi-authorization/issues"
    },
    "contributors": [
        {
            "name": "Asaf David",
            "url": "http://about.me/asafdavid"
        },
        {
            "name": "Tom Caflisch",
            "url": "https://github.com/toymachiner62"
        }
    ],
    "dependencies": {
        "boom": "^3.0.0",
        "hoek": "^3.0.4",
        "joi": "^7.0.1",
        "q": "^1.0.1",
        "underscore": "^1.7.0"
    },
    "description": "ACL support for hapijs apps",
    "devDependencies": {
        "chai": "^3.4.1",
        "coveralls": "^2.11.6",
        "hapi": "^11.1.2",
        "istanbul": "^0.4.1",
        "jscoverage": "^0.6.0",
        "mocha": "^2.3.4"
    },
    "directories": {},
    "dist": {
        "shasum": "a2b01d56c1e7d5cfbfbb20f565cad59ab27dbd69",
        "tarball": "https://registry.npmjs.org/hapi-authorization/-/hapi-authorization-3.0.2.tgz"
    },
    "engines": {
        "node": ">=4.0.0"
    },
    "gitHead": "f645daed3f700ad4df0cf87c86e272115bf43c15",
    "homepage": "https://github.com/toymachiner62/hapi-authorization",
    "keywords": [
        "hapi",
        "auth",
        "authorization",
        "acl"
    ],
    "license": "ISC",
    "main": "index.js",
    "maintainers": [
        {
            "name": "toymachiner62"
        }
    ],
    "name": "hapi-authorization",
    "optionalDependencies": {},
    "peerDependencies": {
        "hapi": ">= 8"
    },
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/toymachiner62/hapi-authorization.git"
    },
    "scripts": {
        "coverage": "istanbul cover _mocha test; cat ./coverage/lcov.info | coveralls",
        "test": "mocha test"
    },
    "version": "3.0.2"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
