## Currency Converter with React

![alt](./gif/react_currency_converter.gif)

<br/>

Lessons

- Props
- State Management
- Hooks

<br/>

### Basic Initialization

- `npx create-react-app .`

- delete unnecessary files
- index.js

  - delete code related to serviceWorker

- App.css
  - remove all code
- App.js
  - modify HTML code
- `npm start`
  - to check if initialized

<br/>

### Create Single Component

- CurrencyRow.js
  - ES7 React/Redux/React-Native/JS snippets
  - `rfc` snippet
- modify HTML to include CurrencyRow component
- write basic UI

<br/>

### Styling

- `display: flex`
  - line everything up in the center
- `min-height: 100vh;`

  - align vertically

- create classNames and perform styling

<br/>

### Currency API

- http://exchangeratesapi.io/

- `useEffect`
  - to fetch the latest currency information
- console.log the .json returned

<br/>

### Use Props for Passing Currency Information

- setup **state** for application

  - `useState`

    - state for currency list

    - ```javascript
      const [currencyOptions, setCurrencyOptions] = useState([]);

      .then((data) => {
              setCurrencyOptions([data.base, ...Object.keys(data.rates)]);
            });
      ```

    - `currencyOptions` will now have `data.rates`

- pass `currencyOptions` as a prop

<br/>

### Handle Props in CurrencyRow Component

- destructure the props

  - ```javascript
    const { currencyOptions } = props;
    ```

- > Each child in a list should have a unique "key" prop.

  - ```javascript
    <option value={option}>{option}</option>
    ```

<br/>

### Create State for Default Currency

- create states
  1. fromCurrency
  2. toCurrency
- allocate the base currency and the first currency to the state
- pass as props to CurrencyRow Component
- at CurrencyRow
  1. extract the prop
  2. set the value to HTML element with the prop

<br/>

### Hook onChange Event for each Selectors

- pass `onChangeCurrency` function from App.js to CurrencyRow.js component

- ```javascript
  onChangeCurrency={(e) => setFromCurrency(e.target.value)}
  ```

- an inline function that returns e

<br/>

### Declare States for Changes in Input

- 3 states

  1. amount
     - how much of the input is changed
  2. amountInFromCurrency
     - whether the In or From input box has been changed
  3. exchangeRate
     - used to calculate the currency

- amountInFromCurrency === true

  - fromCurrency has been modified

- pass down `amount`

<br/>

### Apply Changes to Each Input Boxes

- CurrencyRow.js
  - add a new `onChange` event at `<input>`
- App.js
  - create 2 handlers
    1. From Currency
    2. To Currency

<br/>

### Allow Change Currency

- `useEffect`

  - ```javascript
    useEffect(() => {}, [fromCurrency, toCurrency]);
    ```

  - whenever `fromCurrency` array or `toCurrency` array changes

  - run the code inside the function

- > Unhandled Rejection (TypeError): Cannot read property 'undefined' of undefined

  - since `useEffect` is called when `fromCurrency` and `toCurrency` are`undefined`

- ```javascript
  if (fromCurrency !== Object.null && toCurrency !== Object.null)
  ```
