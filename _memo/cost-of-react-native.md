---
tags: 
  - framework
  - web
title: Cost Of React Native
date: 2023-04-17
description: null
authors: null
menu: memo
type: null
hide_frontmatter: false
---

![](assets/cost-of-react-native_69b49ec589ff19151408b8959ace27bd_md5.webp)

*React Native is a popular cross-platform app development framework that allows developers to build mobile apps for both iOS and Android platforms using a single codebase. It has gained popularity in recent years due to its ability to provide a native-like experience while reducing development time and cost.*

## Introduction
At Dwarves, React Native has been on our radar and we use it in some of our projects. Lately, we have been investigating cost-benefits of using it and making light of some concerns we should be aware of. We haven’t seen many posts consolidating this in broader detail. So in this blog post, our focus will be on exploring the cost of React Native development, discussing the advantages and disadvantages of using the framework, and hopefully providing some insights for developers and engineering leaders to make more informed decisions on choosing React Native for their projects.

## Choosing React Native
Most likely the main reason why companies choose to use React Native in their projects is due to how similar it is to regular React. This is because React was designed to be able to work with different JavaScript runtimes. Typically, the common runtime or JavaScript engine used for React Native will be [Hermes](https://reactnative.dev/docs/hermes). Otherwise, it will fallback to [JavaScriptCore](https://trac.webkit.org/wiki/JavaScriptCore), the engine that powers Safari.

This is great to avoid the need for polyglot developers, since if you know React, you can probably work with React Native albeit with a few nuances.

### Advantages of React Native
Additionally, React Native boasts several advantages over other frameworks and native development methods:

* **Cross-platform compatibility**: React Native allows developers to build mobile apps for multiple platforms (iOS, Android, Web, etc.) with a single codebase. This means that developers don’t have to create separate codebases for different platforms, which can save time and reduce development costs.
* **Faster development time**: React Native’s “Hot Reload” feature allows developers to see changes in their code immediately, which can speed up the development process. Additionally, the ability to reuse code across multiple platforms can save time and effort.
* **Large community and ecosystem**: React Native has a large and active community of developers, which means that there are plenty of resources and support available online. There are also many third-party libraries and tools available for React Native, which can make development faster and easier.
* **Developer productivity**: React Native allows developers to use JavaScript, which is a widely-used and popular programming language. This means that developers can leverage their existing skills and knowledge to build mobile apps, which can increase productivity and reduce the learning curve.
* **Learning curve**: If you're already familiar with React, a popular JavaScript library for building user interfaces, learning React Native can be easier as it shares many concepts and syntax with React.

### Disadvantages of React Native
Despite its many advantages, React Native has its share of drawbacks:

* **Performance**: While React Native is generally fast and efficient, it may not perform as well as native app development in some cases. This is because React Native uses a JavaScript bridge to communicate with native code, which can introduce some performance overhead.
* **Bundle size**: React Native apps can have a large bundle size, which can affect app performance and load times. This is because React Native includes a lot of code and libraries by default, and developers need to be careful not to include unnecessary code.
* **Native library integration**: React Native may not integrate easily with some native libraries, and developers may need to write custom modules to achieve the desired functionality. This can be time-consuming and may require a high level of expertise.

### Should developers use React Native?
React Native is certainly great option for developers who want to build mobile applications quickly and easily while providing a native-like experience for their users. However, it may not be the best choice for all applications. Engineers should consider specific needs of their application to evaluate whether React Native is the best option for them.

## Big Tech Companies Using React Native and Challenges Faced
We were definitely interested at what enterprise-level companies do with React Native. Some of the big tech companies that have stories with using React Native are of course:

### Facebook
Facebook, the origin of React Native, uses the framework to build a variety of applications, including Facebook Ads Manager and Facebook Analytics. The main challenge faced by Facebook in adopting React Native was ensuring optimal performance and a smooth user experience while maintaining a single codebase. This was not without the history of hurdles in the creation and use of GraphQL.

### Airbnb
While Airbnb initially used React Native for its mobile applications, it eventually decided to revert to native development due to performance and maintenance issues. However, they did acknowledge that React Native was beneficial for specific use cases and smaller projects.

### Microsoft
Microsoft has adopted React Native for several applications, such as Skype and Xbox. Their challenges were in optimizing the performance of React Native apps for feature-parity for a wide range of devices as well as addressing compatibility issues with third-party libraries.

### Coinbase
Coinbase, a leading cryptocurrency exchange platform, uses React Native to build its mobile applications. The company needed a framework that allowed rapid iteration and the ability to reuse code for different platforms. While React Native provided these benefits, Coinbase faced challenges in optimizing complex animations and ensuring a seamless user experience.

### Discord
Discord, a popular communication platform for gamers, adopted React Native for its mobile applications. React Native allowed Discord to develop and iterate their app quickly. However, they faced challenges in maintaining optimizing specific native features, such as voice and video chat, and needed to develop custom native modules to help address these issues.

![](assets/cost-of-react-native_cb4a01ca2ab93832ae3ffec401441e07_md5.webp)

## The development cost of React Native
The cost of developing a React Native application can vary depending on several factors, including the complexity of the application, design, features, and maintenance costs. The larger and more complex the application, the more expensive it is to develop. Similarly, applications with more advanced features, such as push notifications or in-app purchasing, will cost more to develop.

Additionally, the cost of development can vary depending on the hourly rate of developers in different regions. For example, developers in the United States and Western Europe typically charge higher rates than those in Eastern Europe or Asia. This means that businesses can save money by outsourcing development to countries with lower hourly rates.

However, it’s essential to consider the trade-offs of outsourcing development to save on costs. Developers in other countries may not have the same level of expertise as those in more developed countries. This can lead to lower-quality work, missed deadlines, and communication difficulties, all of which can increase the overall cost of the project.

Furthermore, while React Native is a cost-effective option for mobile application development, it’s not always the best choice. For instance, if the application requires advanced hardware features, such as fingerprint scanning or camera functionality, native application development may be a better choice. Native development provides better access to platform-specific features, but it also increases development costs.

![](assets/cost-of-react-native_076bec90671c2f71c0fdb93849498a01_md5.webp)

## Conclusion
In conclusion, React Native is a popular cross-platform app development framework that offers several advantages, including cross-platform compatibility, faster development time, and a large developer community. However, it also has some drawbacks, such as performance issues, a nuanced learning curve, and limitations on native functionality.

Whether a developer should use React Native really depends on the needs of their application. The cost of developing a React Native application can vary depending on several factors, including complexity, design, features, and maintenance costs. As such, it may be something to consider whether you should stay on the web or going native.

# References:
* [https://reactnative.dev/](https://reactnative.dev/)
* [https://medium.com/airbnb-engineering/sunsetting-react-native-1868ba28e30a](https://medium.com/airbnb-engineering/sunsetting-react-native-1868ba28e30a)
* [https://www.coinbase.com/blog/announcing-coinbases-successful-transition-to-react-native](https://www.coinbase.com/blog/announcing-coinbases-successful-transition-to-react-native)
* [https://discord.com/blog/how-discord-achieves-native-ios-performance-with-react-native](https://discord.com/blog/how-discord-achieves-native-ios-performance-with-react-native)
* [https://www.youtube.com/watch?v=8wAj0KG5H6U](https://www.youtube.com/watch?v=8wAj0KG5H6U)