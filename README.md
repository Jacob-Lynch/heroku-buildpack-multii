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

Frankly not much is different. I thought there would be more, but as
I learned how the directories (build, cache, env) are set up, this has
gradually converged with the original heroku-buildpack-multi.

Here are the remaining primary differences:

* Each buildpack gets its own CACHE_DIR.
* Error messages from git etc. are displayed rather than stifled.
* Doesn't work with tarballs yet, only git repos.
