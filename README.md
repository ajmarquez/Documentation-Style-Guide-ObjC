# Objective-C Documenting Style Guide
## (or Can I comment this, objective-Cly?)


###1.- ABOUT THE STYLE GUIDE

  In order to create a good documentation of the work in iOS the following Style guide is created, the first rule to follow
  on a good documentation is the use of comments at the right times.

  First we will create this comments using the approach `/*! - */` since this one is recognize by Documentation parsing software
  and also by XCode. For example:


   **EXAMPLE 1.0.1**

```
    /*!
        Hi, I'm a nice piece of code
     */
```
  The documentation starts with a `/*!` then a break line, and the next line of comment will be spaced by a TAB. Comment will close  with `*/`

####1.1.- WHEN TO USE THE COMMENTS

  Comments will be added on the following times:
  * At the a Class header before the interface call (See 2.1)
  * At certain public properties that are needed to explain to the user (See 2.2)
  * Always methods will be documented, explaining briefly its function, arguments, return and any other help needed (See 2.3)
  * Inside the .m body we will use a particular notation in order to express important information that must be knowned or also
      any bonus or easter egg inside the code (Yeah, this doesn't have to be boring). Also runtime helping code or call to console must be identified (See 2.4)

###2.- HOW TO DOCUMENT YOUR CODE AND DON'T DIE TRYING

  Ok... XCode has this pretty cool feature that it read several tags and add them to the methods, classes and properties as help. This
  may also be retrieved by some software that currently hasn't been chosen but it's good to be prepared for when the time comes.

####2.1.- CLASS DOCUMENTATION

  There are several tags to be used on a Class, there are not restrictions of how many may be used, but we will choose as MANDATORY (Watch out,
  I just used Caps!) the following: @header, @class, @brief, @discussion, @author. Here's an example:

  *EXAMPLE 2.1.1*
```
  /*!
    @header ViewController.h

    @brief This is the header file where my super-code is contained.

    This file contains the most important method and properties declaration. It's parted by two methods in total, which can be used to perform
    time travels.

    @author Dr.Brown
    @version    15.12.7
  */
```
 In this case it's added the `@version` tag. But this one will be considered as optional. See the fancy thing I did there with the //'s' and --'s?
 Well you can do that too, to separate diferent parts of the code if you will. Let's say you have a long method (they shouldn't be that long but
 for the sakes of the explanation let's keep at it). in order to help to you fellow Developers and mainly your Future self, the division of code
 stages are recommended.

 Now let's go to a second example. This one is another class definition.

 **EXAMPLE 2.2.2**
```
 /*!
    @class ViewController

    @brief The ViewController class

    @discussion    This class was designed and implemented to help people covert temperatures between the Fahrenheit and Celsius scales.

    @superclass SuperClass: UIViewController\n
    @classdesign    No special design is applied here.
    @coclass    AppDelegate
    @helps It helps no other classes.
    @helper    No helper exists for this class.
 */
```
 This one uses another bunch of tags. Most of them optional, but in this particular case @classdesign MUST be filled if applies.

 When OUTSIDE a method we will use the following format in order to explain or datail it, for example (From AFNEtworking):

**EXAMPLE 2.2.3**
 ```
 /**
 *  A workaround for issues related to key-value observing the `state` of an `NSURLSessionTask`.
 *
 *  See:
 *  - https://github.com/AFNetworking/AFNetworking/issues/1477
 *  - https://github.com/AFNetworking/AFNetworking/issues/2638
 *  - https://github.com/AFNetworking/AFNetworking/pull/2702
 */

static inline void af_swizzleSelector(Class class, SEL originalSelector, SEL swizzledSelector) {
    Method originalMethod = class_getInstanceMethod(class, originalSelector);
    Method swizzledMethod = class_getInstanceMethod(class, swizzledSelector);
    method_exchangeImplementations(originalMethod, swizzledMethod);
}
```

 When INSIDE the method, the use of ```///``` must be used to signal To-do's or little reminders for the programmer.
 when a wide explanation INSIDE a method must be done we will start with ```/**``` and end with ```*/```.

 We will use the following bullets to specify punctual situations:

 * ```(!)``` Will be used to call attention to possible bugs or fixes needed to make
 * ```(?)``` When the piece of code presents a problem not identified at the moment
 * ```:::``` This is a DevMark. When the code is ready for production, comments market this way must be deleted
