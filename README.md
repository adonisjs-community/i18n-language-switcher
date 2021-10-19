# AdonisJS language switcher

The repo contains code for a demo application that showcase how to implement a language switcher.

The language switcher stores the user preferred language within sessions and displays the translated text for the selected language.

## Usage
Following are the steps to get the application running on your computer.

- Clone the repo
- Install dependencies by running `npm install` or `yarn install`
- Copy `.env.example` to `.env`.
- Start the development server by running `node ace serve --watch`

Visit the homepage and use the language dropdown on the top right to switch between the languages.

## Storing the preferred language

- Everytime the user selects a language, we make a POST request to the `/language/:locale` endpoint and update the user language to the selected language.
- Yes, it should be a POST request and not GET. The `GET` requests can have unwanted side-effects if you have prefetching enabled.

## Displaying translated content

- On every HTTP request, the `DetectUserLocale` midddleware reads the user preferred language from the session.
- Check it against the locales supported by the application.
- And uses the `switchLocale` method to update the locale for the rest of the request.
- From here on `ctx.i18n` and the `t` helper inside templates will use the user preferred language.
