# plainsite

Quick POC of CLI tool to embed arbitrary data inside a JPEG file.

## Getting Started

It's actually really simple to use this tool. Either just run the program using `./freeStorage` to see the help, or use the following example:

```
➔ cat testdata
This is test data
Testing using data
Data-driven testing :)

➔ ./plainsite embed img_orig.jpg testdata

➔ ./plainsite fetch testdata_embedded_in_img_orig.jpg
This is test data
Testing using data
Data-driven testing :)
```

## Goals
The main goal of this simple project is to allow someone to embed a piece of data inside an image file without corrupting said file. Afterwards, you could upload the file to, for instance, Reddit (or any other image upload service which doesn't recompress the image or strip the data), allowing you to use it as free data-storage.

In the future, I'd like to add encryption options, to make sure that even with the image file, someone can't fetch the data inside without the right key.

## Built With

* [Node.JS](https://nodejs.org) - Node.js is an open-source, cross-platform JavaScript run-time environment for executing JavaScript code server-side.

<!--## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 
-->
## Authors

* **Jeff Huijsmans** - *Initial work* - [jeffhuys](https://github.com/jeffhuys)


## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

