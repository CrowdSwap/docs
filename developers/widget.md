# CrowdSwap Swap Widget

The CrowdSwap Swap Widget is a versatile tool that seamlessly integrates with other applications, providing users with a powerful and user-friendly decentralized finance (DeFi) experience. This innovative widget allows users to access and interact with decentralized exchanges, swapping functionalities, and cross-chain ability directly from their favorite apps.

Integrating the CrowdSwap Swap Widget into your project is a straightforward process that brings the power of cross-chain swaps to your application. By utilizing the standalone component approach, you can seamlessly embed the widget's functionality without requiring extensive technical know-how.

## Here is how you can do it in just a few steps:

### Access Widget Resources

First, access the necessary resources for the widget, including the JavaScript and CSS files. These resources are hosted on our server, ensuring you always have the latest version.

### Include Resources

In your HTML file's <body> section, place the widget's HTML tag. Customize the configurations like fromTokenAddress, fromChainId, toTokenAddress, toChainId, and theme to match your requirements. Finally, include the widget's JavaScript file at the end of the <body> section. This file will load the widget's assets and make it interactive on your webpage.

Following these simple steps, you can seamlessly integrate the CrowdSwap Swap Widget into your project, enabling your users to engage in cross-chain swaps easily. This approach ensures that your application benefits from advanced functionality without the complexities of building it from scratch.

## A step-by-step guide to integrating the CrowdSwap Swap Widget into your project

### Add the Widget Element

In your HTML file's `<body>` section, add the `<crowdswap-swap-widget>` element to embed the CrowdSwap Swap Widget. This element will include the configuration parameters for the widget.

```
<crowdswap-swap-widget
  id="crowdswapWidget"
  config='{
    "fromTokenAddress":"0x0000000000000000000000000000000000001010",
    "fromChainId":137,
    "toTokenAddress":"0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE",
    "toChainId":56,
    "theme":"light",
    "affiliateId":"your affiliate Id"
}'></crowdswap-swap-widget>
```

| property name    | description                                                          |
| ---------------- | -------------------------------------------------------------------- |
| fromTokenAddress | default from token for first time visitors                           |
| fromChainId      | default network that will be looked up for from token address        |
| toTokenAddress   | default to token for first time visitors                             |
| toChainId        | default network that will be looked up for to token address          |
| theme            | can be light or dark. This will make the widget's look light or dark |
| affiliateId      | your Affiliate IDs                                                   |

You can receive your affiliate ID by using this [ link ](https://crowdswap.org/ambassador-program/).

By using the affiliate ID key, you will earn commission whenever any user registers and trades through your website. This commission is usually calculated based on the trading volume. By using an affiliate ID, CrowdSwap can track your performance and deposit earned commission amount into your account.

Make sure to replace the fromTokenAddress, fromChainId, toTokenAddress, and toChainId values with the appropriate token addresses and chain IDs.

### Include the Widget Script

At the end of the `<body>` section, include the widget's script just before the closing `</body>` tag. This script will initialize and render the widget:

```
<script src="https://widget.crowdswap.org/loadAssets.js"></script>
```

### Test and Verify

Save your HTML file and open it in a web browser. You should see the CrowdSwap Swap Widget, and users can interact with it to perform swaps.

### Custom Splash Loading (Optional)

To customize the splash loading, start by adding the CSS code snippet to your CSS file:

```
.app-splash-screen {
    display: none !important;
}
```

Next, create your splash loading within an HTML tag with the given ID (below), so that the functions can work properly:

```
<div id="splash-div"></div>
```

### Adjust Styling (Optional)

If you want to customize the widget's appearance to match your website's design, you can use CSS to further style the widget's components.

Using this easy step-by-step guide, you can integrate the CrowdSwap Swap Widget into your project and bring the power of cross-chain swaps to your business and application.
