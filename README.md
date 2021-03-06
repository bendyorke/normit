#Normit [![Build Status](https://travis-ci.org/pawurb/normit.png)](https://travis-ci.org/pawurb/normit) [![NPM version](https://badge.fury.io/js/normit.svg)](http://badge.fury.io/js/normit) [![Coverage Status](https://coveralls.io/repos/pawurb/normit/badge.png?branch=master)](https://coveralls.io/r/pawurb/normit?branch=master)


Normit is an easy way to use Google Translate in your terminal.
## Installation
```bash
npm install normit -g
```

## Usage
```bash
normit 'source_language' 'target_language' 'text'
```

Example:

```bash

normit en es "hey cowboy where is your horse?"
=> "Hey vaquero dónde está tu caballo?"

normit fr en "qui est votre papa?"
=> "Who's Your Daddy?"
```

Parenthesis are not necessary for text data input:
```bash
normit fr ru qui est votre papa?
=> "Кто твой папочка?"
```
#### Speech synthesis

Specify a **-t** (talk) flag to use speech synthesis (requires mpg123):
``` bash
normit en zh "hey cowboy where is your horse?" -t
=> "嘿，牛仔是你的马在哪里？" # and a chinese voice says something about a horse
```

You can use normit as a speech synthesizer of any supported language without having to translate anything:
``` bash
normit en en "hold your horses cowboy !" -t
=> "hold your horses cowboy !" # and an english voice asks you to hold on
```

#### Synonyms

Specify a **-s** (synonyms) flag to get the list of synonyms if available:
``` bash
normit es en muchacho -s
=> boy
=> Synonyms: boy, lad, youngster, laddie, cully
```

#### Learning language when committing to git (zsh only)
Idea by [Nedomas](https://news.ycombinator.com/item?id=7545747) . See and hear your messages translated to target lang every time you commit:

In **~/.zshrc**
```bash
export LANG=es
git(){[[ "$@" = commit\ -m* ]]&&normit en $LANG ${${@:$#}//./} -t;command git $@}
```


## Language codes:
* english - en
* polish - pl
* french - fr
* spanish - es
* chinese - zh
* russian - ru
* automatic source language detection - auto

To find all available language codes visit https://developers.google.com/translate/v2/using_rest#language-params.

## Requirements

Works with node 0.10.0 and higher.

To use speech synthesis you need to have mpg123 installed.

For Ubuntu:

    sudo apt-get install mpg123

For MacOSX:

    brew install mpg123




