> ## This project is a modified version of this one, https://www.npmjs.com/package/react-native-input-credit-card

# React Native CreditCard
Credit Card Input for React Native Project

<p align="center">
<img src="https://github.com/rajeshsmallarc/react-native-creditcard/blob/master/example/image/Example.png?raw=true" width=200/>
</p>

Code:

```js
<CreditCardInput onChange={this._onChange} />
```


# Features
* credit-card 💳 (inspired by: [card](https://jessepollak.github.io/card/), [react-native-input-credit-card](https://www.npmjs.com/package/react-native-input-credit-card))
* Credit-card input validations & formatting while you're typing
* Form is fully navigatable using keypad
* Works on both Android and iOS

# Usage

```bash
npm i @rajeshsmallarc/react-native-creditcard --save
```

then add these lines in your react-native codebase

```js
import { CreditCardInput } from "@rajeshsmallarc/react-native-creditcard";

<CreditCardInput onChange={this._onChange} />

```

And then on your onChange handler:

```js
_onChange => card => console.log(card);

// will print:
{
  valid: true, // will be true once all fields are "valid" (time to enable the submit button)
  values: { // will be in the sanitized and formatted form
  	number: "4242 4242 4242 4242",
  	expiry: "12/25",
  	cvc: "123",
  	type: "visa", // will be one of [null, "visa", "master-card", "american-express", "diners-club", "discover", "jcb", "unionpay", "maestro"]
  	name: "Rajesh",
  	postalCode: "123456",
  },
  status: {  // will be one of ["incomplete", "invalid", and "valid"]
	number: "incomplete",
	expiry: "incomplete",
	cvc: "incomplete",
	name: "incomplete", 
	postalCode: "incomplete",
  },
};

// Notes: 
// You can enable/disable cvc, name using requiresCVC, requiresName, requiresPostalCode)

// Example: 

<CreditCardInput 
	onChange={this._onChange} 
	requiresName
	requiresPostalCode
/>
```


## CreditCardInput
| Property | Type | Description |
| --- | --- | --- |
|autoFocus | PropTypes.bool | Automatically focus Card Number field on render|
|onChange | PropTypes.func | Receives a `formData` object every time the form changes |
|onFocus | PropTypes.func | Receives the name of currently focused field |
|labels | PropTypes.object | Defaults to <br/>`{ number: "CARD NUMBER", expiry: "EXPIRY", cvc: "CVC/CCV" }` |
|placeholders | PropTypes.object | Defaults to <br/>`{ number: "1234 5678 1234 5678", expiry: "MM/YY", cvc: "CVC" }` |
|cardScale | PropTypes.number | Scales the credit-card view.<br/>Defaults to `1`, which translates to `{ width: 300, height: 190 }` |
|cardFontFamily | PropTypes.string | Font family for the CreditCardView, works best with monospace fonts. Defaults to Courier (iOS) or monospace (android) |
|cardImageFront | PropTypes.number | Image for the credit-card view `e.g. require("./card.png")` |
|cardImageBack | PropTypes.number | Image for the credit-card view `e.g. require("./card.png")` |
|labelStyle | Text.propTypes.style | Style for credit-card form's labels |
|inputStyle | Text.propTypes.style | Style for credit-card form's textInput |
|inputContainerStyle | ViewPropTypes.style | Style for textInput's container<br/> Defaults to: `{ borderBottomWidth: 1, borderBottomColor: "black" }` |
|validColor | PropTypes.string | Color that will be applied for valid text input. Defaults to: "{inputStyle.color}" |
|invalidColor | PropTypes.string | Color that will be applied for invalid text input. Defaults to: "red" |
|placeholderColor | PropTypes.string | Color that will be applied for text input placeholder. Defaults to: "gray" |
|requiresName | PropTypes.bool | Shows cardholder's name field<br/> Default to `false` |
|requiresCVC | PropTypes.bool | Shows CVC field<br/> Default to `true` |
|requiresPostalCode | PropTypes.bool | Shows postalCode field<br/> Default to `false` |
|validatePostalCode | PropTypes.func | Function to validate postalCode, expects `incomplete`, `valid`, or `invalid` as return values|
|allowScroll | PropTypes.bool | enables horizontal scrolling on CreditCardInput <br/> Defaults to `false` |
|cardBrandIcons | PropTypes.object | brand icons for CardView. see `./src/Icons.js` for details |
| additionalInputsProps | PropTypes.objectOf(TextInput.propTypes) | An object with Each key of the object corresponding to the name of the field. Allows you to change all props documented in [RN TextInput](https://facebook.github.io/react-native/docs/textinput.html).

#### Note on additionalInputsProps

additionalInputsProps gives you more control over the inputs in CreditCardInput. An example object is as follows:
```javascript
addtionalInputsProps = {
  name: {
    defaultValue: 'my name',
    maxLength: 40,
  },
  postalCode: {
    returnKeyType: 'go',
  },
};
```

The above would set the default value of the name field to `my name` and limit the input to a maximum of 40 character. In addition, it would set the returnKeyType of the postalcode field to `go`.

# Methods
## setValues
Set values into credit card form


```js
	// sets 4242 4242 4242 4242 on credit card number field
	// other fields will stay unchanged
	this.refs.CCInput.setValues({ number: "4242 4242 4242 4242" });
```

## focus
focus on to specified field

```js
	// focus to expiry field
	this.refs.CCInput.focus("expiry");
```

# Missing Something? Something is not working?
* Open a GitHub issue or Send a pull request

# TODO
* Rewrite using hooks aiming performance and simplicity
* Add unit and integration tests
