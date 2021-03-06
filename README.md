# Facebook Browser

A searchable index of your favorite Facebook pages.

![Screenshot](screenshot.png)

## Generate the index

Use the [facebook-indexer](https://github.com/specious/facebook-indexer) script, which in turn uses the [facebook-cli](https://github.com/specious/facebook-cli) tool, to generate the page index and image files of the Facebook pages that you follow.

The app loads the index of facebook pages from `app/data/index.json`, where pages are listed by their id and title:

```json
[
  {"id": "117420464947628", "title": "Seattle's Best Coffee"},
  {"id": "131183430264736", "title": "Maxine Hardcastle"},
  {"id": "2036034379955344", "title": "Bodum"},

  ...
]
```

Thumbnail images are expected to reside in `app/data/images/`, named only by their id (no extension). Images might be JPEG, PNG, etc. but no distinction is made based on the file format.

### Try the sample index

To get started right away with a sample index:

```
cp -r app/data/images-sample app/data/images
cp app/data/index-sample.json app/data/index.json
```

There's not much there, but you can see how it works.

### Build an index of the entire set of pages you have Liked on Facebook

- Install and configure [facebook-cli](https://github.com/specious/facebook-cli)
- Clone the [facebook-indexer](https://github.com/specious/facebook-indexer) repository
- Build the page index with:
  ```
  make FORMAT=json ICON_HEIGHT=50
  ```
- Place the `index.json` file and the `images/` directory in this project's `app/data/` folder.

## Build and run

Install dependencies and build the user interface with:

```
yarn install
yarn build
```

Then you can open `app/index.html` in your browser.

However, the data won't load because requesting a file from a file:// URI falls under the policy of blocking cross-origin requests [implemented by browsers](https://stackoverflow.com/a/23118676) due to security concerns. Run:

```
yarn serve
```

This will start a local server and open the index page in your default browser.

## Share online

You can upload your searchable index online and share it. Everything is in the `app/` directory.

## Develop

This application is written in [Elm](http://elm-lang.org). The Elm compiler builds the JavaScript bundle which powers the final product.

To start the source file watcher and local server, run:

```
yarn start
```

## License

ISC
