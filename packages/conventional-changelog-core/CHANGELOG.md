# Changelog

All notable changes to this project will be documented in this file. See [standard-version](https://github.com/conventional-changelog/standard-version) for commit guidelines.

### [5.0.2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/compare/v5.0.1...v5.0.2) (2021-01-07)

### [5.0.1](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/compare/v5.0.0...v5.0.1) (2021-01-07)

## [5.0.0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/compare/v1.1.0...v5.0.0) (2021-01-07)


### ⚠ BREAKING CHANGES

* nested object properties no longer supported when sorting
* drop support for Node 8 (#599)
* **git-semver-tags:** --tagPrefix flag was changed to --tag-prefix
* drop support for Node 6 (#558)
* gitSemverTags now takes options followed by callback.
* moved BREAKING CHANGES to top of template.
* if ! is in the commit header, it now indicates a BREAKING CHANGE, and the description is used as the body.
* a ! character at the end of type will now be omitted
* forcing a breaking semver change based on https://github.com/conventional-changelog/conventional-changelog/pull/385
* Re-use parser options object between components of a preset. For some
presets this may change the behavior of `conventional-recommended-bump`
as the parser options object for the `conventional-recommended-bump` options
within a preset were different than the parser options object for the
`conventional-changelog` options within a preset.

If you are not using `conventional-recommended-bump`, then this is
**not** a breaking change for you.
* **package:** Set the package's minimum required Node version to be the oldest LTS
currently supported by the Node Release working group. At this time,
that is Node 6 (which is in its Maintenance LTS phase).
* Anchor tags are removed from the changelog header templates. The
rendered Markdown will no longer contain anchor tags proceeding the
version number header that constitutes the changelog header. This means
that consumers of rendered markdown will not be able to use a URL that
has been constructed to contain a version number anchor tag reference,
since the anchor tag won't exist in the rendered markdown.

It's stronly recomended consumers use the full URL path to the release
page for a given version, as that URL is a permalink to that verison,
contains all relavent release information, and does not, otherwise, rely
on the anchor tag being excessible from the current page view.

As an example, for version `2.0.0` of a GitHub project, the following
URL should be used:
- https://github.com/conventional-changelog/releaser-tools/releases/tag/v2.0.0
*   The Angular conventions specifically say that breaking changes must
  start with "BREAKING CHANGE", not the plural form. Therefore the
  previous plural form "CHANGES" has been corrected to singular "CHANGE".

  Former "chore" type has been replaced by a type "build" for commits on
  the build system and "ci" for commits regarding CI
* **writer:** Logic for generating release headings has been changed to make all
heading levels the same (`##`/`h2`) for better compatibility with
screen readers and parsers, and to conform to HTML semantics. Patch
release titles are now wrapped in a `<small>` tag to maintain the
visual hierarchy of the previous style.

Fixes https://github.com/conventional-changelog/conventional-changelog/issues/214
* **eslint:** Trailing whitespaces at the beginning of commit messages
will not be saved anymore
* **deps:** Using conventional-changelog v1.
* **deps:** Use conventional-changelog^0.5.0
* Callback is removed. I think only stream interface should exists.
From does not have any default value.
* This module is imported from https://github.com/ajoslin/conventional-changelog, and is originally written by @vojtajina, @btford and @ajoslin.
* **help:** `overwrite` is now called `same-file`.

Fixes https://github.com/ajoslin/conventional-changelog/issues/100
* **flags:** `--git-raw-commits-opts`, `--parser-opts` and `--writer-opts` are removed as they are considered uncommon, use `--config` is easier as people can write all options within one file and they can learn from existing presets.

Fixes https://github.com/ajoslin/conventional-changelog/issues/100
* **context:** `context.host` cannot change the default of `context.linkReferences` because if the host is unknown, `context.host` is `undefined` and all links will just use `context.repository`.
* **notes:** `notes` in `noteGroups` is not an array of simple string any more but object. You must use `note.text` to access the equivalent of previous `note`.
* **notes:** `includeDetails` will only include `log` and `keyCommit`.
* **templates:** If `partials` is not empty, it should not ignore header, commit and footer partials.
* **reverse:** when there is no commits left for the last block of logs it will still try to generate one. (Assume commits might be rebased or lost but still need a new version).
* **noteGroups:** `options.noteGroups` is no longer available. Filter the notes from upstream or in `options.transform` instead.
* **version:** `version` is not a required field and it is moved to the `context` object. If version is found in the last commit, it will be overwritten.
* **cli:** Previously version number has to be passed as a flag. As a version number is compulsory, it does not make sense for a flag to be compulsory. So if a version number is passed as an input it is still valid.
* **transform:** `options.hashLength`, `options.maxSubjectLength` and `options.map` are deprecated in favour of `options.transform`.
* **map:** `options.replacements` is now `options.map` and it can also take functions
* **compareFunc:** commitGroupsCompareFn -> commitGroupsSort, commitsCompareFn -> commitsSort, noteGroupsCompareFn -> noteGroupsSort and notesCompareFn -> notesSort
* **compareFunc:** Default compare functions no longer sort by lexicographical order. They use `localeCompare` instead
* **merge:** `pull request` should be `merge`. Also make the parsed result to be consistent with other parts.
* **issuePrefixes:** `options.referenceKeywords` is now `options.referenceActions`
* **hash:** hash is no longer supported. This parser should just parse raw commit messages. Also text fields are appended with a newline "\n".
* **regex:** It returns a nomatch regex if it's keywords are missing.
* **headerParts:** `headerParts` does not limit to `type`, `scope` and `subject`. They can now be defined in `options.headerCorrespondence` and the order is the order of capturing group in `options.headerPattern`. If part is missing in `options.headerCorrespondence` it is `undefined`. If part is not captured but is not missing in `options.headerCorrespondence` it is `null`.
* **maxSubjectLength:** `maxSubjectLength` is not available any more.
* **correspondence:** body and footer will be null if they are not found. type and subject are nullable too.
* **references:** `closes` now becomes `references` and it is loosely based the links above.
* **parser:** The regex for matching notes are loosen. The semicolon and space are optional. The `notes` object is no longer a key-value object but an array of note object, such as
```js
{
  title: 'BREAKING AMEND',
  text: 'some breaking change'
}
```
The detection of notes, closes, continueNote and isBody are mutually exclusive.
* **breaks:** Variable name related to `breaks` changes to `notes`, because "Important Notes" a more generic term. There is no functional changes.
* **stream:** It no longer skips the chunk if commit cannot be parsed. An empty string is passed to down stream
* This module is imported from https://github.com/ajoslin/conventional-changelog, and is originally written by @vojtajina, @btford and @ajoslin.
* **unreleased:** If `context.version` is the same as the version of the last release, by default the unreleased chagnelog will not output.
* **config:** `options.preset` is removed in favour of `options.config`

### Features

* ! without BREAKING CHANGE should be treated as major ([#443](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/443)) ([cf22d70](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cf22d70fbccaea0ab0130c011d7d203593f19fcb))
* ability to reset changelog from scratch ([#350](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/350)) ([0eea0af](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0eea0af058b551dea8ed3dd2956777ee0676f9c2))
* add --output-unreleased ([d9cd01a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d9cd01a9f17792ef22922a010feeb1d4293f8733))
* add helper for parsing array of commits ([#711](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/711)) ([e869fe6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e869fe67548b210508a9df0ce99180164b740e65))
* add lerna repository support ([#173](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/173)) ([70df504](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/70df504c51f9cd926c2e1bf6a554c047eba786af))
* add support for ! ([#441](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/441)) ([0887940](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0887940e9103dca111e43337332913b37e1ee02a))
* add support for '--skip-unstable' option ([#656](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/656)) ([#656](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/656)) ([0679d7a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0679d7a1d7a8715918326f31ec3f6168c2341fd6))
* add support for 'feature' as alias for 'feat' ([#582](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/582)) ([94c40f7](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/94c40f755e6c329311d89a47c634b91cf0276da3))
* add support for listing lerna style tags (project@version) ([#161](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/161)) ([b245f9d](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b245f9d46a064a6daa2b46a48eab354c512f46c0))
* allow raw commits to be filtered by path ([#172](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/172)) ([ec0a25d](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/ec0a25d0664ae74da1201c011814f62bd8e1b031))
* allow to specify a tagPrefix in conventional-recommended-bump ([f60f86f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f60f86fa388edb3b0731b2fb0cb5ddabafd36911))
* allows notes pattern to be customized ([#586](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/586)) ([9c00f32](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/9c00f3242d916be1774a618d943f908f8d9699a6))
* **angular:** find package.json from cwd upwards ([#206](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/206)) ([867c142](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/867c142795d34f15673eee3b3e398d8b28a32041))
* **angular:** use the context for getting the repository and host urls ([#217](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/217)) ([c146f2a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c146f2a67ac8127423fe24cc0cbe304cfa637fe3))
* BREAKING CHANGES are important and should be prioritized ([#464](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/464)) ([f8adba2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f8adba2f7dc84fd73adafb695371e0624b922792))
* **cli:** able to have two files, separator works for interactive ([db1e3b5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/db1e3b54ab0574ddad48f34fdafcc3b78e9e4864))
* **cli:** add aliases, more help details and tests ([eb654a2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/eb654a2aab20c0a6d7f2b51a6ac6515e7a2cb562))
* **cli:** add missing options ([8ac1cf7](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/8ac1cf7e7a7a9f6e2eafb19248741c5153c3fec1))
* **cli:** add warn function for interactive shell ([84fe31f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/84fe31f561239beb85a7447796fb34d67bf1aa24))
* **cli:** version can be passed directly as an input ([cadf7af](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cadf7afed75f37799c9be5db5fed552af9edd210))
* **commit.hbs:** scope can be missing ([82e0ffa](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/82e0ffa859356909e37cb11a08fa51125c2f6005))
* **commit.hbs:** use `header` if `subject` is missing ([5e475a0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/5e475a097f01d13be116f2dea2b63a725afd2950))
* **commit:** `raw` object is attached to `commit` ([2ea9f04](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/2ea9f0497c044ab1f196c99d51846c1b7a98331e))
* **compareFunc:** these values can be string or array ([464988c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/464988c9d9ec6ba9d028f396e5e93702f7a50639))
* **compareFunc:** use module "compare-func" ([520014e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/520014e2a1d6b73a5fc356e5452f2854dc940991))
* **config:** change preset to config ([c470628](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c470628d31048752c0a3ca4a36a7267f5c327bdf))
* **config:** should work with preset ([7b6a1e3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/7b6a1e3b4c8b006f6c506cfec3c7eb17b8cdc8b6)), closes [#4](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/4)
* context.currentTag should take into account lerna tag format ([#178](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/178)) ([f0e5875](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f0e58757cc6ba0f80df9b9459c68fe9ce2d38540))
* **context:** default currentTag may not prefix with v ([#179](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/179)) ([431598a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/431598a3b12a404aee63f8ab3e51263121cde485))
* **context:** expose `finalizeContext` to modify context at last ([d5545c0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d5545c0d9fc7468a26d0ed67c788ed4faae1b80d))
* **context:** fallback to repoUrl ([dc9c626](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/dc9c626a0fa977b71c75faf147e3dc6c901ca101))
* **context:** fallback to repoUrl ([20a5ccc](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/20a5ccc5a33040dd68c6fd308188619f578c7dd7)), closes [#7](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/7)
* **context:** linkReferences has nothing to do with context.host ([1656df8](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1656df8e488356ebd4bf4aaa6c88d01dedcb74a7))
* **conventional-changelog-core:** provide facility to define gitExecOpts. ([#480](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/480)) ([814f878](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/814f878054ca3c9ec00c3147478eb1e6a2762e9a))
* **conventional-commits-parser:** add issuePrefixesCaseSensitive parser option ([#580](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/580)) ([526b282](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/526b28214d12c55158eb2e4d44408378587ceb97))
* **conventional-recommended-bump:** send options to whatBump ([#409](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/409)) ([508d6d6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/508d6d6184c1f175b637538b6a554c92bce7d30c)), closes [/github.com/lerna/lerna/blob/a6733a2b864cf9d082d080bbd3bfedb04e59b0ab/core/conventional-commits/lib/recommend-version.js#L13-L21](https://bitbucket.agile.bns/mrvl//github.com/lerna/lerna/blob/a6733a2b864cf9d082d080bbd3bfedb04e59b0ab/core/conventional-commits/lib/recommend-version.js/issues/L13-L21)
* **conventional-recommended-bump:** support for '--skip-unstable' ([#698](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/698)) ([3a5b41e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3a5b41e0ccdcdfb81f1b75f295975b0ab0f48683))
* conventionalcommits preset, preMajor config option ([#434](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/434)) ([dde12fe](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/dde12fe347d8c008c6ba3361e2f6357274537a77))
* **conventionalcommits:** allow matching scope ([#669](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/669)) ([e01e027](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e01e027af60f5fa3e9146223b96797793930aeb4))
* **correspondence:** add `headerCorrespondence` and improve commit parts ([aca9e95](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/aca9e9597a4ea2da172840f629684aa66f67786a)), closes [#6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/6)
* creating highly configurable preset, based on conventionalcommits.org ([#421](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/421)) ([f2fb240](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f2fb240391e10c79756a590eb6aea1e235ccb0a2))
* **debug:** add options.debug function ([a315a4b](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a315a4b471dba4a46ac12671fdcb12e029dfbd88))
* **debug:** convient function for debugging ([c041e35](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c041e35ddd4b1249e9055a63399fc506bfac75a9))
* **debug:** make options.debug as default writeOpts.debug ([71dcd72](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/71dcd72ad893bc9f2654d89813286bbc8946c4ba))
* **debug:** options.debug can print git-log cmd ([cae0ca0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cae0ca0a4bd741197857c5c051f33badba3b27e3))
* **debug:** use conventional-changelog 1.1.0 and debug when verbose ([bf0f1ad](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/bf0f1ad8f519ad665dccda258a503e1e92910cbc))
* **debug:** use conventional-changelog 1.1.0 and debug when verbose ([b72c74f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b72c74f7a10a92b3af6490dcef1bf43192052fc6))
* default to overwriting and/or generating CHANGELOG.md. ([8678b62](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/8678b62271a1396518d7124c379897e4d7260c78))
* **defaults:** merge default options and make it less angular ([8e29f96](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/8e29f9603f892d126ee5aea17820f7a73178e393)), closes [#3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/3) [#4](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/4)
* **deps:** bump ([4e49b36](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/4e49b360d4c0ccb9dc65fabfcb87e1dd5d362a23))
* **deps:** bump conventional-changelog to ^0.2.1 and use new api ([0130835](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0130835081c573c099df9959c187336f27b4444c))
* **deps:** bump conventional-changelog to ^0.3.0 ([e8e40f3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e8e40f39a9ccdaebfef7b8eb893fa3035e6f80d6))
* **err:** print the cmd when error ([7469ce1](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/7469ce16b98aa730ad7963dc16129d409a647d12))
* **eslint:** improve regex headerPattern ([#268](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/268)) ([ccc1365](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/ccc136505712fdf3e13e4c52a8d23f568ad8b3f0))
* **exports:** export the promise ([0432646](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0432646bb0376812607744bf225293601f992f53))
* extracting code from https://github.com/ajoslin/conventional-changelog ([c9c116a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c9c116af35a0bd45738b60147533bce5b44da425))
* **fieldPattern:** should support string format ([b6b6b52](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b6b6b52f50bd5b06c467a7b1c5fa4a742a10009c))
* **flags:** add config and remove uncommon ones ([c2029e6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c2029e612dc9d87a038768b3bf2f38d287e884a0))
* **flush:** add `options.doFlush` to make it possible not to flush ([2fdf142](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/2fdf142475a60c804edfcb703ccd2425dfcfa149))
* **generateOn:** also pass commits, context and options to the function ([a59c73c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a59c73c709e6d7c75ae7a0157bfe5360014817b2)), closes [ajoslin/conventional-changelog#135](https://bitbucket.agile.bns/ajoslin/conventional-changelog/issues/135)
* **generateOn:** by default if `commit.version` is a valid semver ([19ad3b1](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/19ad3b163d3708abb9cc7d7d43c8a3ab88e1e23c))
* **generateOn:** if the commit is ignored fall back on the original ([be5723a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/be5723a51ed12f54485d96b35f651a45ec85a58a))
* **generateOn:** log doesn't have to be generated once ([ff88a62](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/ff88a626107332dcedb47025af97b4722b19571d))
* **generateOn:** other type to disable ([9c50b90](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/9c50b90c96ea99eba3c9b45ab46016f064bdc788))
* **generate:** originalCommits as last argument ([797fa8c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/797fa8c22d801450626ad9730cbec83906360c9c))
* **git-raw-commits:** add execOpts.cwd ([2631213](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/263121376323babeb5bd0e8e48b852921ff81d81))
* **github:** adds github-specific replacements for issues and users ([05dbb08](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/05dbb08b7d57883746f328927f7d9a24cfdc7279)), closes [#12](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/12)
* **hash:** drop support ([1ccc751](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1ccc7510980632fb8bd3fa2c79fd439da63ff738))
* **headerParts:** headerParts can be anything ([31e1c11](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/31e1c1168e46086c2e051ba082f014a1b1b54cd3)), closes [#10](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/10)
* **help:** improve the flag names and add more descriptions ([4355522](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/43555227dc57d40dd51dc0214939464e40634e0b))
* improvements and bug fixes ([1cde104](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1cde104b4fbdddf3ac471a862d28d779005a5706)), closes [#5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/5)
* **includeDetails:** return an object that contains more details ([81e79f7](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/81e79f795fe730a5f7fe29fac91363ab8f143189))
* **infile:** warn if infile does not exist ([1a196bb](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1a196bbbe0fe636038dbec0680531769b16de8cd))
* init ([a331bd0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a331bd02ae5145024bb42f894367145d22b49e3d)), closes [ajoslin/conventional-changelog#84](https://bitbucket.agile.bns/ajoslin/conventional-changelog/issues/84)
* **init:** extract cli from conventional-changelog ([9cb3a46](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/9cb3a460366502c8223e36fe9b2beda19e7942d7))
* **init:** extract core from conventional-changelog ([cb58157](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cb58157558646b374652c274fbd20a87bfce01c1))
* **init:** extracting code from https://github.com/ajoslin/conventional-changelog ([c647bdf](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c647bdfb0d5f331e349ad4a58585d67f69f626e0))
* introducing support for lerna style tagging ([7be07c7](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/7be07c7c0f49572b1c0e9c98f004b599d8b5bb1a))
* **issuePrefixes:** init and referenceKeywords -> referenceActions ([86bf798](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/86bf798cea0f78e0c22a0ebe5a094a87cee6f7dd)), closes [#11](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/11)
* make comment stripping optional ([db5b711](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/db5b7111022fadbd44717fa5a74580c542f80fcb)), closes [#251](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/251)
* **map:** change `options.replacements` to `options.map` ([d0a04ef](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d0a04efa8319a906ca86a6d358c51e94aa51b675))
* **maxBuffer:** expose this option incase of long git history ([77f8e21](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/77f8e218484896c3168c6fa0ca5a1a8e5fa50105)), closes [#5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/5)
* **maxSubjectLength:** added ([83c98b9](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/83c98b9fbe6e228e9d94071de7a5514b4f7a6e1e))
* **maxSubjectLength:** removed ([3448582](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3448582be14116489769569341ddab60e5f8b624))
* **mentions:** [@someone](https://bitbucket.agile.bns/someone) in commit ([d60fe76](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d60fe766fd6caca026b22f5d8af40337315cfa34)), closes [#24](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/24)
* **merge:** ignore merge commits ([15c8dc3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/15c8dc3912c2f0336ceb63c04117c164ca860501))
* migrate repo to lerna mono-repo ([793e823](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/793e8235c961dd509cc63dccadaeb7cb956da6f9))
* **newline:** fields does not contain leading or trailing newlines ([6db453b](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/6db453bb768d6d98a48fca39414ff54a7ea096f6)), closes [#14](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/14)
* **noteGroups:** remove and add note title transform ([abedbfd](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/abedbfd3c1c747ef3ed684dec878a36b2d784de4))
* **noteKeywords:** make BREAKING CHANGE more forgiving ([b74e061](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b74e061a33730712b3fdac88997ddef418073d0f))
* **note:** noteKeywords is case insensitive ([f779a29](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f779a296e61ba9290c0361c35538dff505f8e92a)), closes [#21](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/21)
* **notes:** attach the commit to the note ([af89d4a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/af89d4a6fe0f39906ddc7cbfb6bc48c1049fbd07)), closes [#12](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/12)
* **options:** all options can be a string ([0fa17b4](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0fa17b40f801037e204961c64179dd7eca3719e1))
* **otherFields:** other fields are possible to be included ([9e06278](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/9e06278174004c708f74038dafd396a47e31dba2))
* **owner:** add owner context ([8d7b5d9](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/8d7b5d9dac994373835e34efe7a3517b63faa21c)), closes [#7](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/7)
* **owner:** yield owner field ([d8d0334](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d8d0334801d3df78b83ffc6865408995f35b3a78)), closes [stevemao/conventional-commits-parser#1](https://bitbucket.agile.bns/stevemao/conventional-commits-parser/issues/1) [conventional-commits-parser#1](https://bitbucket.agile.bns/mrvl/conventional-commits-parser/issues/1) [#12](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/12)
* **parser:** notes can have more than one paragraph ([733bfa9](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/733bfa95628e6fd5810836b227a181492e566e52)), closes [#3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/3)
* **pkg:** fallback to git remote origin url ([ff22fe6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/ff22fe652bac6cc2fd4889669f2159e2df59eae9))
* **preset-loader:** allow use of absolute package path ([#530](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/530)) ([84d28b2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/84d28b285f787e9b1252aadf55f07a358635a5a6))
* **preset-loader:** allow use of full package names ([#481](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/481)) ([03cb95c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/03cb95cb92aed56b2cca995f1c7ead9fbe6a08d7))
* **preset-loader:** new package for loading preset packages ([6f5cb10](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/6f5cb102834cf0d726b962ea2ccace8c96f864d7))
* **preset, conventionalcommits:** add handling of issue prefixes ([#498](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/498)) ([85c17bb](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/85c17bb9b08329b1f7f4822429f43836e7d8f7c4))
* **preset:** add recommended-bump opts into presets ([60815b5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/60815b50bc68b50a8430c21ec0499273a4a1c402)), closes [#241](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/241)
* **pullRequest:** Allow to skip and parse pull request header ([a2e929f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a2e929fed07836f7ac3234b61c2490f318db60b6)), closes [#20](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/20)
* pulls in conventional-recommended-bump adding support for lerna ([#176](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/176)) ([840fe68](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/840fe6899c4c11de962282862f23369042724082))
* re-use parser options within each preset ([#335](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/335)) ([d3eaacf](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d3eaacfe642eb7e076e4879a3202cc60ca626b59)), closes [#241](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/241)
* **recommended-bump:** add `eslint` preset ([#256](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/256)) ([64abf07](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/64abf0797bdbbb7b0153c2d3e5dcb5f28def7ce0))
* **reference:** able to reference an issue without an action ([6474123](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/6474123c0062826575570a8c706574664e797714)), closes [#22](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/22)
* **reference:** expose prefix ([47df766](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/47df76661f0000ceede5720246ae6f80131129a7)), closes [#17](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/17)
* **references:** allow header to reference an issue ([df18a24](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/df18a247d4f37924bd1ab4ec6bc907085b3296e8))
* **references:** remove references that already appear in the subject ([a01e0ba](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a01e0ba400ac62cb2025894c15156f4f523dabbf))
* **references:** support other formats of references ([7c70213](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/7c7021324c3d67f8426c03fee02e6080c460a1ec)), closes [#4](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/4) [#8](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/8)
* **regex:** leading and trailing space for closes and breaks keywords are trimmed ([9639860](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/96398603dd11b6f89e2a59bfc3ceb24a08b79b2f))
* **regex:** matching JIRA-123 like references ([20f1f7a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/20f1f7ad323299eeb799850bb82557d522f74e34)), closes [#19](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/19)
* remove commit length restriction ([10a07f9](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/10a07f9f5915ce5fe6c61cfc742b0d66a64a4abb)), closes [#12](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/12)
* **reverse:** new options for commits that are poured reversely ([613651e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/613651e93929047e1d414854984a28d7acbbd518))
* **revert:** ignore reverted commits ([0f279ad](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0f279ad4629d2ba2ab175ef6219f941b2e8ffcdb)), closes [ajoslin/conventional-changelog#66](https://bitbucket.agile.bns/ajoslin/conventional-changelog/issues/66)
* **revert:** parse a commit that reverts ([2af7233](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/2af723378f32956baf6b09ec4128b2b381bef0b7)), closes [ajoslin/conventional-changelog#66](https://bitbucket.agile.bns/ajoslin/conventional-changelog/issues/66)
* rewrite this module ([8968f1b](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/8968f1b6e88ecf4131d6223ccde1e3faef7d192d))
* sort sections of CHANGELOG based on priority ([#513](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/513)) ([a3acc32](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a3acc3222135b17af0ee9785605d21b104ed0aef))
* **stream:** emmit an empty string to down stream if commit cannot be parsed ([76bf84e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/76bf84e453d8ab07640a5d07412f8da65e0f2596))
* **stream:** make the function return a through stream ([24032e7](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/24032e79bfb5ad51d1e417b82d5e147878d863ca)), closes [#1](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/1)
* support `conventional-changelog-*` presets in `conventional-recommended-bump` ([#270](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/270)) ([39240ad](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/39240add234e66fde3c19f0799d32fe7581bef82)), closes [#241](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/241)
* support slash in headerPattern default options ([93a547d](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/93a547d742634d8676f499cfa2a274bc3792d020))
* support squash commits ([#31](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/31)) ([fff60c0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fff60c0dfd5dead68571965f8633b85c87400750))
* **sync:** add the sync function ([82071c6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/82071c69acc7bc4ab41a7bc9b26832129cad2e4c)), closes [#13](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/13)
* **template:** bold scope in breaking change ([3b0bb11](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3b0bb119e3d555401d56c290c3e9d962456fd544))
* **templates:** if hash is nullish, do not display in CHANGELOG ([#664](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/664)) ([f10256c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f10256c635687de0a85c4db2bf06292902924f77))
* **template:** use context.repoUrl ([9276ab9](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/9276ab963985c8fe178b8bda430f41ad7a4748fe))
* the conventional-changelog ecosystem has been converted into a monorepo ([1be7d66](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1be7d6670aca2bb5e642bee266edc0dfc6ab4f17))
* **to:** `options.to` is honoured even if `options.from` is falsy ([cf414df](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cf414df89fd91ab84bc82202ab7817fc1785bd92)), closes [#2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/2)
* **transform:** add a transform option ([b05dc2e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b05dc2e5908549af2832f17354cdeb7091fdd8a3)), closes [#2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/2)
* **transform:** also pass context as an arg ([76b869d](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/76b869d88947325fea4b9878052cf63fc79ebdf7))
* **transform:** if returns a falsy value this commit is ignored ([9508ed6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/9508ed6f9d2aea0ff27b29c1414a67796a9037e2))
* **unreleased:** option to output or not unreleased changelog ([b448553](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b448553f964c15303aa3d6e7f087a7ffd4355e19)), closes [ajoslin/conventional-changelog#120](https://bitbucket.agile.bns/ajoslin/conventional-changelog/issues/120)
* update CLI tools to support lerna tags ([#175](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/175)) ([1fc5612](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1fc561217d79978b9d0248612b75e87c4b4a2d0b))
* use new api of `references` and `notes` ([4d27326](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/4d27326299d1f7307d98d9021bf8b30540823715))
* **verbose:** only log if verbose ([0d2921d](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0d2921d10471a109296fc9df5a7e1becba077fcf))
* **version:** is not a required field any more ([3790d8f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3790d8fb5d991fd6b1f6347f244faf727b9e146c))
* **version:** strip leading v by default ([43c2c7e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/43c2c7ed008a3913709b9645152688f22d0c5687))
* **warn:** optionally warn user what is wrong when commit cannot be parsed ([32b3cda](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/32b3cdaa161f71f5fb21d2d2f01f9785b6a7d0a7))
* **writerOpts.transform:** do not discard commit if there is BREAKING CHANGE ([e6fded5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e6fded5ce4c3e00581399c93c5aacd3f25ccb325)), closes [ajoslin/conventional-changelog#127](https://bitbucket.agile.bns/ajoslin/conventional-changelog/issues/127) [angular/angular#5672](https://bitbucket.agile.bns/angular/angular/issues/5672) [angular/angular#5762](https://bitbucket.agile.bns/angular/angular/issues/5762)


### Bug Fixes

* `tagPrefix` was not passed properly in conventional-changelog-core ([#300](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/300)) ([be48f70](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/be48f700fc0907a9535f0cd45172525d5746697d))
* add add-bang-notes to files list ([7e4e4d2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/7e4e4d2ef38537f55926aa1d91eb482d574609c1))
* add missing context flag ([#361](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/361)) ([0cf43f4](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0cf43f448ee191b91df23e9e84bf5ed951dcf2b5)), closes [#355](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/355)
* add types for cli flags ([#551](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/551)) ([bf1d64a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/bf1d64aeaf8f262d4b2beec02d2aebb78df7343b))
* address discrepancies between cc preset and spec ([#429](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/429)) ([18f71d2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/18f71d228c9676af13b736cb46614f23b66e796e))
* adhere to config spec ([#432](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/432)) ([4eb1f55](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/4eb1f558d6b855e0caf66cc294407e6ab2527d75))
* always parse references ([e84a9ae](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e84a9ae2cca5d7713653bff7edd4d7dc1a86c028)), closes [#248](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/248)
* **angular:** smarter username detection ([#219](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/219)) ([f1b4847](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f1b48476dbf3623a7c139777c388de7a898cc916)), closes [#218](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/218)
* bad release of conventional-changelog-writer ([b5da9af](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b5da9afe056ad4597c2503e28060cc6c2f28b19a))
* bad release of git-semver-tags ([8827ae4](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/8827ae418adf8bd400ce879548c732812e5934ea))
* bug in unstableTagTest causing a mismatch on beta release higher then beta-9 ([#679](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/679)) ([cd4c726](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cd4c726b1ca227a132ec2eadac5d0cfdd75d9e81))
* call gitRawCommits with ranges [tag1..tag2, tag2..tag3, ..., tagX..HEAD] to make sure commits are returned in right order. ([2fba5c7](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/2fba5c7a02e0e34093a6bd9a01109457db9b84c5)), closes [#408](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/408)
* **cli.js:** fix issue where standard conventional-changelog options are not passed into options object ([#380](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/380)) ([86ae571](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/86ae571027a23de4325499b1eab0ad9d26429ea3))
* **cli:** commit can be split when testing a commit file ([f3b3a3f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f3b3a3f44e6dbf768511621204fa9065c08c2d2e))
* **cli:** error handling for ENOENT is fixed ([3c92233](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3c92233e717ea7dd35de6555ee798217719953ca))
* **cli:** fix "undefined" in json string ([0680e42](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0680e420b59f3b111bd7a8ed2f73597837f157a2))
* **cli:** options format ([41c813b](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/41c813b8ddeac0b721daa70d43327dc8f2758d54))
* **cli:** options format ([491357e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/491357e7ebce93cb9a316f83ee5d2546c9441e8c))
* **cli:** pass `--tag-prefix` option to core ([#345](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/345)) ([2151fce](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/2151fcef808f32ec0536ae87edad3c000e1a5af5))
* **cli:** require file with absolute path ([fe2b5fe](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fe2b5feb5a57935b7eff36667586bb297c1f92dc)), closes [#13](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/13)
* **cli:** set options.config to loaded custom config for processing ([3d8b243](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3d8b2438e51f0aa7bf8d3c5eb975e3aa643b50cf)), closes [#227](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/227)
* **cli:** should not contain a `\n` at the end ([4044958](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/40449588e039665d76a33e44084ad9730f306696))
* **cli:** show optional options properly ([28c0f01](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/28c0f010bc506a3f8b837e6e6025f7b8e086eb09))
* **cli:** use absolute path to require context and options ([08808fe](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/08808fe05f0e26acd080d7e5defbe75721e1c6cd))
* **cli:** when it is not tty, it should exit if errors ([aa8708c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/aa8708cc253a16231fc0e7d01443526d0420441e))
* **close:** should close stream if there is no data and no error ([63c753e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/63c753ea0ba43cbf23f898e0799f427b85e793e2))
* **cmd:** add a space before other args ([49c4739](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/49c4739708fe1936d5b1e7e34d7cf49800741dfb))
* **context.version:** only valid a semver can decide `context.isPatch` ([8dbc53a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/8dbc53a5f3e724daca074dad150bccb35f1b0088))
* **context:** auto link references if repoUrl ([d5d66f3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d5d66f3da7e82cb45993f27c190f9fffae3b51cd))
* conventional commits not working ([28ea3af](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/28ea3afe6c46628281c3d317503c87fb9f1f7a5c))
* conventional-changelog-core version ([6d234bd](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/6d234bd2c480c561c17d3f33397f7a2c7e6427c6))
* **conventional-changelog-core:** check if HEAD ref exists before using it ([#578](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/578)) ([a49b19a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a49b19a8c4b1d13559ebb02020d4f623189fae6a))
* **conventional-changelog-core:** fix duplicated commits when `from` is specified ([#573](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/573)) ([287a801](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/287a801ecde0a3856b6531cef53474d3a8b808b3)), closes [#567](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/567)
* **conventional-changelog-core:** read current version properly when tagPrefix is provided ([#563](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/563)) ([1deb63f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1deb63fff9a07848c3964264c5ef4d082d654223)), closes [#562](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/562) [#337](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/337)
* **conventional-changelog:** support scoped presets ([0f08267](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0f08267a09f3406d5c51d9a5e207535db6b72736))
* **conventional-commits-parser:** add breaking change notes if header match `breakingHeaderPattern` ([#544](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/544)) ([efdf3cb](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/efdf3cbc9de3278b180a48beebb74e596e3c5f94))
* **conventional-commits-parser:** add missing separator pipe to non tty parser ([#546](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/546)) ([c522743](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c5227437b0b300f30a57e8ba5df2a8ab8d163af0))
* **conventional-commits-parser:** downgrade is-text-path due to node 6 incompatibility ([#536](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/536)) ([3aa2637](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3aa2637a1c65bb4db3d8bf2c6ce17e6f5abe1ca1))
* **conventional-commits-parser:** ignore comments  ([#231](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/231)) ([9db53e3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/9db53e351651a3e77dd7928cdcaafaeec3affcf3)), closes [#224](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/224)
* **conventional-recommended-bump:** include missing file in publishing ([1481c05](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1481c053873606736c161c4dcdd66e0b811ef697))
* **currentTag:** if unreleased, currentTag should be last commit hash ([fb9358c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fb9358cfbac33fc1f96dae9c32117795fc2a82a3))
* **date:** should use committerDate not authorDate ([fbdf73d](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fbdf73d784b6391ccbab93a40e7fe2af0b060ed2))
* **default:** firstCommit and lastCommit should based on original unfiltered commits ([3aed9ca](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3aed9ca836aaf703a1ec994fe898bb23e0b10529)), closes [#2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/2)
* **defaults:** context tags ([e1b938b](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e1b938b0e9af3bfb5f8f3bfe63e24b264ebc72fd))
* **deps, cli:** bumps (minor + patch) lodash in conventional-changelog-cli ([#501](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/501)) ([50212e6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/50212e623af3e9326d0234f40fa090b9150b8636)), closes [#486](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/486)
* **deps:** add missing better-than-before ([5903b58](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/5903b5875085122ec3602c8b9393de8e40da118f))
* **deps:** address CVE in meow ([#642](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/642)) ([46311d2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/46311d2932b367f370d06c4e447b8dcf4bc4e83f))
* **deps:** concat-stream should be in devdeps ([e90881c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e90881ce673eb892ca21102a1bb8c5489770abfb))
* **deps:** require split2 ([59db605](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/59db605a988a852b5fb7e2fa591f75b67a16e006))
* **deps:** require split2 ([1941c37](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1941c374381688aff57ad2f4c20e6bd8e971bf01))
* **deps:** update dependency compare-func to v2 ([#647](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/647)) ([de4f630](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/de4f6309403ca0d46b7c6235052f4dca61ea15bc))
* **deps:** update dependency concat-stream to v2 ([#401](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/401)) ([4c09bfc](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/4c09bfc2e3aef75c6e92d4704c74a5c64e2c00fe))
* **deps:** update dependency conventional-changelog-writer to v5 ([#731](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/731)) ([b5951fb](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b5951fb5c58ada8d480d17213703d717acb1cd42))
* **deps:** update dependency figures to v3 ([#453](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/453)) ([099b5b5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/099b5b58138139ca6d2a9ade58f0c6282aef9ad4))
* **deps:** update dependency git-raw-commits to v2.0.8 ([#723](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/723)) ([9682305](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/968230536914a680237e830ccc8e125c56b0f0aa))
* **deps:** update dependency is-text-path to v2 ([#455](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/455)) ([0f40ec3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0f40ec3de10c3b66f6ebd81721e9fdd763706cb2))
* **deps:** update dependency lodash to v4.17.13 [security] ([#497](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/497)) ([8cb57f0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/8cb57f07675f9d8093f475e3cc7e178c38ee00ad))
* **deps:** update dependency normalize-package-data to v3 ([#687](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/687)) ([7b6ec0a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/7b6ec0add30915bc1569f82a007bb4d1d6df8e3e))
* **deps:** update dependency read-pkg-up to v7 and read-pkg to v5 ([#526](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/526)) ([cc1fa5d](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cc1fa5d9fd362c470f7d35337a7aabb40e0a0f91))
* **deps:** update dependency rimraf to v3 ([#514](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/514)) ([c7e1706](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c7e17062a7a38a194164c47d0e88fcbe3fb6490c))
* **deps:** update dependency semver to v6 ([#458](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/458)) ([efaa7bb](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/efaa7bb651fe1b6de047163fc9db8e5d69f0a6e9))
* **deps:** update dependency tempfile to v3 ([#459](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/459)) ([c0bac28](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c0bac28c45dd4d1516330b83d12f16f6ad88664b))
* **deps:** update dependency through2 to v3 ([#392](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/392)) ([26fe91f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/26fe91f5da4e001b9ab0908b7d3415bbad9bb7d9))
* **deps:** update dependency through2 to v4 ([#657](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/657)) ([7ae618c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/7ae618c81491841e5b1d796d3933aac0c54bc312))
* **deps:** update lodash to fix security issues ([#535](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/535)) ([ac43f51](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/ac43f51de1f3b597c32f7f8442917a2d06199018))
* **deps:** update yargs-parser to move off a flagged-vulnerable version. ([#635](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/635)) ([aafc0f0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/aafc0f00412c3e4b23b8418300e5a570a48fe24d))
* **doFlush:** correct logic ([38e3c03](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/38e3c0382c62511bd776db4d93ecbc36d2864198)), closes [#19](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/19)
* **doFlush:** one it is the only potential release ([3d600cf](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3d600cfb5ca9ca15b78d8a84a032cf4c938ba4d0))
* don't require 'host' and 'repository' when deciding whether to render URLs ([#447](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/447)) ([83dff7a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/83dff7aff782a2a24685f1a0b9c42ffb98ec6a3e))
* don't use multiple H1 tags ([#440](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/440)) ([3d79263](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3d792639815e4c4ae7758e0e84ba72a9cb535f37))
* Downgrade node 10.x dependency to 6.9.0 dependency ([#437](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/437)) ([ded5a30](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/ded5a304cd0b53100f94fff6b225c7178f5eb449))
* drop compare-func making sort consistent across node versions ([#729](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/729)) ([e0081a8](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e0081a829133891e2def4a7b7ee5fa25f1440049))
* **err:** catch any possible error ([c934f50](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c934f50cfab1c1928934d4311d5bbbec07036124))
* **err:** emitted error should not be read only ([58a3a24](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/58a3a246fa99366ba675dcf9fc644c7bd894c4f3))
* **error:** better error handling ([38cc78e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/38cc78e71cc6375471847333d363b77c6f842797)), closes [ajoslin/conventional-changelog#130](https://bitbucket.agile.bns/ajoslin/conventional-changelog/issues/130)
* **error:** change error type and wordings ([d8be5e5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d8be5e548922e3cf45c4715c620b191a1a16d8d4))
* **error:** error should be emitted ([d766685](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d7666850b6729a45f4eb1f15e3326b87e86fe66c))
* **error:** handle errors properly ([587e1d0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/587e1d01a82dd15d6958e7a017813e29c82555f3))
* **error:** handle errors properly ([bde1200](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/bde1200027e3f26da14c6dcce09fb0c7c2add908))
* **events:** emit proper events ([2911647](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/291164714c1c2b616793710d760063df6ce78421))
* **filter:** only remove commits that reverted commits in the scope ([#226](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/226)) ([461dae6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/461dae6fa3f8566cca6049bfb7237932d95773b2))
* **filter:** replace `is-subset` with `lodash.ismatch` ([#377](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/377)) ([fbcc92e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fbcc92ec0f480c089f9ee45cc824ab6e628a01f0))
* **firstRelease:** correct logic ([ccc02e1](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/ccc02e1e162ce0d4dbe276427a5edc6b716b8abc))
* fix broken release of conventional-recommended-bump ([d9267e8](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d9267e86705bac4d7672497a9c9abe62212cb56d))
* Fix plurality of "are" vs. "is" ([#331](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/331)) ([027e778](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/027e77812d11c595bf3593b78669b265f174e5f4))
* fixing conventional-changelog-core verion - using github link instead of version number ([2843ffb](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/2843ffba2bbbe753fb30960fa600cae262550e13))
* fixing dependecy version ([a389c08](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a389c08e7b21ab9f6579dc9b4c5e0d6e3b4feb7d))
* fixing get-pkg-repo ([25275b8](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/25275b895f04e506ff7eef2cc40f516046ca86e5))
* fixing get-pkg-repo verion - using github link instead of version number ([214bb52](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/214bb5241127ef24fa72d04c70f628b61ba5e554))
* fixing require for get-pkg-repo ([cb33c27](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cb33c278be1564b38f687afe2a1e61ffebf0362a))
* fixing requiring modules ([c55782f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c55782fd8dca3bff14a86bb476986ec35b10f907))
* fixing some tests ([deb2eab](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/deb2eab9c759a0b013d28614c1f6d3d4f7f921f3))
* **footer:** notes contains more than one paragraphs after references ([d744ec7](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d744ec771dcc333c54978d035be5097e02a10579))
* **functionify:** should not change falsy values ([1aed002](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1aed002dda1e200c8eaeaf6a521d4cfd56423992))
* **generateOn:** should pass the transformed commit ([2b6cc6c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/2b6cc6cac5b33bee951eb1ee2a26344286131769))
* **git-semver-tags:** change --tagPrefix flag to --tag-prefix ([#566](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/566)) ([490cda6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/490cda6cff74abe63617f982765b63aebdf3b4b6)), closes [#553](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/553)
* **git:** allow the command to pass on windows ([ee2f4d3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/ee2f4d3b9c6760b2dc3790f830ce1bf3410b55a5)), closes [#4](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/4) [ajoslin/conventional-changelog#64](https://bitbucket.agile.bns/ajoslin/conventional-changelog/issues/64)
* **git:** wrap params `from..to` in double-quotes for windows ([02b7c19](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/02b7c190ffeebb9e22b3ae6c337903aa17e79ba6))
* **headerCorrespondence:** string value for cli ([fb774fc](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fb774fc4dc1ddc37c2fec287f63afdbbef0b40c7))
* **headerPattern:** change how capturing groups works ([fe1fe0c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fe1fe0c3cfe785e0f0cc44bcc6c63b42035c4001))
* **host:** auto removes "/" at the end of `options.host` ([2bdadf0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/2bdadf09cd29e6e56080d05ab0d474c5f4a547ac))
* if ! and BREAKING CHANGE were used, notes would populate twice ([#446](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/446)) ([63d8cbe](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/63d8cbedd24d957c759865211dd2341fd4a3e1f2))
* ignore gpg lines ([#685](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/685)) ([f8fcbc2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f8fcbc2e8b0834c29178ace6382b438a020ad828))
* **infile:** do not print the latest release twice if infile ENOENT ([cfe4c64](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cfe4c6427880f0d25944262cdbade4c15c9aa0e7))
* **issuePrefixes:** should return noMatch if falsy ([72db2bf](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/72db2bf3d72f74f864971a7103dbe9b64e855570))
* **keyCommit:** all fields of `keyCommit` overwrites `context` ([63296b5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/63296b52accd8c5aad4723a7da1028593e27a799)), closes [#5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/5)
* **lerna tags:** support multi-digit version tags ([#223](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/223)) ([67012fb](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/67012fb655a7d968d82185685971ca246751ab0b))
* **linkReferences:** can be changed to `false` ([a56f9fd](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a56f9fd363df2b63bc0d3efd70d3410ec333cd5d))
* linting ([33ac525](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/33ac525e294aca4a3b736a67d5b0ae17129027a1))
* **maxBuffer:** Infinity ([03fb581](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/03fb58172cd1af99ed291ade7f8d95b1a8425101)), closes [#5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/5)
* **mention:** fix mention matching ([965986b](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/965986b2c8d9dcc94d5dd0d5b14f6b5957479aa2)), closes [#26](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/26)
* **mergeConfig:** respect issuePrefixes option ([9cc54a1](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/9cc54a1e99a9be26043be46ecd68f6102a4989bf)), closes [#6](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/6) [#8](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/8)
* **newlines:** preserve newlines in a part ([06b8c7c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/06b8c7c2b20dc9947186c1b56605bcdd9e272d52)), closes [#15](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/15)
* normalize git show signature option to false ([#671](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/671)) ([a0b348c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a0b348c7a74ba49bb07053ed1d25c2053a7c3b1a)), closes [conventional-changelog/commitlint#2118](https://bitbucket.agile.bns/conventional-changelog/commitlint/issues/2118)
* **notes:** do not include reverted notes ([4e60fe2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/4e60fe2026b290f5ac5986de44da223ee18da99e))
* **notes:** note keywords must appear at the beginning of a sentence ([5a2059e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/5a2059ee79aa7fe1f764060be8cd03c4be6e159f)), closes [#23](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/23)
* **notesSort:** defaults to sort on `text` ([3511ffb](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3511ffb7bb684d783c64b17a246073304fe864d5))
* **oldNode:** git remote origin url feature is only available under node>=4 ([db1fe72](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/db1fe725aabe1ce5824cf9fd7ade11b856e656ff))
* **options:** only apply default transform in certain conditions ([6080181](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/60801815eb5900d8a774ecc1e14033a8c1e056e3))
* **options:** should fallback to default if supplied value is falsy ([4cfa812](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/4cfa81257ecac46563d3541a10f376040e43ab35))
* **parser:** do not trim spaces but newlines ([1e8c4c5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1e8c4c52b659dc50d12511f0c089b7e4d877c93f))
* **parser:** it returns null if there is no header ([8571c9e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/8571c9eb6446c150333f6633c0965f4009c80d92))
* **partials:** only register if its a string ([915cbeb](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/915cbebe83fde86a8390b5bbaae5ec069f426ee2))
* pass config to parserOpts and writerOpts ([73c7a1b](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/73c7a1b92c2a47c498f42972acbffa156172a341))
* pin git-raw-commits until I have publication rights ([e41777c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e41777c4ed56f911cef4305642899910b265e987))
* preset load error message should handle objects ([fb4a8d1](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fb4a8d1bb7e2142381ea6c11fed8615fd089f018))
* **preset-loader:** don't namespace exported function ([#278](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/278)) ([89880cb](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/89880cb3a7aa15c8835e9198aad2b6a4bafc50a3))
* **preset-loader:** fix handling conventionalcommits preset without config object ([6425972](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/64259723085eaa21a281391acb9fc0704319c8b3)), closes [#512](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/512)
* **preset, conventionalcommits:** Ensure proper substitutions for the conventionalcommit preset by using commit context for values where possible. ([#463](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/463)) ([0b7ed0b](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0b7ed0b73b6728173c8df744abdfa4466a7f0cc5))
* **preset, conventionalcommits:** fix handling conventionalcommits preset without config object ([c0566ce](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c0566ce05c03c6274d6efcb01a2eff42e660a9bc)), closes [#512](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/512)
* **preset, conventionalcommits:** pass issuePrefixes to parser ([#510](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/510)) ([958d243](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/958d243c3f1702eea91ddca40c1550d12fd81aa0))
* **preset, eslint:** display short tag in release notes ([b63a5ff](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b63a5ffdf540cdaff2013e4465f640ef5a8f5013)), closes [#313](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/313)
* **preset:angular:** scoped npm packages should not be seen as GitHub username ([#394](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/394)) ([e332ef0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e332ef0d6dea8dd918ea274e5dae2a3f2b96a313))
* **preset:** ESLint recommended-bump is always "patch" ([#371](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/371)) ([35e279d](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/35e279d40603b0969c6d622514f5c0984c5bf309)), closes [/github.com/conventional-changelog/conventional-changelog/blob/ce1fd981f88ce201e996dfa833e4682de3aafcdd/packages/conventional-changelog-eslint/conventional-recommended-bump.js#L32-L35](https://bitbucket.agile.bns/mrvl//github.com/conventional-changelog/conventional-changelog/blob/ce1fd981f88ce201e996dfa833e4682de3aafcdd/packages/conventional-changelog-eslint/conventional-recommended-bump.js/issues/L32-L35)
* **preset:** recommended-bump ESLint preset ([#295](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/295)) ([acf9c19](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/acf9c193d6930d0ed2c89fc1b0990a784633dfb3)), closes [#270](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/270) [#241](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/241)
* Recommend a patch bump for features when preMajor is enabled ([#452](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/452)) ([3d0a520](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3d0a52036a82ee11415ca777c005d84fa4169d2f))
* **regex:** do not treat it as note if there are texts after keywords ([571b03e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/571b03e0b3d564abdc7ac6530127b92c26a8ec10))
* **regex:** make getReferencePartsRegex stricter ([62adf54](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/62adf5414612bee5dad5e4c242e657ea083cc91e)), closes [#27](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/27) [#30](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/30) [#27](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/27) [#28](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/28)
* removing postinstall script ([cdce534](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cdce53409658cc4c73063a7d22c6fd06d7e1711c))
* **reverse:** should be the other way ([b4156e3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b4156e32ccba20a6a372158ccb32974808384581))
* revert previous change ([2f4530f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/2f4530f06cb8f76e83c5f9c7af8126952b4dc8f3))
* revertPattern match default git revert format ([#545](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/545)) ([fe449f8](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fe449f899567574a36d1819b313e2caa899052ff))
* **revertPattern:** correct regex ([8628983](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/862898305cc827fa0b929e4dc6dcbf0c64ce04e0))
* **template:** commit template markdown ([0949b5a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/0949b5acdb3de9bc1d94ca256535281691b4f2ea))
* **template:** default commit template should handle unkown host ([d1ed4fc](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d1ed4fcfefa0f338e45ed3d141c689a98612f8ea))
* **template:** remove an extra newline in footer ([f6180c5](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f6180c5462a6d4acadcccf5ce0d8b8cd75cfac21))
* **templates:** generate correct url if only host exists ([35f1799](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/35f1799c1a9004aa5282aaefd859a702bf5b2556))
* **template:** should not html escape ([e4e33ae](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e4e33ae3b1a81a4503946cf45ab65d7fde0913a9)), closes [ajoslin/conventional-changelog#65](https://bitbucket.agile.bns/ajoslin/conventional-changelog/issues/65)
* **templates:** incase partial is empty also don't ignore default partials ([d90fb65](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/d90fb65f94bd35ed07994b6812b3de3d6f9ce09e))
* **template:** tweak ([ef6996a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/ef6996a8b435724db295efcf0bdea5019497dad6))
* **template:** whitespace ([4b09854](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/4b098540c51ea47eec38b71b79165bf0e32a2ce3))
* **template:** wrong version link if no host ([b28b9a1](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b28b9a1ee6042fcfdb1a7d0b9fde35f5e793dc57)), closes [#8](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/8)
* **transform:** do not strip leading v ([8e2da57](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/8e2da576cd57fc730f4e4d770a3e5432b0caab51))
* **transform:** should work if any field is missing ([fd413ed](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fd413edea7720c2f62c7646d6f81d4e8b8be9356))
* truncate after scissors line ([#267](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/267)) ([e09df10](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/e09df10ec4736e53ff3343215e973fba4452fc4f))
* **unknownHost:** default context.repository ([c41ddd9](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/c41ddd98eb0a5eb0bd0ae47d2b02fdc48ab42705))
* **unreleased:** now it can output unreleased commits ([03cb05e](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/03cb05ec7869df136ae8242bb5c1f7461069b777))
* update to reference conventional-changelog org ([310bbef](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/310bbef53bef7d36b137a4b4ed1eb8bd1b03519d))
* Upgrade to Lerna 3, fix Node.js v11 error ([#385](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/385)) ([cdef282](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cdef2828e34132020845cc6db23077c2c9c8dc1c))
* use full commit hash in commit link ([7a60dec](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/7a60decb6979efb5026e399e962313e69b005b22)), closes [#476](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/476)
* **util:** remove an accidentally commited file ([3710a8c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/3710a8c080f4490ae1599578e58263a72d24a33a))
* **warn:** is `gutil.log` ([4578d80](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/4578d8087233652cdad3ee64a287cee4e6bfda15))
* **warn:** should tell which commit cannot be parsed ([04b0a9b](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/04b0a9b0e3956fea0cd7d9ac1f25fe68dcb55535))
* **windows:** escape command percent signs ([7774c7b](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/7774c7b0e1b1129b7369057fb7c9cd2bdfb4c9cd)), closes [#10](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/10)
* **windows:** use execFile for executing git ([5d0c2c7](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/5d0c2c7752bb937d526cdaf9f5e6a770a8e1bf5f)), closes [#11](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/11)
* **writer:** normalize release headings ([#237](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/237)) ([9e87dc3](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/9e87dc32b4ffc5202661e674f20e5901feb1ac6f)), closes [/github.com/conventional-changelog/conventional-changelog/issues/214#issuecomment-326681934](https://bitbucket.agile.bns/mrvl//github.com/conventional-changelog/conventional-changelog/issues/214/issues/issuecomment-326681934)


* [Angular Package] Adapt to new Angular Commit Conventions (#296) ([03f0210](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/03f0210e42dff58689ddf182694a8a6ca26e526b)), closes [#296](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/296)
* **breaks:** change `breaks` to `notes` ([5189a61](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/5189a616c5ce1f1440649fcb1a61274bdaf7a24f)), closes [#2](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/2)
* **deps:** bump ([1b8c4dc](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/1b8c4dc24249516baf977514d0d5e73515e1137f))
* drop support for Node 6 ([#558](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/558)) ([fd80738](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/fd80738a46760753a61cb6929bd899ada1ab1e04))
* drop support for Node 8 ([#599](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/599)) ([b9f5057](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/b9f50573f292ea29ff51627646ca7825bf182d52))
* force breaking change ([f6d506d](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/f6d506de038a6a86a1915f85e7cef79a277af2b6))
* init ([ae118df](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/ae118df3fbc037664cf4212ce07efd4265dd62c4))
* init ([a529841](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/a529841e1b936d265d789367828e9b2be8daf0c5))
* **merge:** pull-request should be merge ([4e7c61c](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/4e7c61cb3388644e94e405deacae42cb59165ce9))
* modify gitSemverTags to take options first ([#390](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/390)) ([dc8aeda](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/dc8aedae0519045bfcb2e649167f0f6bfb2f4a30))
* **package:** set Node requirement to oldest supported LTS ([#329](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/329)) ([cae2fe0](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/cae2fe0491bc7d7eef77d790cc65b86fe5070f1b))
* **regex:** regex now takes `options` ([eea319a](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/eea319a2b9e4b2a0a1245519de1dba2e6f8735ea))
* remove anchor from header templates ([#301](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/301)) ([346f24f](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/commit/346f24f0f8d92b64ed62658796d1876a52ec3ab3)), closes [#186](https://bitbucket.agile.bns/mrvl/cdb-lib-credit-p9-connector/issues/186)

### [4.2.2](https://www.github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.2.1...v4.2.2) (2020-12-30)


### Bug Fixes

* **deps:** update dependency git-raw-commits to v2.0.8 ([#723](https://www.github.com/conventional-changelog/conventional-changelog/issues/723)) ([9682305](https://www.github.com/conventional-changelog/conventional-changelog/commit/968230536914a680237e830ccc8e125c56b0f0aa))

## [4.2.1](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.2.0...conventional-changelog-core@4.2.1) (2020-11-05)


### Bug Fixes

* **deps:** update dependency normalize-package-data to v3 ([#687](https://github.com/conventional-changelog/conventional-changelog/issues/687)) ([7b6ec0a](https://github.com/conventional-changelog/conventional-changelog/commit/7b6ec0add30915bc1569f82a007bb4d1d6df8e3e))
* **deps:** update dependency through2 to v4 ([#657](https://github.com/conventional-changelog/conventional-changelog/issues/657)) ([7ae618c](https://github.com/conventional-changelog/conventional-changelog/commit/7ae618c81491841e5b1d796d3933aac0c54bc312))





# [4.2.0](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.1.8...conventional-changelog-core@4.2.0) (2020-08-12)


### Features

* add support for '--skip-unstable' option ([#656](https://github.com/conventional-changelog/conventional-changelog/issues/656)) ([#656](https://github.com/conventional-changelog/conventional-changelog/issues/656)) ([0679d7a](https://github.com/conventional-changelog/conventional-changelog/commit/0679d7a1d7a8715918326f31ec3f6168c2341fd6))





## [4.1.8](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.1.7...conventional-changelog-core@4.1.8) (2020-06-20)

**Note:** Version bump only for package conventional-changelog-core





## [4.1.7](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.1.6...conventional-changelog-core@4.1.7) (2020-05-08)

**Note:** Version bump only for package conventional-changelog-core





## [4.1.6](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.1.2...conventional-changelog-core@4.1.6) (2020-05-08)


### Bug Fixes

* **conventional-changelog-core:** check if HEAD ref exists before using it ([#578](https://github.com/conventional-changelog/conventional-changelog/issues/578)) ([a49b19a](https://github.com/conventional-changelog/conventional-changelog/commit/a49b19a8c4b1d13559ebb02020d4f623189fae6a))
* **conventional-changelog-core:** fix duplicated commits when `from` is specified ([#573](https://github.com/conventional-changelog/conventional-changelog/issues/573)) ([287a801](https://github.com/conventional-changelog/conventional-changelog/commit/287a801ecde0a3856b6531cef53474d3a8b808b3)), closes [#567](https://github.com/conventional-changelog/conventional-changelog/issues/567)
* **conventional-changelog-core:** read current version properly when tagPrefix is provided ([#563](https://github.com/conventional-changelog/conventional-changelog/issues/563)) ([1deb63f](https://github.com/conventional-changelog/conventional-changelog/commit/1deb63fff9a07848c3964264c5ef4d082d654223)), closes [#562](https://github.com/conventional-changelog/conventional-changelog/issues/562) [#337](https://github.com/conventional-changelog/conventional-changelog/issues/337)





## [4.1.2](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.1.1...conventional-changelog-core@4.1.2) (2019-11-21)


### Bug Fixes

* call gitRawCommits with ranges [tag1..tag2, tag2..tag3, ..., tagX..HEAD] to make sure commits are returned in right order. ([2fba5c7](https://github.com/conventional-changelog/conventional-changelog/commit/2fba5c7a02e0e34093a6bd9a01109457db9b84c5)), closes [#408](https://github.com/conventional-changelog/conventional-changelog/issues/408)





## [4.1.1](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.1.0...conventional-changelog-core@4.1.1) (2019-11-14)

**Note:** Version bump only for package conventional-changelog-core





# [4.1.0](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.0.3...conventional-changelog-core@4.1.0) (2019-11-07)


### Features

* **conventional-changelog-core:** provide facility to define gitExecOpts. ([#480](https://github.com/conventional-changelog/conventional-changelog/issues/480)) ([814f878](https://github.com/conventional-changelog/conventional-changelog/commit/814f878054ca3c9ec00c3147478eb1e6a2762e9a))





## [4.0.3](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.0.2...conventional-changelog-core@4.0.3) (2019-10-24)


### Bug Fixes

* **deps:** update lodash to fix security issues ([#535](https://github.com/conventional-changelog/conventional-changelog/issues/535)) ([ac43f51](https://github.com/conventional-changelog/conventional-changelog/commit/ac43f51de1f3b597c32f7f8442917a2d06199018))





## [4.0.1](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@4.0.0...conventional-changelog-core@4.0.1) (2019-10-02)

**Note:** Version bump only for package conventional-changelog-core





# [4.0.0](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.2.3...conventional-changelog-core@4.0.0) (2019-07-29)


* refactor!: modify gitSemverTags to take options first (#390) ([dc8aeda](https://github.com/conventional-changelog/conventional-changelog/commit/dc8aeda)), closes [#390](https://github.com/conventional-changelog/conventional-changelog/issues/390)


### BREAKING CHANGES

* gitSemverTags now takes options followed by callback.





## [3.2.3](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.2.2...conventional-changelog-core@3.2.3) (2019-05-18)

**Note:** Version bump only for package conventional-changelog-core





## [3.2.2](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.2.1...conventional-changelog-core@3.2.2) (2019-04-11)

**Note:** Version bump only for package conventional-changelog-core





## [3.2.1](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.2.0...conventional-changelog-core@3.2.1) (2019-04-11)

**Note:** Version bump only for package conventional-changelog-core





# [3.2.0](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.1.6...conventional-changelog-core@3.2.0) (2019-04-10)


### Bug Fixes

* **deps:** update dependency through2 to v3 ([#392](https://github.com/conventional-changelog/conventional-changelog/issues/392)) ([26fe91f](https://github.com/conventional-changelog/conventional-changelog/commit/26fe91f))


### Features

* creating highly configurable preset, based on conventionalcommits.org ([#421](https://github.com/conventional-changelog/conventional-changelog/issues/421)) ([f2fb240](https://github.com/conventional-changelog/conventional-changelog/commit/f2fb240))





## [3.1.6](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.1.5...conventional-changelog-core@3.1.6) (2019-02-14)

**Note:** Version bump only for package conventional-changelog-core





## [3.1.5](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.1.4...conventional-changelog-core@3.1.5) (2018-11-01)

**Note:** Version bump only for package conventional-changelog-core





## [3.1.4](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.1.3...conventional-changelog-core@3.1.4) (2018-11-01)

**Note:** Version bump only for package conventional-changelog-core





## [3.1.3](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.1.2...conventional-changelog-core@3.1.3) (2018-11-01)


### Bug Fixes

* pin git-raw-commits until I have publication rights ([e41777c](https://github.com/conventional-changelog/conventional-changelog/commit/e41777c))





## [3.1.2](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.1.1...conventional-changelog-core@3.1.2) (2018-11-01)

**Note:** Version bump only for package conventional-changelog-core





## [3.1.1](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.1.0...conventional-changelog-core@3.1.1) (2018-11-01)


### Bug Fixes

* Upgrade to Lerna 3, fix Node.js v11 error ([#385](https://github.com/conventional-changelog/conventional-changelog/issues/385)) ([cdef282](https://github.com/conventional-changelog/conventional-changelog/commit/cdef282))





<a name="3.1.0"></a>
# [3.1.0](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@3.0.0...conventional-changelog-core@3.1.0) (2018-08-21)


### Features

* ability to reset changelog from scratch ([#350](https://github.com/conventional-changelog/conventional-changelog/issues/350)) ([0eea0af](https://github.com/conventional-changelog/conventional-changelog/commit/0eea0af))




<a name="3.0.0"></a>
# [3.0.0](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@2.0.11...conventional-changelog-core@3.0.0) (2018-05-29)


### Chores

* **package:** set Node requirement to oldest supported LTS ([#329](https://github.com/conventional-changelog/conventional-changelog/issues/329)) ([cae2fe0](https://github.com/conventional-changelog/conventional-changelog/commit/cae2fe0))


### BREAKING CHANGES

* **package:** Set the package's minimum required Node version to be the oldest LTS
currently supported by the Node Release working group. At this time,
that is Node 6 (which is in its Maintenance LTS phase).




<a name="2.0.11"></a>
## [2.0.11](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@2.0.10...conventional-changelog-core@2.0.11) (2018-04-16)


### Bug Fixes

* `tagPrefix` was not passed properly in conventional-changelog-core ([#300](https://github.com/conventional-changelog/conventional-changelog/issues/300)) ([be48f70](https://github.com/conventional-changelog/conventional-changelog/commit/be48f70))




<a name="2.0.10"></a>
## [2.0.10](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@2.0.9...conventional-changelog-core@2.0.10) (2018-03-28)




**Note:** Version bump only for package conventional-changelog-core

<a name="2.0.9"></a>
## [2.0.9](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@2.0.8...conventional-changelog-core@2.0.9) (2018-03-27)




**Note:** Version bump only for package conventional-changelog-core

<a name="2.0.8"></a>
## [2.0.8](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@2.0.7...conventional-changelog-core@2.0.8) (2018-03-27)




**Note:** Version bump only for package conventional-changelog-core

<a name="2.0.7"></a>
## [2.0.7](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@2.0.6...conventional-changelog-core@2.0.7) (2018-03-27)




**Note:** Version bump only for package conventional-changelog-core

<a name="2.0.6"></a>
## [2.0.6](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@2.0.5...conventional-changelog-core@2.0.6) (2018-03-22)




**Note:** Version bump only for package conventional-changelog-core

<a name="2.0.5"></a>
## [2.0.5](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@2.0.4...conventional-changelog-core@2.0.5) (2018-02-24)




**Note:** Version bump only for package conventional-changelog-core

<a name="2.0.4"></a>
## [2.0.4](https://github.com/conventional-changelog/conventional-changelog/compare/conventional-changelog-core@2.0.3...conventional-changelog-core@2.0.4) (2018-02-20)




**Note:** Version bump only for package conventional-changelog-core

<a name="2.0.3"></a>
## [2.0.3](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@2.0.2...conventional-changelog-core@2.0.3) (2018-02-13)




**Note:** Version bump only for package conventional-changelog-core

<a name="2.0.2"></a>
## [2.0.2](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@2.0.1...conventional-changelog-core@2.0.2) (2018-02-13)




**Note:** Version bump only for package conventional-changelog-core

<a name="2.0.1"></a>
## [2.0.1](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@2.0.0...conventional-changelog-core@2.0.1) (2018-02-05)




**Note:** Version bump only for package conventional-changelog-core

<a name="2.0.0"></a>
# [2.0.0](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@1.9.5...conventional-changelog-core@2.0.0) (2018-01-29)


### Bug Fixes

* **writer:** normalize release headings ([#237](https://github.com/conventional-changelog/conventional-changelog-core/issues/237)) ([9e87dc3](https://github.com/conventional-changelog/conventional-changelog-core/commit/9e87dc3)), closes [/github.com/conventional-changelog/conventional-changelog/issues/214#issuecomment-326681934](https://github.com//github.com/conventional-changelog/conventional-changelog/issues/214/issues/issuecomment-326681934)


### BREAKING CHANGES

* **writer:** Logic for generating release headings has been changed to make all
heading levels the same (`##`/`h2`) for better compatibility with
screen readers and parsers, and to conform to HTML semantics. Patch
release titles are now wrapped in a `<small>` tag to maintain the
visual hierarchy of the previous style.

Fixes https://github.com/conventional-changelog/conventional-changelog/issues/214




<a name="1.9.5"></a>
## [1.9.5](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@1.9.4...conventional-changelog-core@1.9.5) (2017-12-18)




**Note:** Version bump only for package conventional-changelog-core

<a name="1.9.4"></a>
## [1.9.4](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@1.9.3...conventional-changelog-core@1.9.4) (2017-12-08)




**Note:** Version bump only for package conventional-changelog-core

<a name="1.9.3"></a>
## [1.9.3](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@1.9.2...conventional-changelog-core@1.9.3) (2017-11-13)




**Note:** Version bump only for package conventional-changelog-core

<a name="1.9.2"></a>
## [1.9.2](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@1.9.1...conventional-changelog-core@1.9.2) (2017-10-01)

<a name="1.9.1"></a>
## [1.9.1](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@1.9.0...conventional-changelog-core@1.9.1) (2017-09-01)

<a name="1.9.0"></a>
# [1.9.0](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@1.8.0...conventional-changelog-core@1.9.0) (2017-07-17)


### Features

* **context:** default currentTag may not prefix with v ([#179](https://github.com/conventional-changelog/conventional-changelog/issues/179)) ([431598a](https://github.com/conventional-changelog/conventional-changelog-core/commit/431598a))

<a name="1.8.0"></a>
# [1.8.0](https://github.com/conventional-changelog/conventional-changelog-core/compare/conventional-changelog-core@1.7.0...conventional-changelog-core@1.8.0) (2017-03-11)


### Features

* context.currentTag should take into account lerna tag format ([#178](https://github.com/conventional-changelog/conventional-changelog/issues/178)) ([f0e5875](https://github.com/conventional-changelog/conventional-changelog-core/commit/f0e5875))

<a name="1.5.0"></a>
# [1.5.0](https://github.com/conventional-changelog/conventional-changelog-core/compare/v1.4.0...v1.5.0) (2016-05-10)


### Features

* **context:** fallback to repoUrl([da0b096](https://github.com/conventional-changelog/conventional-changelog-core/commit/da0b096)), closes [#7](https://github.com/conventional-changelog/conventional-changelog-core/issues/7)



<a name="1.4.0"></a>
# [1.4.0](https://github.com/conventional-changelog/conventional-changelog-core/compare/v1.3.4...v1.4.0) (2016-05-08)


### Features

* **debug:** make options.debug as default writeOpts.debug([eeb7e8f](https://github.com/conventional-changelog/conventional-changelog-core/commit/eeb7e8f))



<a name="1.3.4"></a>
## [1.3.4](https://github.com/conventional-changelog/conventional-changelog-core/compare/v1.3.3...v1.3.4) (2016-05-07)


### Bug Fixes

* **mergeConfig:** respect issuePrefixes option ([4be052b](https://github.com/conventional-changelog/conventional-changelog-core/commit/4be052b)), closes [#6](https://github.com/conventional-changelog/conventional-changelog-core/issues/6) [#8](https://github.com/conventional-changelog/conventional-changelog-core/issues/8)



<a name="1.3.3"></a>
## [1.3.3](https://github.com/conventional-changelog/conventional-changelog-core/compare/v1.3.2...v1.3.3) (2016-04-19)


### Bug Fixes

* **unknownHost:** default context.repository ([eaa3b6f](https://github.com/conventional-changelog/conventional-changelog-core/commit/eaa3b6f))



<a name="1.3.2"></a>
## [1.3.2](https://github.com/conventional-changelog/conventional-changelog-core/compare/v1.3.1...v1.3.2) (2016-04-17)




<a name="1.3.1"></a>
## [1.3.1](https://github.com/conventional-changelog/conventional-changelog-core/compare/v1.3.0...v1.3.1) (2016-04-09)


### Bug Fixes

* **defaults:** context tags ([2571038](https://github.com/conventional-changelog/conventional-changelog-core/commit/2571038))



<a name="1.3.0"></a>
# [1.3.0](https://github.com/stevemao/conventional-changelog-core/compare/v1.2.0...v1.3.0) (2016-02-13)


### Features

* **debug:** add options.debug function ([aa56ae6](https://github.com/stevemao/conventional-changelog-core/commit/aa56ae6))



<a name="1.2.0"></a>
# [1.2.0](https://github.com/stevemao/conventional-changelog-core/compare/v1.1.0...v1.2.0) (2016-02-11)


### Features

* **merge:** ignore merge commits ([8f788dc](https://github.com/stevemao/conventional-changelog-core/commit/8f788dc))



<a name="1.1.0"></a>
# [1.1.0](https://github.com/stevemao/conventional-changelog-core/compare/v1.0.2...v1.1.0) (2016-02-08)


### Bug Fixes

* **default:** firstCommit and lastCommit should based on original unfiltered commits ([7fc49c9](https://github.com/stevemao/conventional-changelog-core/commit/7fc49c9)), closes [#2](https://github.com/stevemao/conventional-changelog-core/issues/2)



<a name="1.0.2"></a>
## [1.0.2](https://github.com/stevemao/conventional-changelog-core/compare/v1.0.1...v1.0.2) (2016-02-06)


### Bug Fixes

* **currentTag:** if unreleased, currentTag should be last commit hash ([e3d25ae](https://github.com/stevemao/conventional-changelog-core/commit/e3d25ae))



<a name="1.0.1"></a>
## [1.0.1](https://github.com/stevemao/conventional-changelog-core/compare/v1.0.0...v1.0.1) (2016-02-06)


### Bug Fixes

* **unreleased:** now it can output unreleased commits ([87b7340](https://github.com/stevemao/conventional-changelog-core/commit/87b7340))



<a name="1.0.0"></a>
# [1.0.0](https://github.com/stevemao/conventional-changelog-core/compare/v0.0.2...v1.0.0) (2016-02-05)


### Bug Fixes

* **oldNode:** git remote origin url feature is only available under node>=4 ([c69db53](https://github.com/stevemao/conventional-changelog-core/commit/c69db53))

### Features

* **pkg:** fallback to git remote origin url ([5b56952](https://github.com/stevemao/conventional-changelog-core/commit/5b56952))
* **unreleased:** option to output or not unreleased changelog ([9dfe8d8](https://github.com/stevemao/conventional-changelog-core/commit/9dfe8d8)), closes [ajoslin/conventional-changelog#120](https://github.com/ajoslin/conventional-changelog/issues/120)


### BREAKING CHANGES

* unreleased: If `context.version` is the same as the version of the last release, by default the unreleased chagnelog will not output.



<a name="0.0.2"></a>
## [0.0.2](https://github.com/stevemao/conventional-changelog-core/compare/v0.0.1...v0.0.2) (2016-01-30)


### Bug Fixes

* **error:** better error handling ([614ce1a](https://github.com/stevemao/conventional-changelog-core/commit/614ce1a)), closes [ajoslin/conventional-changelog#130](https://github.com/ajoslin/conventional-changelog/issues/130)



<a name="0.0.1"></a>
## 0.0.1 (2015-12-26)


### Features

* **config:** change preset to config ([85fd9d9](https://github.com/stevemao/conventional-changelog-core/commit/85fd9d9))
* **init:** extract core from conventional-changelog ([4a4bca3](https://github.com/stevemao/conventional-changelog-core/commit/4a4bca3))


### BREAKING CHANGES

* config: `options.preset` is removed in favour of `options.config`
