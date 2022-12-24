# Blotter Minimal User Guide

Fonts (fonts.ltm and fonts.lts)
==================================

The fontloader uses gates, but only superficially. They won't be
documented here.

```\setfont <command>:<attributes>```

Sets <command> to call the font described in <attributes>; all defaults
to the values of the !metafont parameter. If <command> is \mainfont, the
font is called at once. Also, \codefont is used in some places (e.g.
verbatim).

> name

The family name of the font; e.g. Chaparral Pro for the main text of
this document.

> size (dimension)

The size of the font.

> small (dimension)

The size of the font when \small is called. Can be a relative value by
prefixing it with "-" or "+", in which case it is set relative to ?size.

> verysmall (dimension)

The size (possibly relative) for \verysmall.

> big (dimension)

The size (possibly relative) for \big.

> verybig (dimension)

The size (possibly relative) for \verybig.

> bold (font modifier)

The modifier used for the bold version of the font, without the leading slash;
!metafont sets it to "Bold".

> italic (font modifier)

Same as !bold for the italic version; set to "Italic" by !metafont.

> math (true or false)

If true, math fonts will be created.

> features

Well, err, font features...

> slant (angle)

The slant applied to the font to create a fake italic.

> slantsc (angle)

The slant applied to the font to create fake italic smallcaps; if not
given, defaults to ?slant.

There's actually much more going under the hood, but "font.ptxlua" (the
font loader itself) is a work in progress, and undocumented.

The same macros as in plain TeX can be used, except they're cumulative,
i.e. "\it\bf" switches to a bold italic.

\it

Switches to italics.

\rm

Switches to roman.

\bf

Switches to bold.

\rg

Switches to regular weight.

\sc

Switches to small capitals.

\lc

Switches to lower case (i.e. not small caps).

\ital <text>

Typesets <text> in italics.

\bold <text>

Typesets <text> in bold.

\scap <text>

Typesets <text> in small caps.

\rom <text>

Typesets <text> in roman.

\emph <text>

Typesets <text> in italics or roman, depending on whether the current
font is roman or italics, respectively.

\underline <text>

Underlines <text>. Wow.

\small

Switches to small font.

\verysmall

Switches to very small font.

\big

Switches to big font.

\verybig

Got it?

\normalsize

Switches to default size.

\smaller

Switches to the font smaller than the current one (e.g. \normalsize if
you're currently using \big).

\bigger

Same as \smaller, the other way around.

\color <color><text>

Typesets <text> with <color>, which should be a triplet "R G B" with
each value between 0 and 1.

# See also

Documentation for [YaX](https://ctan.org/pkg/yax) to get the set up syntax.
