# Storybook Issue

## Context

I am trying to create a minimal component library package that has support for the following:

* React
* TypeScript
* Babel
* Emotion
* Storybook

I have installed the latest versions of each of these dependencies and am tryig to use the React 17 automatic JSX runtime so that I don't need to include `import React from 'react'`. I have updated my `tsconfig.json` and my `.babelrc` to enable support for this. 

My issue is that running `build-storybook` causes the below error:

```
WARN ./src/Button.stories.tsx 20:2
WARN Module parse failed: Unexpected token (20:2)
WARN File was processed with these loaders:
WARN  * ./node_modules/babel-loader/lib/index.js
WARN  * ./node_modules/@storybook/source-loader/dist/index.js
WARN You may need an additional loader to handle the result of these loaders.
WARN |     backgroundColor: { control: 'color' },
WARN |   },
WARN > } as Meta;
WARN |
WARN | const Template: Story<ButtonProps> = (args) => <Button {...args} />;
WARN  @ \.)(?=.)[^/]*?\.stories\.(js|jsx|ts|tsx))$ (./src sync ^\.(?:(?:^|\/|(?:(?:(?!(?:^|\/)\.).)*?)\/)(?!\.)(?=.)[^/]*?\.stories\.(js|jsx|ts|tsx))$) ./Button.stories.tsx
WARN  @ ./.storybook/generated-stories-entry.js
WARN  @ multi ./node_modules/@storybook/core/dist/server/common/polyfills.js ./node_modules/@storybook/core/dist/server/preview/globals.js ./.storybook/storybook-init-framework-entry.js ./node_modules/@storybook/addon-docs/dist/frameworks/common/config.js-generated-other-entry.js ./node_modules/@storybook/addon-docs/dist/frameworks/react/config.js-generated-other-entry.js ./node_modules/@storybook/addon-links/dist/preset/addDecorator.js-generated-other-entry.js ./node_modules/@storybook/addon-actions/dist/preset/addDecorator.js-generated-other-entry.js ./node_modules/@storybook/addon-actions/dist/preset/addArgs.js-generated-other-entry.js ./node_modules/@storybook/addon-backgrounds/dist/preset/addDecorator.js-generated-other-entry.js ./node_modules/@storybook/addon-backgrounds/dist/preset/addParameter.js-generated-other-entry.js ./.storybook/preview.js-generated-config-entry.js ./.storybook/generated-stories-entry.js
```

My code just has the default `Button.tsx` and `Button.stories.tsx` that Storybook generated. I am suspecting that the issue is coming from either my Babel or TypeScript config, or if I just need to do additional modifications to Storybook config to get this to work.

## How to reproduce:

1. Clone this repo
1. Run `npm install`
1. Run `npm run build` and view the error message show up in the console
