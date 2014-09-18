Heroku Buildpack for Eiffel
================================

A Buildpack that allows you to deploy Eiffel applications on the Heroku platform.

## Status
* Working for simple ECFs

## Notes
* A Procfile is required for execution.  Make sure the application accepts the `$PORT` argument for HTTP routing.
* Use the [nino server](https://github.com/Eiffel-World/Eiffel-Web-Framework/tree/master/contrib/library/network/server/nino) to provide HTTP access.

## Todo
* Currently only the first target in the ecf is used to determine what application to deploy.  This needs to be parameterized.
* There is currently no accommodation for Heroku addons.

## Credits
* Heroku and their new [Buildpack-capable stack](http://devcenter.heroku.com/articles/buildpacks)

## Usage
Push the app to Heroku. Learn more about [deploying to Heroku with git][deploy].

```bash
$ git push heroku master
```

Example output from a `git push`:

```bash
$ git push heroku master
Fetching repository, done.
Counting objects: 1, done.
Writing objects: 100% (1/1), 188 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)

-----> Fetching custom git buildpack... done
-----> Eiffel app detected
-----> compile params: /tmp/build_2b78b706-1fb1-448e-9bed-012204f6e08c /app/tmp/cache /tmp/d20140917-330-dm394l
-----> Checking Eiffel Compiler
       Eiffel Compiler installed
-----> Compiling /tmp/build_2b78b706-1fb1-448e-9bed-012204f6e08c/restbucks-safe.ecf for target restbucks
Eiffel Compilation Manager
Version 14.05.9.5417 GPL Edition - linux-x86-64

Degree 6: Examining System
Degree 5: Parsing Classes
Degree 4: Analyzing Inheritance
Degree 3: Checking Types
Degree 2: Generating Byte Code
Degree 1: Generating Metadata
Melting System Changes
Degree -2: Constructing Polymorphic Table
Removing Unused Code

Degree -3: Generating Optimized Code
System Recompiled.
You must now run "finish_freezing" in:
    /app/tmp/repo.git/EIFGENs/restbucks/F_code
Eiffel C/C++ Compilation Tool - Version 14.05
Copyright Eiffel Software 1985-2010. All Rights Reserved

Preparing C compilation
Compiling C code in E1
Compiling C code in C19
Compiling C code in C17
Compiling C code in C18
Compiling C code in C16
Compiling C code in C15
Compiling C code in C14
Compiling C code in C13
Compiling C code in C12
Compiling C code in C11
Compiling C code in C10
Compiling C code in C9
Compiling C code in C8
Compiling C code in C7
Compiling C code in C6
Compiling C code in C5
Compiling C code in C4
Compiling C code in C3
Compiling C code in C2
Compiling C code in C1
Compiling C code in E2
C compilation completed
-----> Discovering process types
       Procfile declares types -> web

-----> Compressing... done, 1.1MB
-----> Launching... done, v32
       http://peaceful-meadow-3723.herokuapp.com/ deployed to Heroku

To git@heroku.com:peaceful-meadow-3723.git
   b4b1e6b..90ba6f2  master -> master
```

Scale to one web dyno (aka server):

```bash
$> heroku ps:scale  web=1
```

Test your app! The URL is printed at the end of the `git push` step.
