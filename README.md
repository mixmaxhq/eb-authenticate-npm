# eb-authenticate-npm

This module installs an `.ebextensions` config file that will authenticate
your Elastic Beanstalk environments to npm.

The config file will do this by creating an `.npmrc` that reads the value of the
`NPM_TOKEN` environment variable. This `.npmrc` file will only be created in
EB, letting you use whatever authentication strategy you like locally. ([The
alternative.][check in .npmrc])

By the way I was really hoping that EB would automatically read `NPM_TOKEN` as
per [this Stack Overflow answer][wrong answer] but that didn't work for me
(tested 8/3/2016).

## Installation

1. `npm install eb-authenticate-npm --save-dev` (see [here](https://github.com/mixmaxhq/install-files/blob/master/README.md#installation) for why `--save-dev`)
2. Commit the `.ebextensions` file it creates.
3. Set the `NPM_TOKEN` EB environment variable to an npm [authentication token][token].
4. Deploy.

## Modifying the `.ebextensions` file

This module will overwrite the file if/when it is updated.

Pull requests are welcome if you have some generally-useful modifications to
suggest.

If you'd like to make modifications specific to your use case, you should uninstall
this module after installing the `.ebextensions` file. Uninstallation won't take
the file with it.

## Thanks/Prior art

Thanks to Remy Sharp for [suggesting this strategy][this strategy], and [this
Stack Overflow answer][SO] for helping me figure out where the `.npmrc` needed
to be written.

[check in .npmrc]: https://remysharp.com/2015/10/26/using-travis-with-private-npm-deps#file-based
[SO]: http://stackoverflow.com/a/24993093/495611
[this strategy]: https://remysharp.com/2015/10/26/using-travis-with-private-npm-deps#dynamic
[token]: https://docs.npmjs.com/private-modules/ci-server-config#getting-an-authentication-token
[wrong answer]: http://stackoverflow.com/a/37866227/495611
