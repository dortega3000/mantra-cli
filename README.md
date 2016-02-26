# Mantra CLI

[![Build Status](https://travis-ci.org/sungwoncho/mantra-cli.svg?branch=master)](https://travis-ci.org/sungwoncho/mantra-cli)

A command line interface for developing Meteor apps using [Mantra](https://github.com/kadirahq/mantra).


## Installation

    npm install -g mantra-cli


## Commands

The available commands are:

* create
* generate

Currently, CLI expects you to be in the app root directory.


### mantra create [path]
*Note: You can also use the alias "c":* `mantra c [path]`

Create a Meteor application using Mantra spec under `path`.

### mantra generate [type] [name]
*Note: You can also use the alias "g":* `mantra g [type] [name]`

Generate a file of `type` and name specified `name`.

**type**

Possible values are:

* action
* component
* container
* collection
* method
* module
* publication

For `container`, the command generates `container`, and then also generates the
corresponding `component`.

**name**

If the `type` is one of `action`, `component`, or `container`, the name should
follow the format `moduleName:entityName`. This is because Mantra is modular
on the client side, and all files of those types should belong to a module.

*Example*

    mantra generate component core:posts
    mantra generate publication users
    mantra generate method comments

#### Automatic update to index.js

For `action`, `collection`, `method`, and `publication`, the command
automatically updates a `index.js` file to automatically include the newly
generated file.

*Example*

    $ mantra generate action core:users
      create  ./client/modules/core/actions/users.js
      update  ./client/modules/core/actions/index.js

*./client/modules/core/actions/users.js*
```js
export default {

}
```

*./client/modules/core/actions/index.js*
```js
import users from './users';

export default {
  users
};
```

## License

MIT
