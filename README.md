# REACT-DATEPICKER-COMPONENT



## Installation

The package can be installed via [npm](https://github.com/npm/cli):

```
npm install react-datepicker --save
```

Or via [yarn](https://github.com/yarnpkg/yarn):

```
yarn add react-datepicker
```

You’ll need to install React and PropTypes separately since those dependencies aren’t included in the package. If you need to use a locale other than the default en-US, you'll also need to import that into your project from date-fns (see Localization section below). Below is a simple example of how to use the Datepicker in a React view. You will also need to require the CSS file from this package (or provide your own). The example below shows how to include the CSS from this package if your build system supports requiring CSS files (Webpack is one that does).

```js
import React, { useState } from "react";
import DatePicker from "react-datepicker";

import "react-datepicker/dist/react-datepicker.css";

// CSS Modules, react-datepicker-cssmodules.css
// import 'react-datepicker/dist/react-datepicker-cssmodules.css';

const Example = () => {
  const [startDate, setStartDate] = useState(new Date());
  return (
    <DatePicker selected={startDate} onChange={(date) => setStartDate(date)} />
  );
};
```

## Configuration

The most basic use of the DatePicker can be described with:

```js
<DatePicker selected={startdate} onChange={(date) => setStartDate(date)} />
```

You can use `onSelect` event handler which fires each time some calendar date has been selected

```js
<DatePicker
  selected={date}
  onSelect={handleDateSelect} //when day is clicked
  onChange={handleDateChange} //only when value has changed
/>
```

`onClickOutside` handler may be useful to close datepicker in `inline` mode


### Time picker

You can also include a time picker by adding the showTimeSelect prop

```js
<DatePicker
  selected={date}
  onChange={handleDateChange}
  showTimeSelect
  dateFormat="Pp"
/>
```

Times will be displayed at 30-minute intervals by default (default configurable via timeIntervals prop)


### Localization

The date picker relies on [date-fns internationalization](https://date-fns.org/v3.3.1/docs/I18n) to localize its display components. By default, the date picker will use the locale globally set, which is English. Provided are 3 helper methods to set the locale:

- **registerLocale** (string, object): loads an imported locale object from date-fns
- **setDefaultLocale** (string): sets a registered locale as the default for all datepicker instances
- **getDefaultLocale**: returns a string showing the currently set default locale

```js
import { registerLocale, setDefaultLocale } from  "react-datepicker";
import { es } from 'date-fns/locale/es';
registerLocale('es', es)

<DatePicker
  locale="es"
/>
```

Locales can be changed in the following way:

- **Globally** - `setDefaultLocale('es');`

## Compatibility

### React

We're always trying to stay compatible with the latest version of React. We can't support all older versions of React.

Latest compatible versions:

- React 16 or newer: React-datepicker v2.9.4 and newer
- React 15.5: React-datepicker v2.9.3
- React 15.4.1: needs React-datepicker v0.40.0, newer won't work (due to react-onclickoutside dependencies)
- React 0.14 or newer: All above React-datepicker v0.13.0
- React 0.13: React-datepicker v0.13.0
- pre React 0.13: React-datepicker v0.6.2

### Browser Support

The date picker is compatible with the latest versions of Chrome, Firefox, and IE10+.

