# Presentation template

Uses the training department's fork of the Reveal.js slide engine.

## File arrangement

In Training, we have a course level TOC slide, then individual folders/files for each of the lessons that make up the course. If you have similar structure, your file structure will look roughly like this:

```
   - your_presentation (folder)  
      - index.html  <-- agenda for the whole presentation, update this one
      - presenternotes.html (script/template file, no need to touch)  
      - presentation-engine (folder, contains CSS/JS of Reveal engine)  
      - css (folder, contains CSS for main TOC index file)  
      - images (folder, contains images for main TOC index file)  
      - i18n (folder, contains internationalization JS files for main TOC index file)  
      - subtopic (folder)  
         - index.html <-- Main file for a section of your presentation, update this one 
         - presenternotes.html (script/template file, no need to touch)  
         - css (folder, contains CSS for this folder's index file)  
         - images (folder, contains images for this folder's index file)  
         - i18n (folder, contains internationalization JS files for this folder's index file)  
      ... etc
```

## Instrutions

1. Update the main index.html with your agenda, include links to each of the subfolder index.html files
2. Copy the subtopic folder as needed, update its index.html with the contents of your presentation
3. Add presenter notes into the HTML: <div class="slidenote"><div class="l_slidenote_classname">YOUR PRESENTER NOTES GO HERE</div></div>
4. (Optional) internationalize by setting a unique classname on each tag in your HTML, adding those same classes to the i18n/localizations.js file, and updating the strings there. See below.
5. Rinse and repeat

The biggest challenge for adding slides and content is getting the HTML structure correct. 

- Slides are enclosed by <section> tags
- Pretty much any HTML content can follow the opening <section> tag to have it show up on the slide
- Your content must come before the <div class="slidenote"><div class="l_slidenote_classname">YOUR PRESENTER NOTES GO HERE</div></div> tags, which as indicated are where you put the text/html of your presenter notes

A TextMate bundle is included to ease the addition of the necessary HTML in the index files. See below.

### TextMate Bundle

I've included a TextMate bundle with convenient tab-shortcuts for adding elements to the HTML files. For example, 

- type 'slide' and press Tab and the HTML needed for a new slide is inserted. 
- type 'topic' and press Tab and the HTML for a topic/title slide is inserted
- type 'ul' or 'ol' and press Tab for an unordered/ordered list
- type 'para' for a paragraph
- type 'code' for a code block
- type 'table' for a table
- type 'img' for an <img> tag

There are others, check out the bundle using TextMate's bundle editor window.

If you have TextMate installed, simply double-click the bundle file to install it. You can install it to Titanium Studio by following the steps here: http://docs.appcelerator.com/titanium/latest/#!/guide/Converting_a_Textmate_Bundle

# Running a presentation

Open the main index.html file and navigate as needed.

Press right or left arrow keys to move forward/back in a presentation. 

Press the Spacebar to see a partial overview of the slides in a presentation.

Click the house icon to return to the course table of contents slide.

Click the blue arrow icon to return to the first slide in the current lesson

Click the Note icon to open the presenter's notes window. As you move forward/back through the slides, any notes will be shown in that window.

# Translations

Slide content is provided as HTML pages, in which the actual text is read in at display time from a JavaScript strings file. Which strings are read in are based on the *browser's language setting.* Which text is replaced and where is based on the HTML element's ID and must begin with "%l\_" (e.g. &lt;div id="l_foo" would have a corresponding %l\_foo string in the localizations.js file). This makes translating mostly a process of updating that strings file. 

The strings files follow this format: 

```
String.toLocaleString({ 
  "en-US": { 
    "%l_coursename": "Building Native Mobile Apps with Titanium", 
    "%l_agenda_title": "AGENDA" 
  }, 
  "ja": { 
    "%l_coursename": "Appcelerator Titaniumによるネイティブアプリ開発", 
    "%l_agenda1_title": "アジェンダ1" 
  } 
}); 
```

Each of the l_foo attributes correspond to a unique class assigned within the HTML of your page. Any text set as the value here will replace the text you put inside the corresponding HTML tag in the index.html file. If no class is found in the localizations file, the text in your HTML file will be used.

To provide a new translation/language, you would copy the entire "en-US" node giving it the _two-letter ISO 639 language code_ for the target language (or the occasional 4-letter exceptions, such as en-US). Then, you'd translate each string. 

### Language-specific stylesheets 

In some cases, such as Asian languages, you will need to supply CSS overrides for existing styles. You might need to use custom fonts (such as Japanese scripts), adjust text sizes or RTL/LTR layout options, etc. See the css/presentation.css file for the primary list of styles used in the HTML files. You can then override any by adding a css/2letterCode.css file (such as css/ja.css). This file will be automatically read-in at display time, if present.

If you want to supply a custom font, either link to an online repository (such as Google Fonts) or make sure that the font's licensing permits redistribution and its licensing is compatible with that of our slides. 

# License

Unless otherwise stated, the slides and contents of this repository are licensed under the [Attribution-NonCommercial-ShareAlike 3.0 Unported (CC BY-NC-SA 3.0)](http://creativecommons.org/licenses/by-nc-sa/3.0/) license. You are free to use, copy, distribute, and adapt these materials under these terms:

* You cannot use these slides or derivatives for commercial purposes (e.g. classes you charge for). Commercial use is restricted to Authorized Training Partners (ATPs). Visit [http://www.appcelerator.com/form/forms/www/partner-training-submit](http://www.appcelerator.com/form/forms/www/partner-training-submit) for information on becoming an ATP.
* You must attribute Appcelerator, Inc. in any use or derivative of these materials.
* If you distribute these materials, you must do so under the same license.

These slides use [Crystal Clear](http://commons.wikimedia.org/wiki/Crystal_Clear) icons, which are licensed under the [LGPL](http://www.everaldo.com/crystal/?action=license) license.
