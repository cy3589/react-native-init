#!/bin/bash
:<<'END'
Need global installed react-native-cli!!
copy shell file and open terminal same directory
sh ./react-native-init.sh
just type your project name
will run create-next-app and setup prettier and eslint with airbnb code convention
END
echo "Need global installed react-native-cli, yarn"
echo "Already installed react-native-cli and yarn?? y/n"
read isAlreadyInstallCli

if [ $isAlreadyInstallCli == Y ] || [ $isAlreadyInstallCli == y ]; then
echo "init with react-native 0.66.4"

echo "Enter your project name(do not type hyphen)"
read projectName

npx react-native init "$projectName" --template react-native-template-typescript@6.8.4
cd "$projectName"
yarn add --dev prettier
yarn add --dev eslint-plugin-prettier
yarn add --dev eslint-config-prettier
npx install-peerdeps --dev eslint-config-airbnb -Y
yarn add --dev @react-native-community/eslint-config
yarn add --dev eslint-plugin-import
yarn add --dev eslint-import-resolver-babel-module
yarn add --dev babel-plugin-module-resolver
yarn add --dev @babel/eslint-parser
yarn add --dev eslint-plugin-react
yarn add --dev @typescript-eslint/eslint-plugin
yarn add --dev @typescript-eslint/parser

echo -e "module.exports = {
  env: {jest: true},
  root: true,
  parser: '@babel/eslint-parser',
  extends: [
    'eslint:recommended',
    '@react-native-community',
    'airbnb',
    'airbnb/hooks',
    'plugin:prettier/recommended',
  ],
  rules: {
    'no-shadow': 'off',
    '@typescript-eslint/no-shadow': ['error'],
    'react/jsx-filename-extension': [
      2,
      {extensions: ['.js', '.jsx', '.ts', '.tsx']},
    ],
    'import/extensions': [
      'error',
      'ignorePackages',
      {js: 'never', jsx: 'never', ts: 'never', tsx: 'never', json: 'never'},
    ],
    'react/function-component-definition': [
      2,
      {namedComponents: 'arrow-function', unnamedComponents: 'arrow-function'},
    ],
    'react/jsx-props-no-spreading': 'off',
    'no-unused-vars': 'off',
    '@typescript-eslint/no-unused-vars': ['error'],
    'no-use-before-define': [
      'error',
      {functions: true, classes: true, variables: false},
    ],
  },
  settings: {
    'import/resolver': {
      'babel-module': {},
      node: {extensions: ['.js', '.jsx', '.ts', '.tsx', '.json']},
    },
  },
};" > .eslintrc.js

echo -e "module.exports = {
  presets: ['module:metro-react-native-babel-preset'],
  plugins: [
    [
      'module-resolver',
      {
        root: ['./src'],
        extensions: ['.ts', '.tsx', '.jsx', '.js', '.json'],
        alias: {'@': './src'},
      },
    ],
  ],
};" > babel.config.js

echo -e "{
  \"compilerOptions\": {
    \"target\": \"esnext\",
    \"module\": \"commonjs\",
    \"lib\": [\"es2017\"],
    \"allowJs\": true,
    \"jsx\": \"react-native\",
    \"noEmit\": true,
    \"isolatedModules\": true,
    \"strict\": true,
    \"moduleResolution\": \"node\",
    \"baseUrl\": \"./src\",
    \"paths\": {\"@/*\": [\"./*\"]},
    \"allowSyntheticDefaultImports\": true,
    \"esModuleInterop\": true,
    \"skipLibCheck\": false,
    \"resolveJsonModule\": true
  },
  \"exclude\": [
    \"node_modules\",
    \"babel.config.js\",
    \"metro.config.js\",
    \"jest.config.js\"
  ]
}" > tsconfig.json

echo -e "/**
 * @format
 */

import 'react-native';
import React from 'react';
import renderer from 'react-test-renderer';
import App from '../App';

// Note: test renderer must be required after react-native.

it('renders correctly', () => {
  renderer.create(<App />);
});" > ./__tests__/App-test.tsx

mkdir src
mkdir src/components
mkdir src/screens
mkdir src/layouts
mkdir src/utils
mkdir src/hooks
mkdir src/typings

echo "# My $projectName ReactNativeApp" > README.md
git add .
git commit -m 'React Native Project Init with Chad_shell'

fi
  exit 0
