# react-hook-consent

React consent management solution for cookies and (external) scripts.

## Features

-   Provides the consent context to components
-   Loads (external) scripts based on consent state
-   Hook to retrieve and change the current consent
-   Optional Banner to approve / decline consent
-   Persists the selection to local storage
-   Ready for Next.js
-   Dark and light mode

## Example

Working examples are provided in the `examples` folder.

## Installation

```bash
yarn add react-hook-consent

# or

npm install react-hook-consent
```

## Basic usage

### Provider

Wrap the application in the `ConsentProvider`. Provide settings via the `options` prop.

```typescript
/*
 * index.tsx
 */

import { ConsentProvider } from 'react-hook-consent';

// ...
<ConsentProvider
    options={{
        services: [
            {
                id: 'myid',
                name: 'MyName',
                scripts: [
                    { id: 'external-script', src: 'https://myscript.com/script.js' },
                    { id: 'inline-code', code: `alert("I am a JavaScript code");` },
                ],
            },
        ],
        theme: 'light', // or 'dark'
    }}
>
    <App />
</ConsentProvider>;
// ...
```

### Banner

Optionally use the banner component to render a banner to show a consent dialogue.

```typescript
/*
 * index.tsx
 */

import { ConsentBanner } from 'react-hook-consent';

// styling
import 'react-hook-consent/dist/styles/style.css';

// ...
<App />
<ConsentBanner>
    <>
        Optional individual consent text including a <a href="test">link</a>
    </>
</ConsentBanner>
```

### Hooks

Use the provided `useConsent` hook to access or update the current consent and show or hide the banner.

```typescript
/*
 * App.tsx
 */

import { useConsent } from 'react-hook-consent';

// ...
const { consent, setConsent, isBannerVisible, toggleBanner } = useConsent();
```
