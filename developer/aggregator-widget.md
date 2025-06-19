---
hidden: true
---

# Aggregator Widget

The `@minswap/aggregator-widget` is for token swapping at the best prices across all Cardano DEXes.

## Installation

### React Setup

```bash
npm install @minswap/aggregator-widget
```

or

```bash
yarn add @minswap/aggregator-widget
```

or

```bash
pnpm install @minswap/aggregator-widget
```

### HTML Setup

You can also use the widget directly in HTML without a React build setup. Add the following to your HTML file:

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- Add this part to <head> -->
    <link
      rel="stylesheet"
      href="https://esm.sh/@minswap/aggregator-widget/dist/index.css"
    />
  </head>
  <body>
    <!-- Add this part to <body> -->
    <div id="minswap-widget"></div>
    <script type="importmap">
      {
        "imports": {
          "react": "https://esm.sh/react",
          "react-dom": "https://esm.sh/react-dom",
          "react-dom/": "https://esm.sh/react-dom/",
          "react/jsx-runtime": "https://esm.sh/react/jsx-runtime",
          "@minswap/aggregator-widget": "https://esm.sh/@minswap/aggregator-widget?external=react,react-dom"
        }
      }
    </script>
    <script type="module" src="https://esm.sh/tsx"></script>
    <script type="text/babel">
      import React from "react";
      import ReactDOMClient from "react-dom/client";
      import { Widget } from "@minswap/aggregator-widget";

      ReactDOMClient.createRoot(
        document.getElementById("minswap-widget")
      ).render(<Widget displayMode="full" partnerCode="your-partner-code" />);
    </script>
  </body>
</html>
```

## Basic Usage

```jsx
import { Widget } from "@minswap/aggregator-widget";

function App() {
  return <Widget partnerCode="your-partner-code" displayMode="full" />;
}
```

## Props

Here's a quick overview of all available props:

| Prop               | Type                 | Required | Default       | Description                                                                                   |
| ------------------ | -------------------- | -------- | ------------- | --------------------------------------------------------------------------------------------- |
| `wallet`           | `WalletApi`          | No       | -             | Wallet instance for integration. If not provided, widget handles wallet connection internally |
| `partnerCode`      | `string`             | No       | -             | Your unique partner identification code                                                       |
| `defaultAsset`     | `string`             | No       | -             | Pre-selected asset (cannot be ADA)                                                            |
| `selectableAssets` | `string[]`           | No       | All assets    | List of allowed assets for selection (ADA always included)                                    |
| `allowedProtocols` | `Protocol[]`         | No       | All protocols | List of permitted DEX protocols (Minswap protocols always included)                           |
| `displayMode`      | `"button" \| "full"` | No       | `"full"`      | Widget display mode                                                                           |
| `trigger`          | `ReactNode`          | No       | -             | Custom trigger element for button mode                                                        |

Detailed description of each prop:

### `wallet`

* Type: `WalletApi`
* Optional: Yes
*   Description: An instance of WalletApi for wallet integration. This enables wallet connectivity and transaction functionality within the widget. If not provided, the widget will handle wallet connection internally with its own UI and connection flow. The `WalletApi` type is defined as:

    ```typescript
    type WalletApi = Pick<
      Cip30WalletApi,
      "getUnusedAddresses" | "getUsedAddresses" | "signTx"
    > & {
      id: string;
    };
    ```

    Where:

    * `getUnusedAddresses`: Function to get unused addresses from the wallet
    * `getUsedAddresses`: Function to get previously used addresses from the wallet
    * `signTx`: Function to sign transactions
    * `id`: A unique identifier for the wallet instance. This is crucial for wallet updates within the Widget.

    The interface follows the [CIP-30 Cardano Wallet Standard](https://cips.cardano.org/cips/cip30/), which is the standard specification for Cardano wallet integration.

### `partnerCode`

* Type: `string`
* Optional: Yes
*   Description: A unique code that identifies the partner integrating the widget. To obtain your `partnerCode`:

    1. Visit [minswap.org/partners](https://minswap.org/partners)
    2. Create a new application
    3. Get your unique partner code from the dashboard
    4. Use this code in the widget integration

    The `partnerCode` enables tracking of your application's usage, revenue sharing, and other partnership benefits.

### `defaultAsset`

* Type: `string`
* Optional: Yes
*   Description: The asset that will be pre-selected when the widget initially loads. The string must follow the format `<policyId><tokenName>`, where:

    * `policyId`: The Cardano policy ID of the token (hex string)
    * `tokenName`: The token name in hex format

    Example:

    ```typescript
    // For MIN token
    const minToken =
      "29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c64d494e"; // policyId + "MIN" in hex
    ```

    **Important**: ADA (lovelace) cannot be used as a `defaultAsset`. You must specify a native token.

### `selectableAssets`

* Type: `string[]`
* Optional: Yes
*   Description: An array of assets that users can choose from within the widget. If not provided, all supported assets will be available. Each string in the array must follow the format `<policyId><tokenName>`.

    Example:

    ```typescript
    const assets = [
      "29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c64d494e", // MIN token
      "af65a4734e8a22f43128913567566d2dde30d3b3298306d6317570f60014df104d494e20496e7465726e", // Minswap Intern token
    ];
    ```

    Note:

    * For ADA (lovelace), you can use the special string "lovelace" instead of a policy ID and token name
    * ADA (lovelace) is always included in the selectable assets by default, even if not explicitly specified in the array

### `allowedProtocols`

* Type: `Protocol[]`
* Optional: Yes
*   Description: An array of protocol identifiers that are permitted for use in the widget. This can be used to restrict which protocols are available for swapping. Available protocols include:

    ```typescript
    type Protocol =
      | "MinswapV2"
      | "Minswap"
      | "MinswapStable"
      | "MuesliSwap"
      | "Splash"
      | "SundaeSwapV3"
      | "SundaeSwap"
      | "VyFinance"
      | "WingRidersV2"
      | "WingRiders"
      | "WingRidersStableV2"
      | "Spectrum"
      | "SplashStable";
    ```

    Example:

    ```typescript
    const protocols = ["MuesliSwap", "SundaeSwap", "VyFinance"];
    ```

    **Important Notes**:

    * Minswap protocols ("Minswap", "MinswapV2", "MinswapStable") are always included in the available protocols, regardless of this setting
    * If this prop is not provided, all protocols will be available for routing

### `displayMode`

* Type: `"button" | "full"`
* Optional: Yes
* Default: `"full"`
* Description: Determines how the widget is displayed:
  * `"button"`: The widget appears as a button that, when clicked, opens the full interface
  * `"full"`: The widget is displayed in its complete form directly in the page

### `trigger`

* Type: `ReactNode`
* Optional: Yes
* Description: A custom trigger element for the "button" display mode. This allows you to customize the appearance of the button that opens the widget.

## Examples

### Basic Usage with Full Display Mode

```jsx
import { Widget } from "@minswap/aggregator-widget";

function SwapInterface() {
  return <Widget partnerCode="your-partner-code" displayMode="full" />;
}
```

### Custom Button Trigger

```jsx
import { Widget } from "@minswap/aggregator-widget";

function SwapButton() {
  return (
    <Widget
      partnerCode="your-partner-code"
      displayMode="button"
      trigger={<button className="custom-button">Open Swap</button>}
    />
  );
}
```

## Theming Customization

The widget supports two methods of theme customization: preset themes and custom CSS variables.

### Preset Themes

We provide six predefined themes that you can use out of the box:

* `default-light`
* `default-dark`
* `green-light`
* `green-dark`
* `violet-light`
* `violet-dark`

To use a preset theme, add the `data-ms-theme` attribute to your HTML tag:

```html
<html data-ms-theme="<preset-theme-here>">
  <!-- Your content -->
</html>
```

### Custom CSS Variables

For more granular control over the widget's appearance, you can override the default CSS variables. Create a CSS file with your custom variables:

```css
:root {
  /* Primary interaction tone */
  --ms-itr-tone-pri: #c4e1bc;
  
  /* Highlight tone */
  --ms-itr-tone-hl: #4c7f3a;
  
  /* Subtle tone */
  --ms-itr-tone-sub: #2f5025;
  
  /* Border highlight default */
  --ms-bd-hl-df: #2f5025;
  
  /* Secondary interaction tent default and subtle */
  --ms-itr-tentSec-df: #2f5025;
  --ms-itr-tentSec-sub: #2f5025;
}
```

Then include your CSS file in your HTML, making sure to place it at the end of the head tag to properly override the default styles:

```html
<head>
  <!-- Other stylesheets and meta tags -->
  ...
  <!-- Your custom theme should be last to ensure it overrides default styles -->
  <link rel="stylesheet" href="your-custom-theme.css">
</head>
```

**Note**: The variables shown above are just common examples. You can customize many more CSS variables than those listed. To see the complete list of available CSS variables:

1. Open your browser's DevTools
2. Inspect any element within the widget
3. Look for `:root` or elements with `--ms-` prefixed CSS variables
4. Override any of these variables in your custom CSS file to achieve your desired styling
