## Currency Converter with React

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
