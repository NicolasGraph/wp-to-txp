# WordPress to Textpattern theme

- [WordPress to Textpattern theme](#wordpress-to-textpattern-theme)
  - [Txp theme structure](#txp-theme-structure)
    - [Description](#description)
    - [Default theme filetree](#default-theme-filetree)
  - [Introduction to Txp tags](#introduction-to-txp-tags)
    - [WP vs Txp tags](#wp-vs-txp-tags)
      - [Conditional contents](#conditional-contents)
  - [Tags reference](#tags-reference)
    - [WP functions to Txp tags [a→z]](#wp-functions-to-txp-tags-az)
      - [B](#b)
      - [C](#c)
      - [G](#g)
      - [H](#h)
      - [I](#i)
      - [L](#l)
      - [N](#n)
      - [P](#p)
      - [S](#s)
      - [T](#t)
      - [W](#w)

## Txp theme structure

### Description

Textpattern stores code chunks as _pages_ and _forms_ in its database.
_Forms_ allow to customize the output of some Txp tags (functions) such as [article](https://docs.textpattern.com/tags/article), [comments](https://docs.textpattern.com/tags/comments), [search_input](https://docs.textpattern.com/tags/search_input), etc.; they also provide a way to store other custom templates parts, or overriding forms (post formats). which can be output via the [output_form](https://docs.textpattern.com/tags/output_form) tag.
_Pages_ are used to include _forms_ and/or static contents.

* *template parts* are defined through custom [forms](https://docs.textpattern.com/themes/form-templates-explained)
* *post formats* can be defined via custom article [forms](https://docs.textpattern.com/themes/form-templates-explained) and used as *overidding_forms* in the admin *Write* panel

### Default theme filetree

```
themes
+-- my_theme
|   +-- pages
|   |   +-- archive.txp (Page example)
|   |   +-- default.txp (default page display)
|   |   +-- error_default.txp (default error page display)
|   |   +-- …
|   +-- forms
|   |   +-- article
|   |   |   +-- default.txp (default article display used by the 'article' tag)
|   |   |   +-- article_listing.txp (default article list display used by the 'article' tag)
|   |   |   +-- search_results.txp (default search results display used by the 'search_results' tag)
|   |   |   +-- …
|   |   +-- comment
|   |   |   +-- comment_form.txp (default comment form display used by the 'comments_form' tag)
|   |   |   +-- comments.txp (default comments display used by the 'comments' tag)
|   |   |   +-- comments_display.txp (default comment display used by the 'comment' tag)
|   |   |   +-- popup_comments.txp (default comments popup display)
|   |   |   +-- …
|   |   +-- file
|   |   |   +-- files.txp (default file display used by the 'file_download' tag)
|   |   |   +-- …
|   |   +-- link
|   |   |   +-- plainlinks.txp (default links display used by the 'linklist' tag)
|   |   |   +-- …
|   |   +-- misc
|   |   |   +-- images.txp (not defined as the default form of any tag)
|   |   |   +-- search_input.txp (default search form display used by the 'search_input' tag)
|   |   |   +-- …
|   +-- styles
|   |   +-- default.css (not defined as the default style of any tag)
|   |   +-- …
+-- …
```

## Introduction to Txp tags

### WP vs Txp tags

WordPress templates contain HTML and PHP.  
While Textpattern templates can also contain some PHP code, they are usually mainly composed of HTML and Txp tags.
Textpattern tags are easy to use and make themes really easy to read and modify. You don't even need repeated `<?php ?>` tags to switch between HTML and PHP.

#### Conditional contents

WordPress uses `has_` and `in_` prefixed functions to include conditional contents.

```html
<?php if ( in_category( '3' ) ) : ?>
    <div class="post-cat-three">
<?php else : ?>
    <div class="post">
<?php endif; ?>
```

Textpattern use conditional tags prefixed by `if_`.

```xml
<txp:if_category name="3">
    <div class="post-cat-three">
<txp:else />
    <div class="post">
</txp:if_article>
```

From the introduction of [short-tags](https://docs.textpattern.com/tags/tag-basics/core-short-tags) in Txp v4.7+, you could even make it shorter.  
And in case there is not conditional tag for your need, the recent [`evaluate`](https://docs.textpattern.com/tags/evaluate) tag allows to check any tag output! It also does a lot more…

## Tags reference

### WP functions to Txp tags [a→z]

#### _

* [`__()`](https://developer.wordpress.org/reference/functions/__/) → [`text`](https://docs.textpattern.com/tags/text).
* [`_e()`](https://developer.wordpress.org/reference/functions/_e/) → [`text`](https://docs.textpattern.com/tags/text).

#### B

* [`bloginfo()`](https://developer.wordpress.org/reference/functions/get_bloginfo/) → [`site_name`](https://docs.textpattern.com/tags/site_name), [`site_slogan`](https://docs.textpattern.com/tags/site_slogan), [`site_url`](https://docs.textpattern.com/tags/site_url), [get_pref()](http://phpcrossref.com/xref/textpattern/_functions/get_pref.html).

#### C

* [`comment_author()`](https://developer.wordpress.org/reference/functions/comment_author/) → [`comment_name`](https://docs.textpattern.com/tags/comment_name);
* [`comment_author_email()`](https://developer.wordpress.org/reference/functions/comment_author_email/) → [`comment_email`](https://docs.textpattern.com/tags/comment_email);
* [`comment_date()`](https://developer.wordpress.org/reference/functions/comment_date/) → [`comment_time`](https://docs.textpattern.com/tags/comment_time);
* [`comment_ID()`](https://developer.wordpress.org/reference/functions/comment_ID/) → [`comment_id`](https://docs.textpattern.com/tags/comment_id);
* [`comments_number()`](https://developer.wordpress.org/reference/functions/comments_number/) → [`comments_count`](https://docs.textpattern.com/tags/comments_count);
* [`comments_open()`](https://developer.wordpress.org/reference/functions/comments_open/) → [`if_comments_allowed`](https://docs.textpattern.com/tags/if_comments_allowed);
* [`comment_form()`](https://developer.wordpress.org/reference/functions/comment_form/) → [`comments_form`](https://docs.textpattern.com/tags/comments_form);
* [`comment_text()`](https://developer.wordpress.org/reference/functions/comment_text/) → [`comment_message`](https://docs.textpattern.com/tags/comment_message);
* [`comment_time()`](https://developer.wordpress.org/reference/functions/comment_time/) → [`comment_time`](https://docs.textpattern.com/tags/comment_time);
* [`content_url()`](https://developer.wordpress.org/reference/functions/content_url/) → [`page_url`](https://docs.textpattern.com/tags/page_url).

#### G

* [`get_bookmark()`](https://developer.wordpress.org/reference/functions/get_bookmark/) → [`link`](https://docs.textpattern.com/tags/link);
* [`get_footer()`](https://developer.wordpress.org/reference/functions/get_footer/) (default file: `footer.php`) → [`output_form`](https://docs.textpattern.com/tags/output_form);
* [`get_header()`](https://developer.wordpress.org/reference/functions/get_header/) (default file: `header.php`) → [`output_form`](https://docs.textpattern.com/tags/output_form);
* [`get_search_form()`](https://developer.wordpress.org/reference/functions/get_search_form/) → [`search_input`](https://docs.textpattern.com/tags/search_input) (default form: `search_input`);
* [`get_sidebar()`](https://developer.wordpress.org/reference/functions/get_sidebar/) (default file: `sidebar.php`) → [`output_form`](https://docs.textpattern.com/tags/output_form);
* [`get_template_part()`](https://developer.wordpress.org/reference/functions/get_template_part/) → [`output_form`](https://docs.textpattern.com/tags/output_form).

#### H

* [`has_excerpt()`](https://developer.wordpress.org/reference/functions/has_excerpt/) → [`if_excerpt`](https://docs.textpattern.com/tags/if_excerpt);
* [`has_post_thumbnail()`](https://developer.wordpress.org/reference/functions/has_post_thumbnail/) → [`if_article_image`](https://docs.textpattern.com/tags/if_article_image);
* [`have_posts()`](https://developer.wordpress.org/reference/functions/have_posts/) → [`if_article`](https://docs.textpattern.com/tags/if_article);
* [`have_comments()`](https://developer.wordpress.org/reference/functions/have_comments/) → [`if_comments`](https://docs.textpattern.com/tags/if_comments).

#### I

* [`is_author()`](https://developer.wordpress.org/reference/functions/is_author/) → [`if_author`](https://docs.textpattern.com/tags/if_author);
* [`is_category()`](https://developer.wordpress.org/reference/functions/is_category/) → [`if_category`](https://docs.textpattern.com/tags/if_category);
* [`is_plugin_active()`](https://developer.wordpress.org/reference/functions/is_plugin_active/) → [`if_plugin`](https://docs.textpattern.com/tags/if_plugin);
* [`is_search()`](https://codex.wordpress.org/Function_Reference/is_search) → [`if_search`](https://docs.textpattern.com/tags/if_search);
* [`is_single()`](https://developer.wordpress.org/reference/functions/is_single/) → [`if_article_id`](https://docs.textpattern.com/tags/if_article_id);
* [`is_singular()`](https://codex.wordpress.org/Function_Reference/is_singular) → [`if_individual_article`](https://docs.textpattern.com/tags/if_individual_article).

#### L

* [`language_attributes()`](https://developer.wordpress.org/reference/functions/language_attributes/) → [`lang`](https://docs.textpattern.com/tags/lang).

#### N

* [`next_posts_link()`](https://developer.wordpress.org/reference/functions/next_posts_link/) → [`older`](https://docs.textpattern.com/tags/older).

#### P

* [`previous_posts_link()`](https://developer.wordpress.org/reference/functions/previous_posts_link/) → [`newer`](https://docs.textpattern.com/tags/newer).

#### S

* [`site_url()`](https://developer.wordpress.org/reference/functions/site_url/) → [`site_url`](https://docs.textpattern.com/tags/site_url).

#### T

* [`the_author()`](https://developer.wordpress.org/reference/functions/the_author/) → [`author`](https://docs.textpattern.com/tags/author);
* [`the_author_posts_link()`](https://developer.wordpress.org/reference/functions/the_author_posts_link/) → [`author`](https://docs.textpattern.com/tags/author);
* [`the_content()`](https://developer.wordpress.org/reference/functions/the_content/) → [`body`](https://docs.textpattern.com/tags/body);
* [`the_excerpt()`](https://developer.wordpress.org/reference/functions/the_excerpt/) → [`excerpt`](https://docs.textpattern.com/tags/excerpt);
* [`the_feed_link()`](https://codex.wordpress.org/Function_Reference/the_feed_link) → [`feed_link`](https://docs.textpattern.com/tags/feed_link);
* [`the_id()`](https://codex.wordpress.org/Function_Reference/the_ID) → [`article_id`](https://docs.textpattern.com/tags/article_id);
* [`the_loop()`](https://developer.wordpress.org/reference/functions/the_loop/) → [`article`](https://docs.textpattern.com/tags/article);
* [`the_modified_time()`](https://developer.wordpress.org/reference/functions/the_modified_time/) → [`modified`](https://docs.textpattern.com/tags/modified);
* [`the_permalink()`](https://developer.wordpress.org/reference/functions/the_permalink/) → [`permlink`](https://docs.textpattern.com/tags/permlink);
* [`the_post()`](https://developer.wordpress.org/reference/functions/the_post/) → [`article`](https://docs.textpattern.com/tags/article) (default form: `default`, listform: `article_listing`);
* [`the_post_thumbnail()`](https://developer.wordpress.org/reference/functions/the_post_thumbnail/) → [`article_image`](https://docs.textpattern.com/tags/article_image);
* [`the_search_query()`](https://developer.wordpress.org/reference/functions/the_search_query/) → [`search_term`](https://docs.textpattern.com/tags/search_term);
* [`the_title()`](https://developer.wordpress.org/reference/functions/the_title/) → [`title`](https://docs.textpattern.com/tags/title);
* [`the_time()`](https://developer.wordpress.org/reference/functions/the_time/) → [`posted`](https://docs.textpattern.com/tags/posted).

#### W

* [`wp_get_attachment_image()`](https://developer.wordpress.org/reference/functions/wp_get_attachment_image/) → [`article_image`](https://docs.textpattern.com/tags/article_image);
* [`wp_list_authors()`](https://developer.wordpress.org/reference/functions/wp_list_authors/) → [`authors`](https://docs.textpattern.com/tags/authors);
* [`wp_list_bookmarks()`](https://developer.wordpress.org/reference/functions/wp_list_bookmarks/) → [`linklist`](https://docs.textpattern.com/tags/linklist) (default form: `plainlinks`);
* [`wp_list_categories()`](https://developer.wordpress.org/reference/functions/wp_list_categories/) → [`category_list`](https://docs.textpattern.com/tags/category_list);
* [`wp_list_comments()`](https://codex.wordpress.org/Function_Reference/wp_list_comments) → [`comments`](https://docs.textpattern.com/tags/comments) (default form: `comments`).
