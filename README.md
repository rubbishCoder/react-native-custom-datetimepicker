# react-native-custom-dateTimePicker [![Build Status](https://travis-ci.org/xgfe/react-native-custom-dateTimePicker.svg?branch=master)](https://travis-ci.org/xgfe/react-native-custom-dateTimePicker) [![Coverage Status](https://coveralls.io/repos/github/xgfe/react-native-custom-dateTimePicker/badge.svg?branch=master)](https://coveralls.io/github/xgfe/react-native-custom-dateTimePicker?branch=master) [![Monthly download](https://img.shields.io/npm/dm/react-native-custom-dateTimePicker.svg)](https://img.shields.io/npm/dm/react-native-custom-dateTimePicker.svg) [![Total downloads](https://img.shields.io/npm/dt/react-native-custom-dateTimePicker.svg)](https://img.shields.io/npm/dt/react-native-custom-dateTimePicker.svg)
react native datePicker component for both Android and IOS, using DatePickerAndroid, TimePickerAndroid and DatePickerIOS

## Install

```bash
npm install react-native-custom-dateTimePicker --save
```

Or using [react-native-ui-xg](https://github.com/xgfe/react-native-ui-xg), our react-naitve ui kit.

```bash
npm install react-native-ui-xg --save
```

## Example
Check [index.android.js](https://github.com/xgfe/react-native-custom-dateTimePicker/blob/master/index.android.js) in the Example.

![android](http://xgfe.github.io/react-native-custom-dateTimePicker/img/react-native-custom-dateTimePicker-android.gif)
![ios](http://xgfe.github.io/react-native-custom-dateTimePicker/img/react-native-custom-dateTimePicker-ios.gif)

## Usage

```javascript

import React, { Component } from 'react'
import DatePicker from 'react-native-custom-dateTimePicker'

export default class MyDatePicker extends Component {
  constructor(props){
    super(props)
    this.state = {date:"2016-05-15"}
  }

  render(){
    return (
      <DatePicker
        style={{width: 200}}
        date={this.state.date}
        mode="date"
        placeholder="select date"
        format="YYYY-MM-DD"
        minDate="2016-05-01"
        maxDate="2016-06-01"
        confirmBtnText="Confirm"
        cancelBtnText="Cancel"
        customStyles={{
          dateIcon: {
            position: 'absolute',
            left: 0,
            top: 4,
            marginLeft: 0
          },
          dateInput: {
            marginLeft: 36
          }
          // ... You can check the source to find the other keys.
        }}
        onDateChange={(date) => {this.setState({date: date})}}
      />
    )
  }
}
```

You can check [index.js](https://github.com/xgfe/react-native-custom-dateTimePicker/blob/master/index.android.js) in the Example for detail.

## Properties

| Prop  | Default  | Type | Description |
| :------------ |:---------------:| :---------------:| :-----|
| style | - | `object` | Specify the style of the DatePicker, eg. width, height...  |
| date | - | <code>string &#124; date &#124; Moment instance</code> | Specify the display date of DatePicker. `string` type value must match the specified format |
| mode | 'date' | `enum` | The `enum` of `date`, `datetime` and `time` |
| androidMode | 'default' | `enum` | The `enum` of `default`, `calendar` and `spinner` (only Android) |
| format | 'YYYY-MM-DD' | `string` | Specify the display format of the date, which using [moment.js](http://momentjs.com/). The default value change according to the mode. |
| confirmBtnText | '确定' | `string` | Specify the text of confirm btn in ios. |
| cancelBtnText | '取消' | `string` | Specify the text of cancel btn in ios. |
| iconSource | - | <code>{uri: string} &#124; number</code> | Specify the icon. Same as the `source` of Image, always using `require()` |
| minDate | - | <code>string &#124; date</code> | Restricts the range of possible date values. |
| maxDate | - | <code>string &#124; date</code> | Restricts the range of possible date values. |
| duration | 300 | `number` | Specify the animation duration of datepicker.|
| customStyles | - | `number` | The hook of customize datepicker style, same as the native style. `dateTouchBody`, `dateInput`...|
| showIcon | true | `boolean` | Controller whether or not show the icon |
| hideText | false | `boolean` | Controller whether or not show the `dateText` |
| iconComponent | - | `element` | Set the custom icon |
| disabled | false | `boolean` | Controller whether or not disable the picker |
| is24Hour | - | `boolean` | Set the TimePicker is24Hour flag. The default value depend on `format`. Only work in Android |
| placeholder | '' | `string` | The placeholder show when this.props.date is falsy |
| onDateChange | - | `function` | This is called when the user confirm the picked date or time in the UI. The first and only argument is a date or time string representing the new date and time formatted by [moment.js](http://momentjs.com/) with the given format property. |
| onOpenModal | - | `function` | This is called when the DatePicker Modal open. |
| onCloseModal | - | `function` | This is called when the DatePicker Modal close |
| onPressMask | - | `function` | This is called when clicking the ios modal mask |
| modalOnResponderTerminationRequest | - | `function` | Set the callback for React Native's [Gesture Responder System](https://facebook.github.io/react-native/docs/gesture-responder-system.html#responder-lifecycle)'s call to `onResponderTerminationRequest`. By default this will reject a termination request, but can be overidden in case the View under the Modal is implementing custom gesture responders, and you wish for those to be overidden in certain cases.  |
| TouchableComponent | `TouchableHighlight` | `Component` | Replace the `TouchableHighlight` with a custom `Component`. For example : `TouchableOpacity` |

### Property `customStyles` available keys

* appearance: `dateInput`, `disabled`, `dateTouchBody`, `dateIcon`, `placeholderText`, `dateText`
* ios select panel: `datePickerCon`, `datePicker`, `btnConfirm`, `btnTextConfirm`, `btnCancel`, `btnTextCancel`


## Instance Methods

| Method  | Params  | Description |
| :------------ |:---------------:| :---------------:|
| onPressDate | - | Manually open the date picker panel |
| onPressCancel | - | Manually close the date picker panel like, similarly pressing cancel btn |
