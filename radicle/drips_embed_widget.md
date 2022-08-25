# Drips Widget - Work Proposal

RFP detailed here:
- https://github.com/radicle-dev/radicle-grants/blob/main/rfps/embed_widget_rfp.md
- https://radicle.community/t/rfp-make-drips-communities-embeddable-on-any-site-as-a-login-gate/2670

## Proposed Tech and Reasoning

#### Web Components using StencilJS
Web Components offer a standard way of creating parts of a website that are compartmentalized away from the actual website's logic and styling. 

Specifically the reason for using Stencil is to provide extras that will:
- Uses a very similiar compile time version of React.js
	- While it uses React and JSX templating for the components, they aren't a dependancy for the final product. The components ultimately just compile to standard web components. 
	- If any additional development needs doing, it can be easily be done by a React dev with minimal ramp-up on the framework. 
- Provide fallbacks for older browser support
- Unit testing is easy to use and comes standard (Uses Jest)
- While I haven't tried it, some research I've done makes it seem like web components can also be used in a IOS/Android apps. 

#### Styling done with SCSS

SCSS just adds a small extra layer of features to css. Mostly just for import/exports, variables, and the nested dependancies are easier to read.

I plan to pull the styles from the main website as a starting point for color palette / fonts / etc.

Styles will be protected by Shadow DOM (so the main website's styles don't leak into the component), and will expose anything that you think a user would like to customize through css variables.

## Creator Usage

Given the exact details of what kinds of parameters a user can change, an example of what a user would configure would be something like this:

1. Copy/Paste script (or two if using the fallback) to your website: `<script src="example.cdn/drips-widget/(version)/index.js"></script>` 
   Alternatively, they can download the script files themselves and host them. 
2. Copy/Paste the component, and change parameters. Could even put a little interactive form in front of it if desired. 
```
<drips-join-button
	community-name="Radicle"
	payment-wallet-chain="ETH"
	payment-wallet-public-key="0x000..."
	payment-token="USDC"
	payment-token-amount="0.1"
	gated-element=".main-wrapper-thing"
	on-payment-success="(details) => {console.log("Success", details)}"
	//Etc...
>
</drips-join-button>
```

For a "gated" feature, the implementer would need to be slightly more savvy to find the page element they would want as the "gated" portion, but easily done if provided as another parameter.

3. The implementer would also likely need to listen for specific events that the component will emit. Things to expect would be:
	- User hits page, is already a member, emits member details for consumer, hides button (maybe)
	- User successfully signs up. Consumer might want to redirect, or use specific details for the webpage / app.
	- User fails signup, consuming website might want to know for a reason I can't think of.


## Developer Background

I've been a professional web developer for about 10 years. Most of the work I've done is closed source, so I don't have much to openly show. I do have one website I developed for myself to demonstrate my ability to develop and showcase a small window into myself. I had a lot of fun learning HTML5 animations just for the cube thing. 😀

Github: 
https://github.com/NewDark90
Website Code:
https://github.com/NewDark90/zachary-dow.crypto
Website through an unstoppable domain:
https://zachary-dow.crypto/
Direct link to an IPFS web provider:
https://bafybeifhbjfcdfpoiehzxvvtnnihfbhg5zn4fesk7riitlmub5ug6fsixq.ipfs.dweb.link/

I would love to work on this project and it feels like a great fit. Further contact info is on my website.