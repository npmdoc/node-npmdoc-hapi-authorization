# api documentation for  [hapi-authorization (v3.0.2)](https://github.com/toymachiner62/hapi-authorization)  [![npm package](https://img.shields.io/npm/v/npmdoc-hapi-authorization.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-hapi-authorization) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-hapi-authorization.svg)](https://travis-ci.org/npmdoc/node-npmdoc-hapi-authorization)
#### ACL support for hapijs apps

[![NPM](https://nodei.co/npm/hapi-authorization.png?downloads=true)](https://www.npmjs.com/package/hapi-authorization)

[![apidoc](https://npmdoc.github.io/node-npmdoc-hapi-authorization/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-hapi-authorization_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-hapi-authorization/build/apidoc.html)

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
            "email": "asafdav@gmail.com",
            "url": "http://about.me/asafdavid"
        },
        {
            "name": "Tom Caflisch",
            "email": "tomcaflisch@gmail.com",
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
            "name": "toymachiner62",
            "email": "tomcaflisch@gmail.com"
        }
    ],
    "name": "hapi-authorization",
    "optionalDependencies": {},
    "peerDependencies": {
        "hapi": ">= 8"
    },
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module hapi-authorization](#apidoc.module.hapi-authorization)
1.  [function <span class="apidocSignatureSpan">hapi-authorization.</span>register (server, options, next)](#apidoc.element.hapi-authorization.register)
1.  object <span class="apidocSignatureSpan">hapi-authorization.</span>acl
1.  object <span class="apidocSignatureSpan">hapi-authorization.</span>schema

#### [module hapi-authorization.acl](#apidoc.module.hapi-authorization.acl)
1.  [function <span class="apidocSignatureSpan">hapi-authorization.acl.</span>checkRoles (user, role, hierarchy)](#apidoc.element.hapi-authorization.acl.checkRoles)
1.  [function <span class="apidocSignatureSpan">hapi-authorization.acl.</span>fetchEntity (query, param, request, cb)](#apidoc.element.hapi-authorization.acl.fetchEntity)
1.  [function <span class="apidocSignatureSpan">hapi-authorization.acl.</span>validateEntityAcl (user, role, entity, validator, options)](#apidoc.element.hapi-authorization.acl.validateEntityAcl)

#### [module hapi-authorization.schema](#apidoc.module.hapi-authorization.schema)
1.  [function <span class="apidocSignatureSpan">hapi-authorization.schema.</span>assert (type, options, message)](#apidoc.element.hapi-authorization.schema.assert)



# <a name="apidoc.module.hapi-authorization"></a>[module hapi-authorization](#apidoc.module.hapi-authorization)

#### <a name="apidoc.element.hapi-authorization.register"></a>[function <span class="apidocSignatureSpan">hapi-authorization.</span>register (server, options, next)](#apidoc.element.hapi-authorization.register)
- description and source-code
```javascript
register = function (server, options, next) {

	try {
		// Validate the options passed into the plugin
		Schema.assert('plugin', options, 'Invalid settings');

		var settings = Hoek.applyToDefaults(internals.defaults, options || {});

		server.bind({
			config: settings
		});

		// Validate the server options on the routes
		if (server.after) { // Support for hapi < 11
			server.after(internals.validateRoutes);
		} else {
			server.ext('onPreStart', internals.validateRoutes);
		}
		server.ext('onPreHandler', internals.onPreHandler);

		next();
	} catch (e) {

		next(e);
	}
}
```
- example usage
```shell
...
		register: require('hapi-authorization')
		options: {
		  roles: false	// By setting to false, you are not using an authorization hierarchy and you do not need to specify all the potential
 roles here
		}
	}
];

server.register(plugins, function(err) {
...
'''

## Using hapi-authorization with custom roles
1. Include the plugin in your hapijs app.
Example:
'''js
...
```



# <a name="apidoc.module.hapi-authorization.acl"></a>[module hapi-authorization.acl](#apidoc.module.hapi-authorization.acl)

#### <a name="apidoc.element.hapi-authorization.acl.checkRoles"></a>[function <span class="apidocSignatureSpan">hapi-authorization.acl.</span>checkRoles (user, role, hierarchy)](#apidoc.element.hapi-authorization.acl.checkRoles)
- description and source-code
```javascript
checkRoles = function (user, role, hierarchy) {

	if ((!user) || (!internals.isGranted(user.role, role, hierarchy))) {
		return Boom.forbidden('Unauthorized');
	}

	return null;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.hapi-authorization.acl.fetchEntity"></a>[function <span class="apidocSignatureSpan">hapi-authorization.acl.</span>fetchEntity (query, param, request, cb)](#apidoc.element.hapi-authorization.acl.fetchEntity)
- description and source-code
```javascript
fetchEntity = function (query, param, request, cb) {

	var def = Q.defer();
	query(param, request, function(err, entity) {

		if (err && err.isBoom) {
			return def.reject(err);
		} else if (err) {
			return def.reject(Boom.badRequest('Bad Request', err));
		}
		else if (!entity) {
			return def.reject(Boom.notFound());
		}
		else {
			def.resolve(entity);
		}
	});

	return def.promise;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.hapi-authorization.acl.validateEntityAcl"></a>[function <span class="apidocSignatureSpan">hapi-authorization.acl.</span>validateEntityAcl (user, role, entity, validator, options)](#apidoc.element.hapi-authorization.acl.validateEntityAcl)
- description and source-code
```javascript
validateEntityAcl = function (user, role, entity, validator, options) {

	var def = Q.defer();

	if (!entity) {
		def.reject(new Error('validateUserACL must run after fetchACLEntity'));
	} else if (!user) {
		def.reject(new Error('User is required, please make sure this method requires authentication'));
	} else {

		if (validator) {

			entity[validator](user, role, function(err, isValid) {

				if (err) {
					def.reject(new Error(err));
				} else if (!isValid) {	// Not granted
					def.reject(Boom.forbidden('Unauthorized'));
				} else {	// Valid
					def.resolve(isValid);
				}
			});
		} else {
			// Use the default validator
			var isValid = internals.defaultEntityAclValidator(user, role, entity, options);

			if (isValid) {
				def.resolve(isValid);
			} else {
				def.reject(Boom.forbidden('Unauthorized'));
			}
		}
	}

	return def.promise;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.hapi-authorization.schema"></a>[module hapi-authorization.schema](#apidoc.module.hapi-authorization.schema)

#### <a name="apidoc.element.hapi-authorization.schema.assert"></a>[function <span class="apidocSignatureSpan">hapi-authorization.schema.</span>assert (type, options, message)](#apidoc.element.hapi-authorization.schema.assert)
- description and source-code
```javascript
assert = function (type, options, message) {

	var validationObj = Joi.validate(options, internals[type]);
	var error = validationObj.error;
	var errorMessage = null;

	// If there is an error, build a nice error message
	if(error) {
		errorMessage = error.name + ':';
		error.details.forEach(function(err) {
			errorMessage += ' ' + err.message;
		});
	}

	// If there is an error build the error message
	Hoek.assert(!error, 'Invalid', type, 'options', message ? '(' + message + ')' : '', errorMessage);

	return validationObj.value;
}
```
- example usage
```shell
...
		errorMessage = error.name + ':';
		error.details.forEach(function(err) {
			errorMessage += ' ' + err.message;
		});
	}

	// If there is an error build the error message
	Hoek.assert(!error, 'Invalid', type, 'options', message ? '(' + message + ')' : '', errorMessage);

	return validationObj.value;
};


/**
* Validation rules for a route's params
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
