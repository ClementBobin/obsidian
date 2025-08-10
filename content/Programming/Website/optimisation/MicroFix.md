# add canonical links to your pages
When multiple pages have similar content, search engines consider them duplicate versions of the same page. For example, desktop and mobile versions of a product page are often considered duplicates.

Search engines select one of the pages as the _canonical_, or primary, version and **crawl** that one more. Valid canonical links let you tell search engines which version of a page to crawl and display to users in search results.

**Key term:** _Crawling_ is how a search engine updates its index of content on the web.

Using canonical links has many advantages:

- It helps search engines consolidate multiple URLs into a single, preferred URL. For example, if other sites put query parameters on the ends of links to your page, search engines consolidate those URLs to your preferred version.
- It simplifies tracking methods. Tracking one URL is easier than tracking many.
- It improves the page ranking of syndicated content by consolidating the syndicated links to your original content back to your preferred URL.

## How the Lighthouse canonical links audit fails

[Lighthouse](https://developer.chrome.com/docs/lighthouse/overview) flags any page with an invalid canonical link:

![Lighthouse audit showing document with invalid canonical link](https://developer.chrome.com/static/docs/lighthouse/seo/canonical/image/lighthouse-audit-showing-60ba306d9d197.png)

A page fails this audit if any of the following conditions are met:

- There is more than one canonical link.
- The canonical link is not a valid URL.
- The canonical link points to a page for a different region or language.
- The canonical link points to a different domain.
- The canonical link points to the site root. Note that this scenario may be valid in some scenarios, such as for AMP or mobile page variations, but Lighthouse nonetheless treats it as a failure.

There are two options for specifying a canonical link.

**Option 1:** Add a `<link rel=canonical>` element to the `<head>` of the page:

```
<!doctype html>
<html lang="en">  
	<head>    
		…    
		<link rel="canonical" href="https://example.com"/>    
		…  
	</head>  
	<body>    
		…  
	</body>
</html>
```

**Option 2:** Add a `Link` header to the HTTP response:

```
Link: https://example.com; rel=canonical
```

For a list of the pros and cons of each approach, see Google's [Consolidate duplicate URLs](https://support.google.com/webmasters/answer/139066) page.

### General guidelines

- Make sure that the canonical URL is valid.
- Use secure [HTTPS](https://web.dev/articles/why-https-matters) canonical URLs rather than HTTP whenever possible.
- If you use [`hreflang` links](https://developer.chrome.com/docs/lighthouse/seo/hreflang) to serve different versions of a page depending on a user's language or country, make sure that the canonical URL points to the proper page for that respective language or country.
- Don't point the canonical URL to a different domain. Yahoo and Bing don't allow this.
- Don't point lower-level pages to the site's root page unless their content is the same.
### Google-specific guidelines

- Use the [Google Search Console](https://search.google.com/search-console/index) to see which URLs Google considers canonical or duplicative across your entire site.
- Don't use Google's URL removal tool for canonization. It removes _all_ versions of a URL from search.
# add Web app manifest or service worker
Installability is a core requirement of [Progressive Web Apps (PWAs)](https://web.dev/explore/progressive-web-apps#make-it-installable). By prompting users to install your PWA, you allow them to add it to their home screens. Users who add apps to home screens engage with those apps more frequently.

A [web app manifest](https://web.dev/articles/add-manifest) includes key pieces of information required to make your app installable.

```html
<link rel="manifest" href="/manifest.json">
```

manifest.json

```json
{

	"name": "Clement | Portfolio",
	
	"short_name": "MyPortfolio",
	
	"description": "Welcome to my portfolio! I am a passionate student striving to excel in the world of design, coding, and animation. Explore my projects and journey as I enhance my skills and pursue my ambitions in the tech and creative industry.",
	
	"start_url": "/",
	
	"display": "standalone",
	
	"background_color": "#000000",
	
	"theme_color": "#ffffff",
	
	"icons": [
	
		{
		
		"src": "/public/c-logo.png",
		
		"sizes": "192x192",
		
		"type": "image/png"
		
		}
	
	]

}
```
# add a theme for meta
## How to set a theme color for the address bar

### Step 1: Add a `theme-color` meta tag to every page you want to brand

The `theme-color` meta tag ensures that the address bar is branded when a user visits your site as a normal webpage. Set the tag's `content` attribute to any valid CSS color value:

```html
<!DOCTYPE html>
<html lang="en">
	<head>  
		…  
		<meta name="theme-color" content="#317EFB"/>  
		…
	</head>
	…
```

Learn more about the `theme-color` meta tag in Google's [Support for `theme-color` in Chrome 39 for Android](https://developer.chrome.com/blog/support-for-theme-color-in-chrome-39-for-android).

### Step 2: Add the `theme_color` property to your web app manifest

The `theme_color` property in your web app manifest ensures that the address bar is branded when a user launches your PWA from the home screen. Unlike the `theme-color` meta tag, you only need to define this once, in the [manifest](https://web.dev/articles/add-manifest). Set the property to any valid CSS color value:

```json
{  
	"theme_color": "#317EFB"  
	…
} 
```
# How to make your page fit on mobile screens

This audit is a roundabout way of determining if your page is optimized for mobile devices. See Google's [Responsive Web Design Basics](https://web.dev/articles/responsive-web-design-basics) for an overview of how to create a mobile-friendly page.

You can ignore this audit if:

- Your site does not need to be optimized for mobile screens.
- The content width of your page is intentionally smaller or larger than the viewport width.

```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```
## How to add maskable icon support to your PWA

1. Use [Maskable.app Editor](https://maskable.app/editor) to convert an existing icon to a maskable icon.
2. Add the `purpose` property to one of the `icons` objects in your [web app manifest](https://developer.chrome.com/add-manifest). Set the value of `purpose` to `maskable` or `any maskable`. See [Values](https://developer.mozilla.org/docs/Web/Manifest/icons#Values).
    
    ```json
    {
	    …
	    "icons": [
		    …
		    {
			    "src": "path/to/maskable_icon.png",
			    "sizes": "196x196",
			    "type": "image/png",
			    "purpose": "any maskable"
			}
		]
		…
	}
    ```
# Source map
## Debug your original code instead of deployed with source maps

![](https://youtu.be/SkUcO4ML5U0)

Keep your client-side code readable and debuggable even after you've combined, minified or compiled it. Use [source maps](https://web.dev/articles/source-maps) to map your source code to your compiled code in the **Sources** panel.

## Get started with preprocessors

Source maps from preprocessors cause DevTools to load your original files in addition to your minified ones.

Chrome will actually run your minified code but the **Sources** panel will show you the code you author. You can set breakpoints and step through code in source files and all the errors, logs, and breakpoints will automatically map.

This gives you the appearance of debugging the code as you wrote it, as opposed to code that is served by your development server and executed by the browser.

To use source maps in the **Sources** panel:

- Use only the preprocessors that can produce source maps.
- Verify that your web server can serve source maps.

### Use a supported preprocessor

Common preprocessors used in combination with source maps include but aren't limited to:

- Transpilers: [Babel](https://babeljs.io/)
- Compilers: [TypeScript](http://www.typescriptlang.org/) and [Dart](https://www.dartlang.org/)
- Minifiers: [terser](https://github.com/terser/terser)
- Bundlers and development servers: [Webpack](https://webpack.js.org/), [Vite](https://vitejs.dev/), [esbuild](https://esbuild.github.io/), and [Parcel](https://parceljs.org/)

For an extended list, see [Source maps: Languages, tools, and other info](https://github.com/ryanseddon/source-map/wiki/Source-maps:-languages,-tools-and-other-info).

## Enable source maps in Settings

In ![Settings.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/settings-73dc87819fafb.svg) [**Settings** > **Preferences** > **Sources**](https://developer.chrome.com/docs/devtools/settings/preferences#sources), make sure to check ![Checkbox.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/checkbox-45172ef37cc9.svg) **Enable JavaScript source maps**.

**Note:** You might also want to check ![Checkbox.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/checkbox-9bfa93cde4b6c.svg) **Enable CSS source maps**.

## Check if source maps loaded successfully

See [Developer Resources: View and load source maps manually](https://developer.chrome.com/docs/devtools/developer-resources).

## Debugging with source maps

**Note:** This tutorial uses [this demo](https://github.com/jecfish/parcel-demo) as an example.

With source maps [ready](https://developer.chrome.com/docs/devtools/javascript/source-maps/?utm_source=lighthouse&utm_medium=devtools#use_a_supported_preprocessor) and [enabled](https://developer.chrome.com/docs/devtools/javascript/source-maps/?utm_source=lighthouse&utm_medium=devtools#enable_source_maps_in_settings), you can do the following:

1. [Open your website's sources](https://developer.chrome.com/docs/devtools/javascript#sources-ui) in the **Sources** panel.
2. To focus only on the code you author, [group authored and deployed files in the file tree](https://developer.chrome.com/docs/devtools/javascript/reference#group-authored-and-deployed). Then expand the ![Authored.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/authored-a9321b5e63113.svg) **Authored** section and open your original source file in the **Editor**.
    
    ![The original file opened in the Authored section.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/original-source-file.jpg)
    
3. [Set a breakpoint](https://developer.chrome.com/docs/devtools/javascript/breakpoints) as you normally would. For example, a [logpoint](https://developer.chrome.com/docs/devtools/javascript/breakpoints#log-loc). Then run the code.
    
    ![A logpoint set in an authored file.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/a-logpoint-set-an-author-f6c463bb210b.png)
    
4. Notice that the **Editor** puts a link to the deployed file in the status bar at the bottom. Similarly, it does so for deployed CSS files.
    
    ![A link to the deployed CSS files in the status bar.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/a-link-the-deployed-css-01cdebccb882f.png)
    
5. [Open the **Console** drawer](https://developer.chrome.com/docs/devtools/console/reference#drawer). In this example, next to the logpoint's message, the Console shows a link to the original file, not the deployed one.
    
    ![The Console message with a link to the original file.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/the-console-message-a-li-a300a8fc0d067.png)
    
6. Change the [breakpoint type](https://developer.chrome.com/docs/devtools/javascript/breakpoints#overview) to a [regular one](https://developer.chrome.com/docs/devtools/javascript/breakpoints#loc) and run the code again. The execution pauses this time.
    
    ![Execution paused on a regular breakpoint.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/execution-paused-a-regul-95aa0dd1ab5f7.png)
    
    Notice that the **Call Stack** pane shows the name of the original file and not the deployed one.
    
7. In the status bar at the bottom of the **Editor**, click the link to the deployed file. The **Sources** panel takes you to the corresponding file.
    

![The deployed file with the sourceMappingURL comment.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/the-deployed-file-the-so-8e9b29db67d3f.png)

When you open any deployed file, DevTools notifies you if it found the `//# sourceMappingURL` comment and the associated original file.

Notice that the **Editor** automatically pretty-printed the deployed file. In reality, it contains all the code in a single line, except for the `//# sourceMappingURL` comment.

## Name `eval()` calls with `#sourceURL`

The [`#sourceURL`](https://developer.chrome.com/blog/sourcemappingurl-and-sourceurl-syntax-changed#sourceurl) lets you simplify debugging when dealing with `eval()` calls. This helper looks very similar to the [`//# sourceMappingURL` property](https://developer.chrome.com/blog/sourcemaps#how-does-the-source-map-work). For more information, see the [Source Map V3 specification](https://sourcemaps.info/spec.html).

The `//# sourceURL=/path/to/source.file` comment tells the browser to look for the source file when you use `eval()`. This helps you name your evaluations and inline scripts and styles.

Test it on this [demo page](http://www.thecssninja.com/demo/source_mapping/compile.html):

1. [Open the DevTools](https://developer.chrome.com/docs/devtools/open) and go to the **Sources** panel.
2. On the page, enter an arbitrary filename into the _Name your code:_ input field.
3. Click the **Compile** button. An alert appears with the evaluated sum from the CoffeeScript source.
4. In the file tree on the **Page** pane, open a new file with the custom filename you entered. It contains the compiled JavaScript code that has the `// #sourceURL` comment with the original name of the source file.
5. To open the source file, click the link in the status bar of the **Editor**.

![The sourceURL comment and the link to the source file in the status bar.](https://developer.chrome.com/static/docs/devtools/javascript/source-maps/image/the-sourceurl-comment-th-6d3800c1b38cc.png)
## how to do it
1. **Generate Source Maps:**
    
    - If you are using a build tool or bundler (e.g., [Webpack](https://webpack.js.org/guides/getting-started), [Rollup](https://rollupjs.org/introduction/)), ensure that source maps are generated during the build process. Source maps are usually generated alongside the minified JavaScript file.
2. **Configuration in Build Tool:**
    
    - Check your build tool configuration to ensure that it is set up to generate source maps. For example, in Webpack, you might have a configuration like this:
        
```bash
npm install @babel/core @babel/preset-env @babel/cli --save-dev
```
```bash
sudo npx babel [src](./src/assets/index.js) -d [dist](./)
```
        
- Adjust the configuration based on your specific build tool.
        
3. **Upload Source Maps:**
    
    - If you are deploying your application to a service like Vercel, make sure that you are uploading the generated source maps along with your build. Some deployment services allow you to upload source maps, which can be associated with the corresponding JavaScript files.
4. **Check Deployment Logs:**
    
    - Review the deployment logs on Vercel or your hosting provider. They might provide additional information about why the source map is missing or if there were any errors during the deployment process.
5. **Update Build Scripts:**
    
    - Ensure that your build scripts or commands are set up to generate and include source maps. For example, if you are using npm scripts, check the build script in your `package.json` file.
6. **Verify File Paths:**
    
    - Double-check that the file paths in your HTML or application code match the paths of the generated JavaScript and source map files. The paths specified in the source map should be relative to the location where the files are served.