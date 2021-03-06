[![Build Status](https://travis-ci.org/itsthejb/JCKeyPathValidator.svg?branch=master)](https://travis-ci.org/itsthejb/JCKeyPathValidator)
[![Build Status](https://travis-ci.org/itsthejb/JCKeyPathValidator.svg?branch=develop)](https://travis-ci.org/itsthejb/JCKeyPathValidator)

JCKeyPathValidator
==================

*Stop using constant NSStrings to represent your keypaths: use compiler symbols instead.*

##Intro

Super simple extension to Justin Spahr-Summers' [object key path validation macro](https://gist.github.com/jspahrsummers/1670404) that adds a macro for validating key paths without requiring an instance of the class.

Particularly useful for removing constant `NSStrings` from your API mappings.

##Usage

* `JCValidateKeyPath(anObject, aKeyPath)`
	* The original macro. Validates the specified key path as a compiler symbol and returns an equivalent `NSString` representation.
					
* `JCValidateKeyPathWithClass(aClass, aKeyPath)`
	* As an extension of the above, does not require an object instance, and can use a `Class` directly.
	
**Examples:**

    // With a local instance
    NSString *stringInstance = nil;
    JCValidateKeyPath(stringInstance, length);
    
    // Without a local instance
    JCValidateKeyPathWithClass(NSString, length)

Note that as of v1.0.1 you ***cannot*** use `JCValidateKeyPathWithClass([NSString class], length)`. Instead you must use the class symbol directly.

##Version history

**v1.1.0**

Cache now removed and functionality entirely implemented with macros. Many thanks to [Stepan Hruda](https://github.com/stepanhruda) for this.

**v1.0.2**

General spring-clean and Travis configuration.

**v1.0.1**

Now casting the object returned from the cache. Without this, class validation wasn't actually correctly working; you could use any valid selector from any class.

**v1.0.0**

Initial release.

Have fun!
---------

[MIT Licensed](http://jc.mit-license.org/) >> [jon.crooke@gmail.com](mailto:jon.crooke@gmail.com)