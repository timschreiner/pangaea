pangaea
=======

**Powerful pre-processor for text files - powered by JavaScript.**

Pangaea works on any kind of text file including HTML pages, source code files, documents, etc.  The easy-to-use command line tool lets you effortlessly bake Pangaea into your build process, providing you with an extremely powerful text pre-processor wherever you need it.

### How it works

```html
This is just a normal text file that has pangaea scripts embedded, e.g. JavaScript:

<pangaea type="text/javascript">
  function name(){
    return "Pangaea";
  }
</pangaea>

We can call the scripts to get the name, which is <%= name() %>.

Other JavaScript also works, so we know that 5 + 10 is <%= 5 + 10 %>.
```

The above file, when processed will output as:

```
This is just a normal text file that has scripts embedded:

We can call the scripts to get the name, which is Pangaea.

Other JavaScript also works, so we know that 5 + 10 is 15.
```

### Usage

#### Embedding JavaScript

To embed JavaScript, just use the `<pangaea>` script tag like this:

```html
<pangaea type="text/javascript">
  // code goes here
</pangaea>
```

For inline script that will print out the return, use the `<%=` and `%>` special tags:

```html
My name is <%= name %>.
```

#### Command line tool

The `pangaea` command reads from the standard in pipe, and writes to the standard out pipe.

```
cat ./example/source.txt | pangaea >> ./example/output.txt
```

Or you can use it in an interactive mode:

```
pangaea
```

  * See some [examples](https://github.com/stretchr/pangaea/tree/master/examples) of how you can use Pangaea.

#### Parameters

Pangaea supports parameters that are made available to your scripts via the `$$params` global object.  You can specify parameters using the `-params` flag and a URL encoded query string:

    pangaea -params="name=Mat&age=30"

This will make the `$$params["name"]` and `$$params["age"]` variables available to your scripts.

  * All parameter values are strings, if you want to use other types you can cast them in your code.

### Download latest

Check out [releases](https://github.com/stretchr/pangaea/releases), or download the source and build from source using `go install`.

  * Version v0.2 for darwin amd64 - [pangaea-v0.2-darwin-amd64.tar](https://github.com/stretchr/pangaea/releases/download/v0.2.0/pangaea-v0.2-darwin-amd64.tar)
  * Version v0.2 for freebsd 386 - [pangaea-v0.2-freebsd-386.tar](https://github.com/stretchr/pangaea/releases/download/v0.2.0/pangaea-v0.2-freebsd-386.tar)
  * Version v0.2 for freebsd amd64 - [pangaea-v0.2-freebsd-amd64.tar](https://github.com/stretchr/pangaea/releases/download/v0.2.0/pangaea-v0.2-freebsd-amd64.tar)
  * Version v0.2 for freebsd arm - [pangaea-v0.2-freebsd-arm.tar](https://github.com/stretchr/pangaea/releases/download/v0.2.0/pangaea-v0.2-freebsd-arm.tar)
  * Version v0.2 for linux 386 - [pangaea-v0.2-linux-386.tar](https://github.com/stretchr/pangaea/releases/download/v0.2.0/pangaea-v0.2-linux-386.tar)
  * Version v0.2 for linux amd64 - [pangaea-v0.2-linux-amd64.tar](https://github.com/stretchr/pangaea/releases/download/v0.2.0/pangaea-v0.2-linux-amd64.tar)
  * Version v0.2 for linux arm - [pangaea-v0.2-linux-arm.tar](https://github.com/stretchr/pangaea/releases/download/v0.2.0/pangaea-v0.2-linux-arm.tar)
  * Version v0.2 for windows 386 - [pangaea-v0.2-windows-386.tar](https://github.com/stretchr/pangaea/releases/download/v0.2.0/pangaea-v0.2-windows-386.tar)
  * Version v0.2 for windows amd64 - [pangaea-v0.2-windows-amd64.tar](https://github.com/stretchr/pangaea/releases/download/v0.2.0/pangaea-v0.2-windows-amd64.tar)

### Rules

  * Keep `<pangaea type="text/javascript">` and `</pangaea>` tags on their own lines
  * Please report any [issues](https://github.com/stretchr/pangaea/issues)
  * There are no rules

## Development

To build and run the command inside the `cmd` directory, do:

```
clear; go build -o pangaea; cat ./example/source.txt | ./pangaea >> ./example/output.txt
```
