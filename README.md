# React Hook: use-script
A React hook to load a script file at runtime.

[![CircleCI](https://img.shields.io/circleci/project/github/ayltai/use-script-hook/master.svg?style=flat)](https://circleci.com/gh/ayltai/use-script-hook) ![Maintenance](https://img.shields.io/maintenance/yes/2020) [![Release](https://img.shields.io/github/release/ayltai/use-script-hook.svg?style=flat)](https://github.com/ayltai/use-script-hook/releases) [![License](https://img.shields.io/github/license/ayltai/use-script-hook.svg?style=flat)](https://github.com/ayltai/use-script-hook/blob/master/LICENSE)

[![Buy me a coffee](https://img.shields.io/static/v1?label=Buy%20me%20a&message=coffee&color=important&style=for-the-badge&logo=buy-me-a-coffee&logoColor=white)](https://buymeacoff.ee/ayltai)

## Installation
```shell script
npm install @ayltai/use-script
```

## Usage
```jsx
// index.jsx
import { useScript, } from '@ayltai/use-script';
import React from 'react';
import { render, } from 'react-dom';
import { StripeProvider, } from 'react-stripe-elements';

import MyStoreCheckout from './MyStoreCheckout';

const App = () => {
    const [ isLoaded, hasError, ] = useScript('https://js.stripe.com/v3/');

    return (
        <>
            {hasError ? isLoaded ? (
                <StripeProvider apiKey=''>
                    <MyStoreCheckout />
                </StripeProvider>
            ) : (
                <div>{`isLoaded = ${isLoaded}`}</div>
            ) : (
                <div>{`hasError = ${hasError}`}</div>
            )}
        </>
    );
};

render(<App />, document.getElementById('root'));
```

## Callback
```js
useScript('https://js.stripe.com/v3/', () => console.log(`Script loaded`));
```
