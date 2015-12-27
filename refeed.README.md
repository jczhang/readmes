# refeed

Hoarded a bunch of images or links from the internet, but never really flip through them again? Still go on reddit or hacker news for that hit of novel information, but find it shallow?

refeed is a tool that simulates a mindless internet browsing experience, but with sources drawn from your saved data, which you've already prefiltered from the internet. It helps you process information that you've seen before, but never got the chance to fully digest or evaluate.

## how it works

1. Link sources. In the `config.json` file, specify the types of sources your information comes from. Planned support is for local directories for images and browser bookmark dumps for internet links. If this proves useful, maybe support will be added for hot-reloading of feeds and online-sourced live feeds.

Example config:
```
{
  "version": "0.1",
  "feeds": [
    {
      "name": "internet lolz",
      "types": ["png", "jpeg", "gif", "webp", "webm"],
      "sources": [
        {
          "type": "directory",
          "uri": "file://~/images/"
        }
      ],
      "tags": ["upvote", "downvote"],
    },
    {
      "name": "bookmarks",
      "types": ["url"],
      "sources": [
        {
          "type": "html",
          "uri": "file://~/dump_of_bookmarks.html"
        }
      ],
      "tags": ["tldr", "science"],
    },
  ],
}
```

2. Start the webserver with `npm run`. It uses your sources to generate feeds. Navigate to http://localhost:4330 to view the site.

3. Use tags to organize your stuff. You can specify prefilled tags for each feed that you can click on to quickly mark an item. The tags and any metadata are saved in `metadata.json`. When the server is reloaded, data is reloaded from this file.

4. Use any of the included reorganizer tools to reorganize your files or links according to the tags you've given it. Each tool reads from the `metadata.json` and does something specific to the tool, so make sure to call them with `--help` for options.

