# api documentation for  [memoizee (v0.4.4)](https://github.com/medikoo/memoizee#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-memoizee.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-memoizee) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-memoizee.svg)](https://travis-ci.org/npmdoc/node-npmdoc-memoizee)
#### Memoize/cache function results

[![NPM](https://nodei.co/npm/memoizee.png?downloads=true)](https://www.npmjs.com/package/memoizee)

[![apidoc](https://npmdoc.github.io/node-npmdoc-memoizee/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-memoizee_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-memoizee/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-memoizee/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-memoizee/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Mariusz Nowak",
        "email": "medikoo@medikoo.com",
        "url": "http://www.medikoo.com/"
    },
    "bugs": {
        "url": "https://github.com/medikoo/memoizee/issues"
    },
    "dependencies": {
        "d": "1",
        "es5-ext": "^0.10.13",
        "es6-weak-map": "^2.0.1",
        "event-emitter": "^0.3.4",
        "is-promise": "^2.1",
        "lru-queue": "0.1",
        "next-tick": "1",
        "timers-ext": "0.1"
    },
    "description": "Memoize/cache function results",
    "devDependencies": {
        "plain-promise": "^0.1.1",
        "tad": "^0.2.7",
        "xlint": "^0.2.2",
        "xlint-jslint-medikoo": "^0.1.4"
    },
    "directories": {},
    "dist": {
        "shasum": "ecf4b791a09cd11c970203f80682534730fad78f",
        "tarball": "https://registry.npmjs.org/memoizee/-/memoizee-0.4.4.tgz"
    },
    "gitHead": "98d1eaf6f88f3de6da3309bfb91bddad9a471a1a",
    "homepage": "https://github.com/medikoo/memoizee#readme",
    "keywords": [
        "memoize",
        "memoizer",
        "cache",
        "memoization",
        "memo",
        "memcached",
        "hashing.",
        "storage",
        "caching",
        "memory",
        "gc",
        "weak",
        "garbage",
        "collector",
        "async"
    ],
    "license": "MIT",
    "maintainers": [
        {
            "name": "medikoo",
            "email": "medikoo+npm@medikoo.com"
        }
    ],
    "name": "memoizee",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/medikoo/memoizee.git"
    },
    "scripts": {
        "lint": "npm run lint-medikoo -- --no-cache --no-stream",
        "lint-console": "npm run lint-medikoo -- --watch",
        "lint-medikoo": "xlint --linter=node_modules/xlint-jslint-medikoo/index.js",
        "test": "tad"
    },
    "version": "0.4.4"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module memoizee](#apidoc.module.memoizee)
1.  object <span class="apidocSignatureSpan">memoizee.</span>profile
1.  object <span class="apidocSignatureSpan">memoizee.</span>registered_extensions

#### [module memoizee.profile](#apidoc.module.memoizee.profile)
1.  [function <span class="apidocSignatureSpan">memoizee.profile.</span>log ()](#apidoc.element.memoizee.profile.log)
1.  object <span class="apidocSignatureSpan">memoizee.profile.</span>statistics

#### [module memoizee.registered_extensions](#apidoc.module.memoizee.registered_extensions)
1.  [function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>async (tbi, conf)](#apidoc.element.memoizee.registered_extensions.async)
1.  [function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>dispose (dispose, conf, options)](#apidoc.element.memoizee.registered_extensions.dispose)
1.  [function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>max (max, conf, options)](#apidoc.element.memoizee.registered_extensions.max)
1.  [function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>maxAge (maxAge, conf, options)](#apidoc.element.memoizee.registered_extensions.maxAge)
1.  [function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>promise (mode, conf)](#apidoc.element.memoizee.registered_extensions.promise)
1.  [function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>refCounter (ignore, conf, options)](#apidoc.element.memoizee.registered_extensions.refCounter)



# <a name="apidoc.module.memoizee"></a>[module memoizee](#apidoc.module.memoizee)



# <a name="apidoc.module.memoizee.profile"></a>[module memoizee.profile](#apidoc.module.memoizee.profile)

#### <a name="apidoc.element.memoizee.profile.log"></a>[function <span class="apidocSignatureSpan">memoizee.profile.</span>log ()](#apidoc.element.memoizee.profile.log)
- description and source-code
```javascript
log = function () {
	var initial, cached, ordered, ipad, cpad, ppad, toPrc, log;

	initial = cached = 0;
	ordered = [];

	toPrc = function (initial, cached) {
		if (!initial && !cached) {
			return '0.00';
		}
		return ((cached / (initial + cached)) * 100).toFixed(2);
	};

	log = "------------------------------------------------------------\n";
	log += "Memoize statistics:\n\n";

	forEach(stats, function (data, name) {
		initial += data.initial;
		cached += data.cached;
		ordered.push([name, data]);
	}, null, function (a, b) {
		return (this[b].initial + this[b].cached) -
			(this[a].initial + this[a].cached);
	});

	ipad = partial.call(pad, " ",
		max(String(initial).length, "Init".length));
	cpad = partial.call(pad, " ", max(String(cached).length, "Cache".length));
	ppad = partial.call(pad, " ", "%Cache".length);
	log += ipad.call("Init") + "  " +
		cpad.call("Cache") + "  " +
		ppad.call("%Cache") + "  Source location\n";
	log += ipad.call(initial) + "  " +
		cpad.call(cached) + "  " +
		ppad.call(toPrc(initial, cached)) + "  (all)\n";
	ordered.forEach(function (data) {
		var name = data[0];
		data = data[1];
		log += ipad.call(data.initial) + "  " +
			cpad.call(data.cached) + "  " +
			ppad.call(toPrc(data.initial, data.cached)) + "  " + name + "\n";
	});
	log += "------------------------------------------------------------\n";
	return log;
}
```
- example usage
```shell
...
var memProfile = require('memoizee/profile');
'''

Access statistics at any time:

'''javascript
memProfile.statistics;         // Statistcs accessible for programmatical use
console.log(memProfile.log()); // Output statistics data in readable form
'''

Example console output:

'''
------------------------------------------------------------
Memoize statistics:
...
```



# <a name="apidoc.module.memoizee.registered_extensions"></a>[module memoizee.registered_extensions](#apidoc.module.memoizee.registered_extensions)

#### <a name="apidoc.element.memoizee.registered_extensions.async"></a>[function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>async (tbi, conf)](#apidoc.element.memoizee.registered_extensions.async)
- description and source-code
```javascript
async = function (tbi, conf) {
	var waiting = create(null), cache = create(null)
	  , base = conf.memoized, original = conf.original
	  , currentCallback, currentContext, currentArgs;

	// Initial
	conf.memoized = defineLength(function (arg) {
		var args = arguments, last = args[args.length - 1];
		if (typeof last === 'function') {
			currentCallback = last;
			args = slice.call(args, 0, -1);
		}
		return base.apply(currentContext = this, currentArgs = args);
	}, base);
	try { mixin(conf.memoized, base); } catch (ignore) {}

	// From cache (sync)
	conf.on('get', function (id) {
		var cb, context, args;
		if (!currentCallback) return;

		// Unresolved
		if (waiting[id]) {
			if (typeof waiting[id] === 'function') waiting[id] = [waiting[id], currentCallback];
			else waiting[id].push(currentCallback);
			currentCallback = null;
			return;
		}

		// Resolved, assure next tick invocation
		cb = currentCallback;
		context = currentContext;
		args = currentArgs;
		currentCallback = currentContext = currentArgs = null;
		nextTick(function () {
			var data;
			if (hasOwnProperty.call(cache, id)) {
				data = cache[id];
				conf.emit('getasync', id, args, context);
				apply.call(cb, data.context, data.args);
			} else {
				// Purged in a meantime, we shouldn't rely on cached value, recall
				currentCallback = cb;
				currentContext = context;
				currentArgs = args;
				base.apply(context, args);
			}
		});
	});

	// Not from cache
	conf.original = function () {
		var args, cb, origCb, result;
		if (!currentCallback) return apply.call(original, this, arguments);
		args = aFrom(arguments);
		cb = function self(err) {
			var cb, args, id = self.id;
			if (id == null) {
				// Shouldn't happen, means async callback was called sync way
				nextTick(apply.bind(self, this, arguments));
				return;
			}
			delete self.id;
			cb = waiting[id];
			delete waiting[id];
			if (!cb) {
				// Already processed,
				// outcome of race condition: asyncFn(1, cb), asyncFn.clear(), asyncFn(1, cb)
				return;
			}
			args = aFrom(arguments);
			if (conf.has(id)) {
				if (err) {
					conf.delete(id);
				} else {
					cache[id] = { context: this, args: args };
					conf.emit('setasync', id, (typeof cb === 'function') ? 1 : cb.length);
				}
			}
			if (typeof cb === 'function') {
				result = apply.call(cb, this, args);
			} else {
				cb.forEach(function (cb) { result = apply.call(cb, this, args); }, this);
			}
			return result;
		};
		origCb = currentCallback;
		currentCallback = currentContext = currentArgs = null;
		args.push(cb);
		result = apply.call(original, this, args);
		cb.cb = origCb;
		currentCallback = cb;
		return result;
	};

	// After not from cache call
	conf.on('set', function (id) {
		if (!currentCallback) {
			conf.delete(id);
			return;
		}
		if (waiting[id]) {
			// Race condition: asyncFn(1, cb), asyncFn.clear(), asyncFn(1, cb)
			if (typeof waiting[id] === 'function') waiting[id] = [waiting[id], currentCallback.cb];
			else waiting[id].push(currentCallback.cb);
		} else {
			waiting[id] = currentCallback.cb;
		}
		delete currentCallback.cb;
		currentCallback.id = id;
		currentCallback = null;
	});

	// On delete
	conf.on('delete', function (id) {
		var result;
		// If false, we don't have value yet, so we assume that intention is not
		// to memoize this call. After value is obtained we don't cache it but
		// gracefully pass to callback
		if (hasOwnProperty.call(waiting, id)) return;
		if (!cache[id]) return;
		result = cache[id];
		delete cache[id];
		conf.emit('deleteasync', id, slice.call(result.args, 1));
	});

	// On clear
	conf.on('clear', function () {
		var oldCache = cache;
		cache = create(null);
		conf.emit('clearasync', objectMap(oldCache, function (data) {
			return slice.call(data.args, 1);
		}));
	});
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.memoizee.registered_extensions.dispose"></a>[function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>dispose (dispose, conf, options)](#apidoc.element.memoizee.registered_extensions.dispose)
- description and source-code
```javascript
dispose = function (dispose, conf, options) {
	var del;
	callable(dispose);
	if ((options.async && extensions.async) || (options.promise && extensions.promise)) {
		conf.on('deleteasync', del = function (id, resultArray) {
			apply.call(dispose, null, resultArray);
		});
		conf.on('clearasync', function (cache) {
			forEach(cache, function (result, id) { del(id, result); });
		});
		return;
	}
	conf.on('delete', del = function (id, result) { dispose(result); });
	conf.on('clear', function (cache) {
		forEach(cache, function (result, id) { del(id, result); });
	});
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.memoizee.registered_extensions.max"></a>[function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>max (max, conf, options)](#apidoc.element.memoizee.registered_extensions.max)
- description and source-code
```javascript
max = function (max, conf, options) {
	var postfix, queue, hit;

	max = toPosInteger(max);
	if (!max) return;

	queue = lruQueue(max);
	postfix = ((options.async && extensions.async) || (options.promise && extensions.promise))
		? 'async' : '';

	conf.on('set' + postfix, hit = function (id) {
		id = queue.hit(id);
		if (id === undefined) return;
		conf.delete(id);
	});
	conf.on('get' + postfix, hit);
	conf.on('delete' + postfix, queue.delete);
	conf.on('clear' + postfix, queue.clear);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.memoizee.registered_extensions.maxAge"></a>[function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>maxAge (maxAge, conf, options)](#apidoc.element.memoizee.registered_extensions.maxAge)
- description and source-code
```javascript
maxAge = function (maxAge, conf, options) {
	var timeouts, postfix, preFetchAge, preFetchTimeouts;

	maxAge = timeout(maxAge);
	if (!maxAge) return;

	timeouts = create(null);
	postfix = ((options.async && extensions.async) || (options.promise && extensions.promise))
		? 'async' : '';
	conf.on('set' + postfix, function (id) {
		timeouts[id] = setTimeout(function () { conf.delete(id); }, maxAge);
		if (!preFetchTimeouts) return;
		if (preFetchTimeouts[id]) {
			if (preFetchTimeouts[id] !== 'nextTick') clearTimeout(preFetchTimeouts[id]);
		}
		preFetchTimeouts[id] = setTimeout(function () {
			delete preFetchTimeouts[id];
		}, preFetchAge);
	});
	conf.on('delete' + postfix, function (id) {
		clearTimeout(timeouts[id]);
		delete timeouts[id];
		if (!preFetchTimeouts) return;
		if (preFetchTimeouts[id] !== 'nextTick') clearTimeout(preFetchTimeouts[id]);
		delete preFetchTimeouts[id];
	});

	if (options.preFetch) {
		if ((options.preFetch === true) || isNaN(options.preFetch)) {
			preFetchAge = 0.333;
		} else {
			preFetchAge = max(min(Number(options.preFetch), 1), 0);
		}
		if (preFetchAge) {
			preFetchTimeouts = {};
			preFetchAge = (1 - preFetchAge) * maxAge;
			conf.on('get' + postfix, function (id, args, context) {
				if (!preFetchTimeouts[id]) {
					preFetchTimeouts[id] = 'nextTick';
					nextTick(function () {
						var result;
						if (preFetchTimeouts[id] !== 'nextTick') return;
						delete preFetchTimeouts[id];
						conf.delete(id);
						if (options.async) {
							args = aFrom(args);
							args.push(noop);
						}
						result = conf.memoized.apply(context, args);
						if (options.promise) {
							// Supress eventual error warnings
							if (isPromise(result)) {
								if (typeof result.done === 'function') result.done(noop, noop);
								else result.then(noop, noop);
							}
						}
					});
				}
			});
		}
	}

	conf.on('clear' + postfix, function () {
		forEach(timeouts, function (id) { clearTimeout(id); });
		timeouts = {};
		if (preFetchTimeouts) {
			forEach(preFetchTimeouts, function (id) {
				if (id !== 'nextTick') clearTimeout(id);
			});
			preFetchTimeouts = {};
		}
	});
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.memoizee.registered_extensions.promise"></a>[function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>promise (mode, conf)](#apidoc.element.memoizee.registered_extensions.promise)
- description and source-code
```javascript
promise = function (mode, conf) {
	var waiting = create(null), cache = create(null), promises = create(null);

	// After not from cache call
	conf.on('set', function (id, ignore, promise) {
		var isFailed = false;

		if (!isPromise(promise)) {
			// Non promise result
			cache[id] = promise;
			conf.emit('setasync', id, 1);
			return;
		}
		waiting[id] = 1;
		promises[id] = promise;
		var onSuccess = function (result) {
			var count = waiting[id];
			if (isFailed) {
				throw new Error("Memoizee error: Promise resolved with both failure and success," +
					" this can be result of unordered done & finally resolution.\n" +
					"Instead of 'promise: true' consider configuring memoization via 'promise: 'then'' or " +
					"'promise: 'done'");
			}
			if (!count) return; // deleted from cache before resolved
			delete waiting[id];
			cache[id] = result;
			conf.emit('setasync', id, count);
		};
		var onFailure = function () {
			isFailed = true;
			if (!waiting[id]) return; // deleted from cache (or succeed in case of finally)
			delete waiting[id];
			delete promises[id];
			conf.delete(id);
		};

		if ((mode !== 'then') && (typeof promise.done === 'function')) {
			// Optimal promise resolution
			if ((mode !== 'done') && (typeof promise.finally === 'function')) {
				// Use 'finally' to not register error handling (still proper behavior is subject to
				// used implementation, if library throws unconditionally even on handled errors
				// switch to 'then' mode)
				promise.done(onSuccess);
				promise.finally(onFailure);
			} else {
				// With no 'finally' side effect is that it mutes any eventual
				// "Unhandled error" events on returned promise
				promise.done(onSuccess, onFailure);
			}
		} else {
			// With no 'done' it's best we can do.
			// Side effect is that it mutes any eventual "Unhandled error" events on returned promise
			promise.then(function (result) {
				nextTick(onSuccess.bind(this, result));
			}, function () {
				nextTick(onFailure);
			});
		}
	});

	// From cache (sync)
	conf.on('get', function (id, args, context) {
		var promise;
		if (waiting[id]) {
			++waiting[id]; // Still waiting
			return;
		}
		promise = promises[id];
		var emit = function () { conf.emit('getasync', id, args, context); };
		if (isPromise(promise)) {
			if (typeof promise.done === 'function') promise.done(emit);
			else promise.then(function () { nextTick(emit); });
		} else {
			emit();
		}
	});

	// On delete
	conf.on('delete', function (id) {
		delete promises[id];
		if (waiting[id]) {
			delete waiting[id];
			return; // Not yet resolved
		}
		if (!hasOwnProperty.call(cache, id)) return;
		var result = cache[id];
		delete cache[id];
		conf.emit('deleteasync', id, [result]);
	});

	// On clear
	conf.on('clear', function () {
		var oldCache = cache;
		cache = create(null);
		waiting = create(null);
		promises = create(null);
		conf.emit('clearasync', objectMap(oldCache, function (data) { return [data]; }));
	});
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.memoizee.registered_extensions.refCounter"></a>[function <span class="apidocSignatureSpan">memoizee.registered_extensions.</span>refCounter (ignore, conf, options)](#apidoc.element.memoizee.registered_extensions.refCounter)
- description and source-code
```javascript
refCounter = function (ignore, conf, options) {
	var cache, postfix;

	cache = create(null);
	postfix = ((options.async && extensions.async) || (options.promise && extensions.promise))
		? 'async' : '';

	conf.on('set' + postfix, function (id, length) { cache[id] = length || 1; });
	conf.on('get' + postfix, function (id) { ++cache[id]; });
	conf.on('delete' + postfix, function (id) { delete cache[id]; });
	conf.on('clear' + postfix, function () { cache = {}; });

	defineProperties(conf.memoized, {
		deleteRef: d(function () {
			var id = conf.get(arguments);
			if (id === null) return null;
			if (!cache[id]) return null;
			if (!--cache[id]) {
				conf.delete(id);
				return true;
			}
			return false;
		}),
		getRefCount: d(function () {
			var id = conf.get(arguments);
			if (id === null) return 0;
			if (!cache[id]) return 0;
			return cache[id];
		})
	});
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
