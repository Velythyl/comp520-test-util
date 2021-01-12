# comp520-test-util
Util that uses a docker image to build and test your compiler. Supports JUnit, and runs all test files in your tests folder

# Install

This depends on docker. It is also better if it can run without needing to `sudo`, so follow this guide to install it https://phoenixnap.com/kb/how-to-install-docker-on-ubuntu-18-04 and then this guide to set it up for your user https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user.

Then, fork & clone this repo into your project's root and rename it to something weird like `ﾉΦωΦﾉ` to make sure that there's no naming conflicts on the server.

And like, add it to your .gitignore so that there's no submodule issues or whatever, or just delete its .git folder.

That's it.

# Usage

*All commands listed here assume your are in this util's directory, and the root of your gitlab repo is found in `..`*

To pipe all your test C files into your compiler, call `make <pass>`, where pass is the compiler pass you want to test your files found in `../tests`.

To run JUnit tests, call `make junit`. This assumes that you have JUnit tests inside the `test` repository of your project (you have to create these yourself). This is less usefull than the `make <pass>` feature, because really you could just make IntelliJ do your tests, but it was an easy include, so why not.

# How it works

## Junit:

Inside the docker, this repo gets expanded into the root of the project. So from the point of view of JUnit, `src` and `test` are on the same level, just like they would normally be in a normal JUnit-compatible project. And then it builds using maven inside the docker and prints its output to a file in this util's directory.

## Pass:

Inside the docker, there's a python script that reads all your files found in your project's `tests` folder and calls your desired compiler pass on each one sequentially .
