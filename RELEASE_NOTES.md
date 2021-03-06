# ANS Release Notes

### 1.2.1 2016/07/13 ###

* Fixes issue where schemas whose type included a hyphen would never successfully validate (operations)

### 1.2.0 2016/07/13 ###

* Adds 'sync' functionality to fix document composed of multi-version sub-documents

### 1.1.0 2016/07/08 ###

* Adds AnsValidator
* Improves transformer testing
* Fixes minor issues with upverters, tests
* Removes unused fixtures

### 1.0.2 2016/07/06 ###

* Adds gallery operation
* Adds tests for image and gallery operations
* Fixes lots of tests that were not being run properly
* Fixes bug in 0.5.5->0.5.6 upverter that generated invalid reference objects in taxonomy.sites

### 1.0.1 2016/07/01 ###

* ANS Version de-coupled from package version
* Adds library command line for generating new ANS version stubs, cleaning up

### 0.5.6 2016/6/27 ###

* Add corrections to story object, including text and correction_type (to distinguish "clarification" from "correction", etc)
* Adds interstitial_links content element
* Adds reference as a type under related_content, promo_items
* Adds first_publish_date
* Adds source.source_id
* Adds owner.name, owner.sponsored
* Adds syndication.external_distribution, syndication.search
* Adds taxonomy.stock_symbols
* Adds site.primary

### 0.5.5 2016/5/10 ###

* Added 'user_id' and 'published' to revision object
* Added 'slug' to story, video, image, gallery and author objects
* Created schemas for Clavis Topics and Auxiliaries.
* Modified the Keyword schema to match that of the Clavis datatype.
* Score is now a required field in the Keyword schema.

### 0.5.4 2016/4/27 ###

* Moves extraneous properties in planning trait and reference object into additional_properties, enables strict validation

### 0.5.3 2016/4/20 ###

* Removed `sections` from taxonomy and added `sites`. Sites define several fields and validate strictly - previously freeform sections will be upverted to sites as best as possible, stuffing unknown fields into `additional_properties`
* Allows a `reference` to be used in the sites list
* Fixed a bug where schema for `tags` appeared to allow objects but in fact only allowed strings. Tag objects with `_id` and `text` will now validate.
* Made `basic` a required index in the `promo_items` dictionary

### 0.5.2 2016/4/18 ###

* Added `additional_properties` to image.json

### 0.5.1 2016/4/14 ###

* Correct misspelled `additonal_properties` in text, header elements


### 0.5.0 2016/4/13 ###

* camelCase and hypen-ated variable names everywhere converted to under_score
* `author.description` renamed `author.bio`
* (type == "author") required on author objects
* Changed `.default` everywhere to `.basic`
* Story, Video, Image, Audio and Results objects, and others no longer allow unspecified properties outside of `additional_properties`
* Most content_elements do not allow unspecified properties outside of `additional_properties`
* Dropped `"editable": true` from story elements and dropped story_element meta-type
* Separated tests for 0.4.x and 0.5.0
* Separate transformers for 0.4.x and 0.5.x version sequences
* Slight directory re-organization


### 0.4.3 2016/1/29 ###

* Added test coverage

### 0.4.0 2016/1/28 ###

* Added nodejs module backing
* Removed Java POJOs to focus on schema
* Re-factored schema to better distinguish content types, content elements, and summaries

### 0.3.6 2016/1/15 ###

* Added code sample, table, and header content elements
* Made "text" a require field for text objects

### 0.3.5 2015/11/18 ###

* Added a StorySummary object to offer a lower-weight option for Story transmission over the wire
* Made sure Content.getLastUpdatedDateAsInstant and .getCreatedDateAsInstant were null safe if their underlying Strings were null/empty

### 0.3.4 2015/11/23 ###

* Added "channel" attribute to allow for per-channel variation of content elements

### 0.3.3 2015/11/16 ###

* Adding raw_html type
* Adding blockquote and list types
* Making Image.height and Image.widht Integers (instead of ints) so unset JSON values will not result in deserialized "0" values
* Changing lastUpdatedDate and createdDate from java.util.Date to Strings of enforced RFC3339 format
* Added Audio type
* Added Oembed type

### 0.3.2 2015/10/08 ###

* Really fixing bug where the "type" attribute was being deserialized twice. The fix put in the 0.3.1 release technically works, but is incompatible with some other Jackson/Mongo frameworks being used "downstream" of this artifact.
* Renaming Video.type to Video.videoType and VideoStream.type to VideoStream.streamType to avoid ambiguity about what "Video.type" refers to (answer: it should be the ANS type of the Video object)

### 0.3.1 2015/09/25 ###

* Fix bug where the "type" attribute was being deserialized into JSON twice.
* Adding a small ANSVersion enumeration class to standardize on what people should enter in the ANS.version field

### 0.3.0 2015/09/14 ###

* Under development
* Provides a new ANS top-level class/schema to enable Story objects to refer to Lists<ANS> instead of just an HTML String blob
* Implements new types of ANS content like Text, Blockquote, etc
* Sub-classed empty Story and Gallery class from what *used* to be called Story and is now called Collection.
* Added a "version" property at the root-level ANS object to hold the value of the ANS schema the ANS object conforms to
* Removing "title" property in favor of just "headline" which now becomes a tuple of (headline, display) to support multiple headline variants for the same story

#### 0.2.0 2015/08/27 ####

* DEPRECATED / DEVELOPMENT VERSION - do not use this version
* Includes the arc-0.2 specification and corresponding Java classes
