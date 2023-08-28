# CrowdSwap Swap Widget

The CrowdSwap Swap Widget is a versatile tool that seamlessly integrates with other applications, providing users with a powerful and user-friendly decentralized finance (DeFi) experience. This innovative widget allows users to access and interact with decentralized exchanges, swapping functionalities, and cross-chain ability directly from their favorite apps.

Integrating the CrowdSwap Swap Widget into your project is a straightforward process that brings the power of cross-chain swaps to your application. By utilizing the standalone component approach, you can seamlessly embed the widget's functionality without requiring extensive technical know-how.

## Here is how you can do it in just a few steps:

### Access Widget Resources
First, access the necessary resources for the widget, including the JavaScript and CSS files. These resources are hosted on our server, ensuring you always have the latest version.

### Include Resources
In your HTML file's <head> section, link to the CrowdSwap widget CSS file to ensure proper styling. Then, place the widget's HTML tag within the <body> section. Customize the configurations like fromTokenAddress, fromChainId, toTokenAddress, toChainId, and theme to match your requirements. Finally, include the widget's JavaScript file at the end of the <body> section. This file will load the widget's functionality and make it interactive on your webpage.

Following these simple steps, you can seamlessly integrate the CrowdSwap Swap Widget into your project, enabling your users to engage in cross-chain swaps easily. This approach ensures that your application benefits from advanced functionality without the complexities of building it from scratch.

## A step-by-step guide to integrating the CrowdSwap Swap Widget into your project

### Include the CSS Stylesheet
Add the following line in the ```<head>``` section of your HTML file to include the widget's CSS stylesheet:

```
<link rel="stylesheet" href="https://widget.crowdswap.org/crowdswap-widget.css">
```

### Add the Widget Element
In your HTML file's ```<body>``` section, add the ```<crowdswap-swap-widget>``` element to embed the CrowdSwap Swap Widget. This element will include the configuration parameters for the widget.

```
<crowdswap-swap-widget
  config='{
    "fromTokenAddress":"0x0000000000000000000000000000000000001010",
    "fromChainId":137,
    "toTokenAddress":"0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE",
    "toChainId":56, 
    "theme":"light" 
}'></crowdswap-swap-widget>
```

Theme can be chosen to be light or dark. This will make the widget's look light or dark.

Make sure to replace the fromTokenAddress, fromChainId, toTokenAddress, and toChainId values with the appropriate token addresses and chain IDs.

### Include the Widget Script
At the end of the ```<body>``` section, include the widget's script just before the closing ```</body>``` tag. This script will initialize and render the widget:

```
<script src="https://widget.crowdswap.org/crowdswap-widget.js"></script>
```

### Test and Verify
Save your HTML file and open it in a web browser. You should see the CrowdSwap Swap Widget, and users can interact with it to perform swaps.

### Adjust Styling (Optional)
If you want to customize the widget's appearance to match your website's design, you can use CSS to further style the widget's components.

Using this easy step-by-step guide, you can integrate the CrowdSwap Swap Widget into your project and bring the power of cross-chain swaps to your business and application.