# Introduction

#### What is Figma Plus?

Figma Plus is an **unofficial** plugin platform for Figma. We hope to create a friendly community of users and developers building extensions to enhance the Figma experience.

#### Is it safe to run Figma Plus?

Security is our top priority in the development of Figma Plus. Our code does not perform any destructive actions to your Figma documents, nor does it contain any tracking or analytics scripts that expose your private information to third parties. Our code is open source and can be audited on [Github](https://github.com/figma-plus).

We also review every plugin and their updates for security threats before approving them to be available on our platform.

#### Is Figma Plus in affiliation with Figma?

**No.** Figma Plus is a community-driven project that is not affiliated with the Figma company.

#### What will happen to Figma Plus when Figma's official extensibility support arrives?

We are well aware of the extension platform that Figma is working on, as announced in [this article](https://www.figma.com/blog/figma-series-c/#the-future). However we believe both systems can coexist as there will undoubtedly be limitations from the official implementation that only Figma Plus can unlock.

An example would be any custom modifications to the Figma app UI, which can make for better plugin experiences but is very unlikely to be supported by the Figma team.

#### If I start building plugins for Figma Plus, will I have to rebuild them when the official extensibility becomes available?

The short answer is yes, but the migration process will likely be very easy.

We cannot talk about what we know about the official extensibility platform, but our [developer API](api/scene) will follow the official extension API syntaxes as much as possible. Transitioning between the two API's will be simple and straightforward.

We encourage developers to start building and experimenting with Figma Plus and decide whether to migrate to the official implementation when it becomes available.
