## Data models

### Material

Material is the basic data model in the whole app. It contains the following fields:

```
 title: 'Great expectations. Chapter 1.',
 lang: 'en',
 unit: 'GreatExpectationsEn',
 order: '001',
 phrases: { 'phrase1id': { start: 1.06, end: 3.48, text: "Chapter One" }, ... },
 mediaLink: 'fileIdInStorageOrExternalHttpsLink', // 'folder/filename.mp3' or 'https://bbc.com/6minutEnglish.mp3'
 duration: 0, // 45.035 (sec)
 translations: [], // ['ru', 'ar', 'ch'],
 createdBy: {
     userId: uid,
     userName: displayName
     },
 createdAt: 'timestamp[13]',
 updatedAt: 'timestamp[13]',
```

`lang` used for sorting materials. It can also affect display options. `lang:'ar'` loads special fonts and styles for Arabic.

`unit` used for assembling headings from the titles of materials of the same unit.

`order` is the order of a heading. If it is not set, createdAt timestamp will be applied by default.

`phrases` - `start`-`end` is a time interval in an audio file, and `text` is the text related to a particular phrase.

`mediaLink` can be fileId in Cloud Storage, if you loaded your local file. Or it can be external httpS link to an audio file: mp3, ogg,

`duration` length of an audio file in seconds.

`translations` - array of avaliable translations. Used for generating links to each translation.

`createdBy` assigned to material when you add your own material or edit an existing one. Displayed in latest updates on site feed and in revisions section of material.

`createdAt`, `updatedAt` used for ordering materials by agregated blocks like last updates for a particular language, or main page with all events that happened.

### Unit

```
title: 'Great Expectations',
author: 'Charles Dickens',
logo: 'storageId', //png, jpg,
background: 'storageId',
heading: [
    {
        id: materialId,
        title: materialTitle,
        order: '001',
        createdAt: 'timestamp[13]',
        updatedAt: 'timestamp[13]'
    }
]
```

Unit menu appears on click on the sandwich menu-button in the bottom left corner of the screen and allows you to navigate through the materials in a unit, like chapters in a book. Heading is autogenerated on server side and contains info for generating links to materials. Also it contains data for ordering, like `order`, `createdAt` and `updatedAt`.

### MaterialTr

```
title: 'Большие надежды',
lang: 'ru',
for: 'materialId',
phrases: { materialPhrase1id: { text: 'Глава первая' } },
 createdBy: {
     userId: uid,
     userName: displayName
     },
 createdAt: 'timestamp[13]',
 updatedAt: 'timestamp[13]',
```

Translations for Material. Phrases ids are exactly the same as in Material. Both texts will be syncronyzed by them.

Each material can have only one translation for each language, and `translationId` = `materialId_trLang`.

`greatExpectationChapter1` --> `greatExpectationChapter1_ru` - Russian translation for material.

## Following text is autogenerated by Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br>
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br>
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br>
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br>
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br>
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify
