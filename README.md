<h2 align='center'><samp>stimulus-vite-helpers-2</samp></h2>

<p align='center'>Helpers to easily load your Stimulus controllers when using Vite.js</p>

<p align='center'>
  <a href='https://www.npmjs.com/package/stimulus-vite-helpers-2'>
    <img src='https://img.shields.io/npm/v/stimulus-vite-helpers-2?color=222&style=flat-square'>
  </a>
  <a href='https://github.com/ElMassimo/vite_ruby/blob/master/LICENSE.txt'>
    <img src='https://img.shields.io/badge/license-MIT-blue.svg'>
  </a>
</p>

<br>

[globEager]: https://vitejs.dev/guide/features.html#glob-import
[stimulusvitehelpers]: https://github.com/ElMassimo/stimulus-vite-helpers
[stimulus handbook]: https://stimulus.hotwire.dev/handbook/installing
[stimulus]: https://github.com/hotwired/stimulus
[vite_rails]: https://vite-rails.netlify.app
[vite-plugin-stimulus-hmr]: https://github.com/ElMassimo/vite-plugin-stimulus-hmr

This package is a fork of [stimulus-vite-helpers][stimulusvitehelpers], and will exist untill author accept my PR https://github.com/ElMassimo/stimulus-vite-helpers/pull/11 🤠

If you are looking for a simple way to integrate Vite.js in Rails, check out <kbd>[vite_rails]</kbd>.

If you would like to enable HMR for your Stimulus controllers, check out <kbd>[vite-plugin-stimulus-hmr]</kbd>.

## Installation 💿

```bash
npx ni stimulus-vite-helpers-2
```

## Usage 🚀

You can now register your Stimulus controllers using Vite's [globEager] and the `loadControllers` helper:

```ts
import { Application } from 'stimulus'
import { loadControllers } from 'stimulus-vite-helpers-2'

const application = Application.start()
const controllers = import.meta.globEager('./**/*_controller.js')
loadControllers(application, controllers)
```

If you are using controllers within `view_component` sidecar directories, the identifiers for these controllers might become lengthy and unclear
```js
// app/components/ui/button_component/button_component_controller.js

//├ components
//│ └ ui/
//│   └ button_component/
//│     └ button_component_controller.js

//=> ui--button-component--button-component
```

Enabling the `{ nestedMode: true }` flag removes the duplicated part of the controller identifier
```js
loadControllers(application, controllers, { nestedMode: true });
// default
//=> ui--button-component--button-component

// reduced
//=> ui--button-component
```

For more information, check the [Stimulus handbook].

## Special Thanks

- [Stimulus]

## License

This library is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
