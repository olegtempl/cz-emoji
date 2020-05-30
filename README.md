# cz-emoji

> Commitizen adapter formatting commit messages using emojis.

**cz-emoji** allows you to easily use emojis in your commits using [commitizen].

```sh
? Select the type of change you are committing: (Use arrow keys)
❯ feature   🌟  A new feature
  fix       🐞  A bug fix
  docs      📚  Documentation change
  refactor  🎨  A code refactoring change
  chore     🔩  A chore change
```

## Install

**Globally**

```bash
npm install --global cz-emoji

# set as default adapter for your projects
echo '{ "path": "cz-emoji" }' > ~/.czrc
```

**Locally**

```bash
npm install --save-dev cz-emoji
```

Add this to your `package.json`:

```json
"config": {
  "commitizen": {
    "path": "cz-emoji"
  }
}
```

## Usage

```sh
$ git cz
```

## Customization

By default `cz-emoji` comes ready to run out of the box. Uses may vary, so there are a few configuration options to allow fine tuning for project needs.

### How to

Configuring `cz-emoji` can be handled in the users home directory (`~/.czrc`) for changes to impact all projects or on a per project basis (`package.json`). Simply add the config property as shown below to the existing object in either of the locations with your settings for override.

```json
{
  "config": {
    "cz-emoji": {}
  }
}
```

### Configuration Options

#### Types

By default `cz-emoji` comes preconfigured with the [Gitmoji](https://gitmoji.carloscuesta.me/) types.

An [Inquirer.js] choices array:

```json
{
  "config": {
    "cz-emoji": {
      "types": [
        {
          "emoji": "🌟",
          "code": ":star2:",
          "description": "A new feature",
          "name": "feature"
        }
      ]
    }
  }
}
```

#### Scopes

An [Inquirer.js] choices array:

```json
{
  "config": {
    "cz-emoji": {
      "scopes": ["home", "accounts", "ci"]
    }
  }
}
```

#### Symbol

A boolean value that allows for an using a unicode value rather than the default of [Gitmoji](https://gitmoji.carloscuesta.me/) markup in a commit message. The default for symbol is false.

```json
{
  "config": {
    "cz-emoji": {
      "symbol": true
    }
  }
}
```

#### Skip Questions

An array of questions you want to skip:

```json
{
  "config": {
    "cz-emoji": {
      "skipQuestions": ["scope", "issues"]
    }
  }
}
```

You can skip the following questions: `scope`, `body`, and `issues`. The `type` and `subject` questions are mandatory.


#### Customize Questions

An object that contains overrides of the original questions:

```json
{
  "config": {
    "cz-emoji": {
      "questions": {
        "body": "This will be displayed instead of original text"
      }
    }
  }
}
```

## Examples

- https://github.com/Falieson/TRAM

## Commitlint

Commitlint can be set to work with this package by leveraging the package https://github.com/arvinxx/commitlint-config-gitmoji.

```bash
npm install --save-dev commitlint-config-gitmoji
```

_commitlint.config.js_

```js
module.exports = {
  extends: ['gitmoji'],
  parserPreset: {
    parserOpts: {
      headerPattern: /^(:\w*:)(?:\s)(?:\((.*?)\))?\s((?:.*(?=\())|.*)(?:\(#(\d*)\))?/,
      headerCorrespondence: ['type', 'scope', 'subject', 'ticket']
    }
  }
}
```

<table class="" style="margin-left: 50px;"><tr class=""><th style="margin-left: 100px;" class="">name</th>
    <th style="margin-right: 5px;" class="">emoji</th>
    <th style="margin-right: 10px;" class="">description</th></tr> <tr class=""><td class="" style="margin-left: 100px;">style</td> <td class="" style="margin-right: 5px;">🎨</td> <td class="" style="margin-right: 10px;">Improving structure / format of the code.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">perf</td> <td class="" style="margin-right: 5px;">⚡️</td> <td class="" style="margin-right: 10px;">Improving performance.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">prune</td> <td class="" style="margin-right: 5px;">🔥</td> <td class="" style="margin-right: 10px;">Removing code or files.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">fix</td> <td class="" style="margin-right: 5px;">🐛</td> <td class="" style="margin-right: 10px;">Fixing a bug.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">quickfix</td> <td class="" style="margin-right: 5px;">🚑</td> <td class="" style="margin-right: 10px;">Critical hotfix.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">feature</td> <td class="" style="margin-right: 5px;">✨</td> <td class="" style="margin-right: 10px;">Introducing new features.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">db</td> <td class="" style="margin-right: 5px;">🗃</td> <td class="" style="margin-right: 10px;"> Performing database related changes.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">ui</td> <td class="" style="margin-right: 5px;">💄</td> <td class="" style="margin-right: 10px;">Updating the UI and style files.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">wip</td> <td class="" style="margin-right: 5px;">🚧</td> <td class="" style="margin-right: 10px;">Work in progress.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">breaking</td> <td class="" style="margin-right: 5px;">💥</td> <td class="" style="margin-right: 10px;">Introducing breaking changes.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">review</td> <td class="" style="margin-right: 5px;">👌</td> <td class="" style="margin-right: 10px;">Updating code due to code review changes.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">docs-code</td> <td class="" style="margin-right: 5px;">💡</td> <td class="" style="margin-right: 10px;">Documenting source code.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">analytics</td> <td class="" style="margin-right: 5px;">📈</td> <td class="" style="margin-right: 10px;">Adding analytics or tracking code.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">refactoring</td> <td class="" style="margin-right: 5px;">♻️</td> <td class="" style="margin-right: 10px;"> Refactoring code.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">dep-add</td> <td class="" style="margin-right: 5px;">➕</td> <td class="" style="margin-right: 10px;">Adding a dependency.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">dep-rm</td> <td class="" style="margin-right: 5px;">➖</td> <td class="" style="margin-right: 10px;">Removing a dependency.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">config</td> <td class="" style="margin-right: 5px;">🔧</td> <td class="" style="margin-right: 10px;">Changing configuration files.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">i18n</td> <td class="" style="margin-right: 5px;">🌐</td> <td class="" style="margin-right: 10px;">Internationalization and localization.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">poo</td> <td class="" style="margin-right: 5px;">💩</td> <td class="" style="margin-right: 10px;">Writing bad code that needs to be improved.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">merge</td> <td class="" style="margin-right: 5px;">🔀</td> <td class="" style="margin-right: 10px;">Merging branches.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">dep-up</td> <td class="" style="margin-right: 5px;">📦</td> <td class="" style="margin-right: 10px;">Updating compiled files or packages.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">compat</td> <td class="" style="margin-right: 5px;">👽</td> <td class="" style="margin-right: 10px;">Updating code due to external API changes.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">mv</td> <td class="" style="margin-right: 5px;">🚚</td> <td class="" style="margin-right: 10px;">Moving or renaming files.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">arch</td> <td class="" style="margin-right: 5px;">🏗</td> <td class="" style="margin-right: 10px;"> Making architectural changes.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">iphone</td> <td class="" style="margin-right: 5px;">📱</td> <td class="" style="margin-right: 10px;">Working on responsive design.</td></tr> <br class=""><tr class=""><td class="" style="margin-left: 100px;">seo</td> <td class="" style="margin-right: 5px;">🔍</td> <td class="" style="margin-right: 10px;">Improving SEO</td></tr> <br class=""></table>

## License

MIT © [Nicolas Gryman](http://ngryman.sh)

[commitizen]: https://github.com/commitizen/cz-cli
[inquirer.js]: https://github.com/SBoudrias/Inquirer.js/


 /*


   {
      emoji: "🔊",
      code: ":loud_sound:",
      description: "Adding logs.",
      name: "log-add"
    },
    {
      emoji: "🔇",
      code: ":mute:",
      description: "Removing logs.",
      name: "log-rm"
    },
        {
      emoji: "📝",
      code: ":pencil:",
      description: "Writing docs.",
      name: "docs"
    },
    {
      emoji: "💬",
      code: ":speech_balloon:",
      description: "Updating text and literals.",
      name: "texts"
    },
            emoji: "📸",
          code: ":camera_flash:",
          description: "Adding or updating snapshots",
          name: "camera-flash"
        },

  // chrome, firefox, safari, mobile ios, mobile anroid.
{
      emoji: "🍎",
      code: ":apple:",
      description: "Fixing something on macOS.",
      name: "osx"
    },
    {
      emoji: "🐧",
      code: ":penguin:",
      description: "Fixing something on Linux.",
      name: "linux"
    },
    {
      emoji: "🏁",
      code: ":checkered_flag:",
      description: "Fixing something on Windows.",
      name: "windows"
    },
    {
      emoji: "🤖",
      code: ":robot:",
      description: "Fixing something on Android.",
      name: "android"
    },
    {
      emoji: "🍏",
      code: ":green_apple:",
      description: "Fixing something on iOS.",
      name: "ios"
    },
    {
      emoji: "🚨",
      code: ":rotating_light:",
      description: "Removing linter warnings.",
      name: "lint"
    },
        {
      emoji: "💚",
      code: ":green_heart:",
      description: "Fixing CI Build.",
      name: "fix-ci"
    },

  // issue
    {
      emoji: "🔒",
      code: ":lock:",
      description: "Fixing security issues.",
      name: "security"
    },


      {
      emoji: "🤡",
      code: ":clown_face:",
      description: "Mocking things.",
      name: "clown-face"
    },
    {
      emoji: "🥚",
      code: ":egg:",
      description: "Adding an easter egg.",
      name: "egg"
    },

      {
      emoji: "🚀",
      code: ":rocket:",
      description: "Deploying stuff.",
      name: "deploy"
    },
    {
      emoji: "✏️",
      code: ":pencil2:",
      description: " Fixing typos.",
      name: "typo"
    },
        {
      emoji: "🐳",
      code: ":whale:",
      description: "Work about Docker.",
      name: "docker"
    },

    {
      emoji: "♿️",
      code: ":wheelchair:",
      description: "Improving accessibility.",
      name: "access"
    },
        {
      emoji: "🍻",
      code: ":beers:",
      description: "Writing code drunkenly.",
      name: "beer"
    },
    {

    {
      emoji: "🙈",
      code: ":see_no_evil:",
      description: "Adding or updating a .gitignore file",
      name: "see-no-evil"
    },
    {
      emoji: "⚗",
      code: ":alembic:",
      description: " Experimenting new things",
      name: "experiment"
    },
       {
      emoji: "☸️",
      code: ":wheel_of_dharma:",
      description: " Work about Kubernetes",
      name: "k8s"
    },
    {
      emoji: "🏷️",
      code: ":label:",
      description: " Adding or updating types (Flow, TypeScript)",
      name: "types"
    },
    {
      emoji: "🌱",
      code: ":seedling:",
      description: "Adding or updating seed files",
      name: "seed"
    },
    {
      emoji: "🚩",
      code: ":triangular_flag_on_post:",
      description: "Adding, updating, or removing feature flags",
      name: "flags"
    },
    {
      emoji: "💫",
      code: ":dizzy:",
      description: "Adding or updating animations and transitions",
      name: "animation"
    }


    {
      emoji: "👥",
      code: ":busts_in_silhouette:",
      description: "Adding contributor(s).",
      name: "contrib-add"
    },
    {
      emoji: "🚸",
      code: ":children_crossing:",
      description: "Improving user experience / usability.",
      name: "ux"
    },



    // REMAINS repository
    {
      emoji: "⏪",
      code: ":rewind:",
      description: "Reverting changes.",
      name: "revert"
    },
     {
      emoji: "🔖",
      code: ":bookmark:",
      description: "Releasing / Version tags.",
      name: "release"
    },

    // сомнительные управление зависимостями
     {
      emoji: "⬇️",
      code: ":arrow_down:",
      description: " Downgrading dependencies.",
      name: "downgrade"
    },
    {
      emoji: "⬆️",
      code: ":arrow_up:",
      description: " Upgrading dependencies.",
      name: "upgrade"
    },
    {
      emoji: "📌",
      code: ":pushpin:",
      description: "Pinning dependencies to specific versions.",
      name: "pushpin"
    },


      // сомнительное для иннициализации репозитория
    {
      emoji: "👷",
      code: ":construction_worker:",
      description: "Adding CI build system.",
      name: "ci"
    },
        {
      emoji: "🎉",
      code: ":tada:",
      description: "Initial commit.",
      name: "init"
    },
    {
      emoji: "✅",
      code: ":white_check_mark:",
      description: "Adding tests.",
      name: "test"
    },
    {
      emoji: "📄",
      code: ":page_facing_up:",
      description: "Adding or updating license.",
      name: "license"
    },
        {
      emoji: "🍱",
      code: ":bento:",
      description: "Adding or updating assets.",
      name: "assets"
    },



   */