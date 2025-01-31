# NativeScript-Toasty

[![npm](https://img.shields.io/npm/v/nativescript-toasty.svg)](https://www.npmjs.com/package/nativescript-toasty)
[![npm](https://img.shields.io/npm/dt/nativescript-toasty.svg?label=npm%20downloads)](https://www.npmjs.com/package/nativescript-toasty)

## Install

`tns plugin add nativescript-toasty`

## Usage

TypeScript

```js
import { Toasty } from 'nativescript-toasty';
// Toasty accepts an object for customizing its behavior/appearance. The only REQUIRED value is `text` which is the message for the toast.
const toast = new Toasty({ text: 'Toast message' });
toast.show();

// you can also chain the methods together and there's no need to create a reference to the Toasty instance with this approach
new Toasty({ text: 'Some Message' })
  .setToastDuration(ToastDuration.LONG)
  .setToastPosition(ToastPosition.BOTTOM)
  .setTextColor(new Color('white'))
  .setBackgroundColor('#ff9999')
  .show();

// or you can set the properties of the Toasty instance
const toasty = new Toasty({
  text: 'Somethign something...',
  position: ToastPosition.TOP,
  android: { yAxisOffset: 100 },
  ios: {
    anchorView: someButton.ios, // must be the native iOS view instance (button, page, action bar, tabbar, etc.)
    displayShadow: true,
    shadowColor: '#fff000',
    cornerRadius: 24
  }
});

toasty.duration = ToastDuration.SHORT;
toasty.textColor = '#fff';
toasty.backgroundColor = new Color('purple');
toasty.show();
```

JavaScript

```js
var toasty = require('nativescript-toasty').Toasty;
var toast = new toasty({ text: 'Toast message' });
toast.show();
```

### API

```typescript

  constructor(opts: ToastyOptions);

  position: ToastPosition;

  duration: ToastDuration;

  textColor: Color | string;

  backgroundColor: Color | string;

  /**
   * Show the Toasty
   */
  show();

  /**
   * Cancels the Toasty
   */
  cancel();

/**
 * Sets the Toast position.
 */
  setToastPosition(value: ToastPosition): Toasty;

/**
 * Sets the Toast duration.
 */
  setToastDuration(value: ToastDuration): Toasty;

/**
  * Set the text color of the toast.
  * @param value [Color | string] - Color of the string message.
  */
  setTextColor(value: Color | string): Toasty;

/**
  * Set the background color of the toast.
  * @param value [Color |  string] - Color of the background.
  * On Android this currently removes the default Toast rounded borders.
  */
  setBackgroundColor(value: Color | string): Toasty;
```

```typescript
export enum ToastDuration {
  'SHORT',
  'LONG'
}

export enum ToastPosition {
  'BOTTOM'
  'CENTER'
  'TOP'
}

export interface ToastyOptions {
  /**
   * Message text of the Toast.
   */
  text: string;

  /**
   * Duration to show the Toast.
   */
  duration?: ToastDuration;

  /**
   * Position of the Toast.
   */
  position?: ToastPosition;

  /**
   * Text color of the Toast message.
   */
  textColor?: Color | string;

  /**
   * Background Color of the Toast.
   */
  backgroundColor?: Color | string;

  /**
   * Android specific configuration options.
   */
  android?: { yAxisOffset: number };

  /**
   * iOS Specific configuration options.
   */
  ios?: {
    /**
     * The native iOS view to anchor the Toast to.
     */
    anchorView?: any;

    /**
     * The number of lines to allow for the toast message.
     */
    messageNumberOfLines?: number;

    /**
     * The corner radius of the Toast.
     */
    cornerRadius?: number;

    /**
     * True to display a shadow for the Toast.
     */
    displayShadow?: boolean;

    /**
     * The color of the shadow. Only visible if `displayShadow` is true.
     */
    shadowColor?: Color | string;
  };
}
```
