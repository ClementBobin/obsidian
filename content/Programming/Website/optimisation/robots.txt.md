# Understanding `robots.txt` in Websites

## What is `robots.txt`?

`robots.txt` is a simple text file used by websites to communicate with web crawlers and other automated agents, such as search engine bots. It provides instructions on which parts of a site should not be crawled or indexed.

## Purpose

The primary purpose of `robots.txt` is to manage and control web crawler access to specific areas of a website. It helps website owners dictate which pages or sections should be excluded from search engine results or other automated processes.

## Basic Syntax

Here's a simple syntax of a `robots.txt` file:

```txt
User-agent: [user-agent-name] 
Disallow: [URL path]
```

- **User-agent:** Specifies the web crawler or user agent to which the rule applies. It can be a specific bot or a wildcard (*) for all bots.
    
- **Disallow:** Indicates the URLs or paths that the specified user agent should not crawl. Multiple `Disallow` directives can be used for different paths.
    

## Examples

### Allow all crawlers to access all content:

```txt
User-agent: * 
Disallow:
```

### Disallow all crawlers from accessing a specific directory:

```
User-agent: * 
Disallow: /private/
```

### Disallow a specific crawler from accessing the entire site:

```
User-agent: BadBot 
Disallow: /
```

>Disallow should only have one path from root on the same line
### Disallow specific file

```txt
User-agent: *
Disallow: /~joe/junk.html
Disallow: /~joe/foo.html
Disallow: /~joe/bar.html
```
### Disallow all same type of file
```txt
User-agent: Googlebot
Disallow: /*.xls$
```
## Best Practices

1. **Use Specific Directives:** Clearly specify which user agents should follow the rules. Avoid using generic rules for all bots unless necessary.
    
2. **Testing:** Regularly test your `robots.txt` file using tools provided by search engines to ensure it works as intended.
    
3. **Place in Root Directory:** Store the `robots.txt` file in the root directory of your website (e.g., `https://example.com/robots.txt`).
    
4. **Comments:** Use comments to explain complex rules or to provide information about the file.
    

```
# This is a comment 
User-agent: * 
Disallow: /private/  # Do not crawl the private directory
```

### Sitemap
if you website have more then 500 page or **Your site is new and has few external links to it**, or **Your site has a lot of rich media content (video, images) or is shown in Google News**, you should add a Sitemap at the end

A _sitemap_ is a file where you provide information about the pages, videos, and other files on your site, and the relationships between them. Search engines like Google read this file to crawl your site more efficiently. A sitemap tells Google which pages and files you think are important in your site, and also provides valuable information about these files. For example, when the page was last updated and any alternate language versions of the page.

You can use a sitemap to provide information about specific types of content on your pages, including [video](https://developers.google.com/search/docs/crawling-indexing/sitemaps/video-sitemaps), [image](https://developers.google.com/search/docs/crawling-indexing/sitemaps/image-sitemaps), and [news](https://developers.google.com/search/docs/crawling-indexing/sitemaps/news-sitemap) content. For example:

- A sitemap _video entry_ can specify the video running time, rating, and age-appropriateness rating.
- A sitemap _image entry_ can include the location of the images included in a page.
- A sitemap _news entry_ can include the article title and publication date.

If you're using a CMS such as WordPress, Wix, or Blogger, it's likely that your CMS has already [made a sitemap available to search engines](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap#cmssitemap) and you don't have to do anything.
![](https://www.youtube.com/watch?v=JlamLfyFjTA)
```txt
Sitemap: https://www.example.com/sitemap.xml
```
If you decided that you need a sitemap, [learn more about how to create one](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap).
## Conclusion

`robots.txt` is a crucial tool for webmasters to control how search engines access and index their websites. Properly configuring this file ensures a more effective and efficient crawling process.

For more detailed information, refer to the [official Robots Exclusion Protocol documentation](http://www.robotstxt.org/robotstxt.html).

[Google doc](https://developers.google.com/search/docs/crawling-indexing/robots/create-robots-txt?visit_id=638374037014459520-2032126718&rd=1)
