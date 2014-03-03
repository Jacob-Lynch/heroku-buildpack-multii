Heroku buildpack: Multi
=======================

I thought, "It would be neat to have a... composable!... buildpack for
Heroku." So I built this. I called my creation heroku-buildpack-multi.

Shortly thereafter I found [ddollar/heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi)
which is named the same, calls itself composable, and uses the same
approach in `bin/compile`.  It's seen real-world use, it has a community,
and it was here first.

So I renamed this one heroku-buildpack-multii, borrowed some ideas and
barged ahead.

What's different?
-----------------

The original heroku-buildpack-multi is designed to build from a set of
cooperative buildpacks, then finish with a terminal buildpack that
completes the installation in /app.  This buildpack attempts to make
apparent terminal buildpacks cooperate, for example to combine ...

* Each buildpack gets its own BUILD_DIR and CACHE_DIR.
* Buildpacks that install to APP_DIR are merged.
* Doesn't throw away compile-time error messages from git, tar, etc.
* Doesn't work with tarballs yet, only git repos.
