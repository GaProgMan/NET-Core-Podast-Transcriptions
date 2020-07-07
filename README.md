# .NET-Core-Podast-Transcriptions

Transcriptions for all released episodes of The .NET Core Podcast - used for generating all show notes for the website.

This repo was set up in order to ask the community for help with the transcriptions created for the podcast. Currently all transcriptions for the podcast are machine-based ones. They are created using a combination of [otter.ai](https://otter.ai) (a paid service) and [PIT Transcriptor](https://transcriptor.productivityintech.com/) (which leverages paid services). These machine transcriptions are often 60-80% correct, but require tweaking before they are ready for human consumption. In the untweaked format, they are still readable and understandable but may have a few spelling or grammatical issues.

I would like to ask the community for help in spotting and fixing the few issues found in the transcriptions. The (paid) machine transcriptions are sill provided, however finding and fixing all of the issues is a rather large time sink.

In this repo, you will find transcriptions for all of published episodes of the podcast. I will work on these transcriptions, in the open, and all contributors will be acknowledged on the show notes for each episode.

## Contributing

Contributions to this repository are welcome, however please see the [Contributing](./github/contributing) guide before submitting your first pull request.

## Acknowledgement

When submitting a pull request, please think about how you would like to be attributed on the newly rendered show notes page. There is a section in the pull request template for this.

## Shortcodes

The website for The .NET Core Podcast is closed source and uses the Hugo static site generator. As such, some transcriptions may make use of custom [Hugo Shortcodes](https://gohugo.io/content-management/shortcodes/). The source for these custom shortcodes is included in the [shortcodes](/shortcodes) directory as a form of reference. Each short code has documentation, in the form of comments, describing what it does.

If you are a Hugo user, please feel free to re-used these shortcodes elsewhere.