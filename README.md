# contents

How to write filters
--------------------
[Howto? block whitlisted spyware](https://github.com/easylist/easylist/issues/4529)

@DandelionSprout have written this: [blocking guide](https://github.com/DandelionSprout/adfilt/blob/master/Wiki/SyntaxMeaningsThatAreActuallyHumanReadable.md#blocking) but a few axamples would be greate


* `$badfilter`: Deactivates a resource-blocking entry, even if it is
	present in another list.   
	As example `@@||hcaptcha.com^*/api.js$script,domain=abcvideo.cc,badfilter`
	here the `,badfilter` tells uBo __**NOT**__ to obey the whitelisting
	rule

* `$important`: Makes a resource-blocking entry take precedence over
	another whitelisting entry. __The rule has precedence__ or __Highest weight__   
	As example `||hcaptcha.com^$important`, here the `$important` is
	blocking everything from the domain `hcaptcha.com` and therefor also
	covering the example in `$badfilter` and therefor making the `$badfilter`
	a unnecessary rule.

* `$redirect`: Redirects resources to a neutered version that has been
	embedded in those extensions.   
    Possible options are listed in 
    [this file](https://github.com/gorhill/uBlock/blob/master/src/js/redirect-engine.js)
    (AdGuard has a [slightly smaller selection](https://github.com/AdguardTeam/AdguardBrowserExtension/blob/master/Extension/lib/filter/rules/scriptlets/redirects.yml)).

* `$empty`: Results in a fake empty page being loaded, instead of an error page.

* `^` Is a wildcard for any __NON__ alphanumerical or `_ - . %` and for
	`end-of-string`   
	This is meant quite literally. `||example.org/a^` would block e.g.
	`example.org/a` and `example/a?trackingnumber=666`, but would not
	block `example.org/abc` or `example.org/a-b-c`.    
	Comparatively, `||example.org/a` without `^` would block all four.
* `$` 

* `,` The comma `,` can be used for a lot of stuff, especially in hiding
	rules. But there's typically only one reasonably valid use in blocking
	rules (except in the very rare cases it's used in URLs), which is to
	combine multiple `$` criteria.   
	For example, `||example.com^$image,media,third-party,important`.

## Url to source
https://help.eyeo.com/en/adblockplus/how-to-write-filters

[Click here to activate in adBlockPlus](https://subscribe.adblockplus.org/?location=https://anonymousposter.gitlab.io/ublockorigin-rules/blockrules.txt&title=My%20Privacy%20DNS)

## Webfront
This project's HTML front end is <https://anonymousposter.gitlab.io/ublockorigin-rules/>
