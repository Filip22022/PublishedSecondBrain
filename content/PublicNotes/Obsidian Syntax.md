---
title: Obsidian Syntax
Tags: Public
Aliases:
Date created: 2024-02-10 14:55
---

### Internal Link
[[link]]
`[[link]]`

### Link to a Heading
[[Obsidian Syntax#Internal Link]]
`file#heading`
`[[##]]` can be used to search for heading in vault

### Link to a Block
[[Pillars of Object Oriented Programming#^06f6e9]]
`[note#^block]` the block identifier will be generated automatically

### External Link
[text]'(link)
`[text](link)`

### Blank Space in Links
Using `%20` in place of blank space or wrapping URL with `< >`

### Checkbox
- [ ] 
`- [ ]` 

### Quotes
> A simple Quote \- Me 

 `> x \-a`

### Callout Blocks
>[!info] Custom Title
>A callout block

```
>[!tag] Custom Title (optional)
>A Callout Block Body (optional)
```

>[!info]- Foldable Callout
>Sth

```
>[!info]- Foldable Callout (with + default unfolded)
>A callout block
```

> [!question] Can callouts be nested?
> > [!todo] Yes!, they can.
> > > [!example]  You can even use multiple layers of nesting.
> > 
```
> [!question] Can callouts be nested?
> > [!todo] Yes!, they can.
> > > [!example]  You can even use multiple layers of nesting.
```

[custom callouts](https://help.obsidian.md/Editing+and+formatting/Callouts)
#### Callout Types
>[!Abstract] Abstract/summary/tldr

>[!info] Info

>[!Todo] Todo

>[!Tip] Tip/hint/important

>[!Success] Success/check/done

>[!Question] Question/help/faq

>[!Warning] Warning/caution/attention

>[!Failure] failure/fail/missing

>[!Danger] Danger/error

>[!bug] Bug

>[!Example] example

>[!Quote] Quote
### Separator
---
```
---
----
****
***
- - -
```


### Text
**Bold**
`**x** / __x__`

*Italic*
`*x* / _x_`

~~Strikethrough~~
`~~x~~`

==highlight==
`==x==`

**Bold, nested _italic_**
`**x _x_*`

***Bold Italic***
`***x*** / ___x___`

### Code
`x`
```
x
x
```

```
One line
`x`


Multiline
\```
x
x
\```
```
### Images
`![title](imaeURL)`
`![title|heigthxwidth](imaeURL)`

