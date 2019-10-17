# Sublime Hugo IF

    Status: Alpha 1 | 2019/10/17

[Hugo Interactive Fiction] syntax support for [Sublime Text 3].

Created by [Tristano Ajmone], 2019/10/17. MIT License.

Project Status: WIP Alpha.

-----

**Table of Contents**

<!-- MarkdownTOC autolink="true" bracket="round" autoanchor="false" lowercase="only_ascii" uri_encoding="true" levels="1,2,3" -->

- [About](#about)
    - [Associated File Extensions](#associated-file-extensions)
    - [Encoding](#encoding)
    - [Syntax Status](#syntax-status)
- [Installation](#installation)
    - [Troubleshooting](#troubleshooting)

<!-- /MarkdownTOC -->

-----

# About

I've created this Hugo syntax definition for my personal use, so it's currently unavailable as an installable package via [PackageControl].
In the future — _if_ and _when_ this project reaches maturity status — I might publish it on PackageControl.

## Associated File Extensions

The following file extensions will be automatically associated with the Hugo IF syntax:

- `.hug`
- `.g`

Unfortunately, the `.h` extensions is also commonly associated with Hugo library files, but because `.h` is commonly used for C/C++ header files I didn't associate it to Hugo, to prevent conflicts.

This means that you'll have to manually set the Hugo IF syntax for `.h` files after opening them.
Don't forget to also manually set their encoding to ISO-8859-1, after setting their syntax to Hugo IF.

## Encoding

The Hugo syntax will automatically enforce [ISO-8859-1] (Latin1) encoding on `*.hug` and `*.g` files — as for `*.h` files, see my previous notes.

Since the Hugo compiler doesn't handle Unicode files, it's important to strictly preserve the ISO encoding in the source files, lest they get corrupted by special non-Ascii characters which are represented as multiple-bytes in UTF-8.
This is especially true for cut-and-paste operations from other (UTF-8) documents, which could corrupt the Hugo source file encoding by switching to UTF-8.

Hugo source files should be Ascii only, for the language provides special escape sequences to represent non-Ascii characters.
Therefore, the [ISO-8859-1] encoding should be fine for most projects.

In any case, you can override the default encoding in your User setting.
For example, to adopt [ISO-8859-3]  (Latin3) for Esperanto, Maltese or Turkish, add to your `<data_path>/Packages/User/Hugo-IF.sublime-settings` the following:

```json
{
    "default_encoding":  "Western (ISO 8859-3)",
    "fallback_encoding": "Western (ISO 8859-3)",
}
```

The important thing is to stick to an 8-bit single-byte encoding.

## Syntax Status

Right now, the Hugo syntax is still very rudimentary.
It detects all Hugo keywords under the generic scope `keyword.other.hugo-if`.

Eventually, as the syntax evolves, every keyword shall be scoped with the correct category, and the syntax semantics will be improved.

Once the semantic stage is achieved, it will be possible to start handling symbols indexing, auto-completions, and add useful snippets and advanced features and functionality.

# Installation

Currently, the only way to install it on your local machine is by manually cloning this repository via Git as a _loose package_ into [ST packages folder]:

- Create a `Hugo-IF` folder inside ST `<data_path>/Packages/` folder.
- Open a shell and CD to `<data_path>/Packages/Hugo-IF/`.
- Clone the repository using:

        git clone https://github.com/tajmone/sublime-hugo-if.git .

    **NOTE:** The final ` .` is required to clone the repository directly inside the current folder without creating a new sub-folder.

For the moment, you'll have to manually update the package via `git pull`, until I find a better solution (e.g. create a PackageControl setting file to handle updates and allow manual installation outside [PackageControl]).

If you're interested in actually using this package, please [contact me] or [open an issue], so that I might give priority to third party usability of this project.

## Troubleshooting

If after the above steps the Package Control plug-in starts to complain and raise error messages, go to

- Preferences » Package Settings » Package Control » Settings — User

and add the following line to your custom setting:

```json
{
    "ignore_vcs_packages": true,
}
```

For more details, [see PackageControl Documentation on Git repositories settings].


<!-----------------------------------------------------------------------------
                               REFERENCE LINKS
------------------------------------------------------------------------------>

[contact me]: mailto:tajmone@gmail.com "Contact Tristano Ajmone via email"
[open an issue]: https://github.com/tajmone/sublime-hugo-if/issues/new "Open a new Issue on Sublime Hugo-IF"
[see PackageControl Documentation on Git repositories settings]: https://packagecontrol.io/docs/settings#setting-ignore_vcs_packages

<!-- Hugo -->

[Hugo website]: http://www.generalcoffee.com/hugo/gethugo.html "Visit the Hugo website"
[Hugo Interactive Fiction]: http://www.generalcoffee.com/hugo/gethugo.html "Visit the Hugo website"

[Awesome IF website » Hugo]: https://tajmone.github.io/awesome-interactive-fiction/#hugo "View Hugo entry at the Awesome Interactive Fiction website"
[Awesome IF » Hugo]: https://github.com/tajmone/awesome-interactive-fiction#hugo "View Hugo entry at the Awesome Interactive Fiction repository"
[Hugo Wiki]: https://github.com/tajmone/hugo/wiki "Visit the Hugo Wiki of this repository"
[IF Archive » Hugo]: https://www.ifarchive.org/indexes/if-archive/programming/hugo/ "Visit the IF Archive section on Hugo"
[IFWiki » Hugo]: http://ifwiki.org/index.php/Hugo "Go to the Hugo page on IFWiki"
[The Hugo Book]: http://www.ifarchive.org/if-archive/programming/hugo/manuals/hugo_book.pdf "Download 'The Hugo Book' (PDF) for Hugo v3.1"

<!-- Sublime Text -->

[Sublime Text 3]: https://www.sublimetext.com/ "Visit Sublime Text website"
[PackageControl]: https://packagecontrol.io/ "Visit PackageControl.io"

[ST packages folder]: https://www.sublimetext.com/docs/3/packages.html "Read Sublime Text 3 documentation on 'Packages Locations'"

<!-- Wikipedia -->

[ISO-8859-1]: https://en.wikipedia.org/wiki/ISO/IEC_8859-1 "See Wikipedia on ISO-8859-1 (Latin1)"
[ISO-8859-3]: https://en.wikipedia.org/wiki/ISO/IEC_8859-3 "See Wikipedia on ISO-8859-3"

<!-- people -->

[Tristano Ajmone]: https://github.com/tajmone "View Tristano Ajmone's GitHub profile"
[Kent Tessman]: https://github.com/tessman "View Kent Tessman's GitHub profile"

<!-- project files -->

[LICENSE]: ./LICENSE "View full text of the MIT License"
[.ec]: ./.editorconfig "View the EditorConfig settings file"

<!-- EOF -->
