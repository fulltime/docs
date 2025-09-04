# Changelog

### 2.3.0

* Major code quality improvements and PSR-4 standard compliance updates
* Enhanced import statements organization and consistency across all PHP files
* Improved code formatting and structure in administration modules and components
* Optimized JavaScript and SCSS files for better performance and maintainability
* Updated API route implementations with improved error handling
* Enhanced entity definitions and collections with better type safety
* Improved migration files structure and database handling
* Updated CMS elements configuration and preview components
* Enhanced storefront JavaScript plugin functionality
* Improved SEO URL routing implementations
* Better template organization and twig block structure
* Enhanced multi-language support and translation snippets
* Optimized controller logic and response handling
* Improved administration UI components and forms
* Updated build assets and compiled resources

### 2.2.2

* Enhanced plugin descriptions for better store compliance
* Fixed missing translation keys in administration snippets
* Improved store validation compatibility
* Updated plugin metadata for Shopware Store requirements

### 2.2.1

* Fixed FAQ page visibility database structure and constraints
* Resolved duplicate entries in faq\_page\_visibility table
* Improved unique constraint handling for FAQ page visibility
* Enhanced database migration stability
* Fixed visibility entity structure to align with Shopware standards

### 2.2.0

* Implemented comprehensive view tracking system for FAQ items
* Added dual tracking approach: server-side for direct page access and client-side for accordion interactions
* Enhanced FAQ templates with proper data attributes for view tracking
* Added default values for position (1) and views (0) fields in all entities
* Improved FAQ list displays with user-friendly messages for empty states
* Enhanced visibility selector with proper label integration
* Fixed type errors in FaqListEntity setViews method
* Updated CMS elements with view tracking capabilities
* Optimized JavaScript plugin for better performance and error handling
* Added server-side view increment method with proper error handling

### 2.1.0

* Updated plugin to Shopware 6.7 compatibility
* Improved README.md with comprehensive documentation
* Enhanced plugin structure and organization
* Added detailed feature overview and installation guide
* Improved CMS integration documentation
* Added developer information and API documentation
* Enhanced SEO features documentation
* Updated support and community links

### 2.0.0

* Major version update for Shopware 6.7
* Enhanced administration interface
* Improved frontend performance
* Better SEO optimization
* Extended CMS integration capabilities
* Customizations for Shopware 6.7

### 1.8.4

* response data for faq categories (store-api) optimized

### 1.8.3

* service categories repository added

### 1.8.2

* store-aip endpoint for FAQ categories added

### 1.8.1

* CMS element for FAQ categories and entries customized
* store-api endpoint added

### 1.8.0

* Adds category selection with page association in faq items
* Makes cms category/item selection optional

### 1.7.2

* Removes unused language property

### 1.7.1

* Indexer for Categories, Items and Pages fixed

### 1.7.0

* Added new twig block
* Added initial state for accordion

### 1.6.1

* Search field has been adjusted

### 1.6.0

* Added a new shopping experience element for FAQ categories

### 1.5.5

* Warnings of the static code analysis fixed

### 1.5.4

* Fixed CMS element

### 1.5.3

* Remove association\_fields field

### 1.5.2

* Fix storefront js

### 1.5.1

* Changes for Shopware 6.6

### 1.5.0

* Fixed collapse item on search page
* Added indexing settings
* Added option to insert faqs to the sitemap

### 1.4.0

* Add title type to page, category and entry

### 1.3.0

* App updated and refactored with Rector for Shopware 6.5 (https://github.com/FriendsOfShopware/shopware-rector/)

## 1.2.3

* Fix sorting of categories and entries
* Fix search url parameter

## 1.2.2

* In template 1 and template 2, the heading for categories has been adjusted from h2 to h1

## 1.2.1

* Corrected search form setting

## 1.2.0

* Integration to Shopping Experiences

## 1.1.3

* Fixes for sales channels

## 1.1.2

* Define maximum number of characters for meta title/description and SEO keywords
* Load images into their own folder
* Corrected sorting by categories within the entries
* Corrected sorting by pages within the categories
* Check translation within entries (category)
* Check translation within categories (page)

## 1.1.1

* Fix meta data
* Change search url

## 1.1.0

* Fix mapping bug

## 1.0.9

* Fix mobil bug with long text in Questions #32

## 1.0.8

* Compatibility to Shopware 6.4.7.x established

## 1.0.7

* Change access to global Shopware object (SW-6.4.5.0)

## 1.0.6

* Correction of the installation routine (migration)
* Integrated search function
* Twig blocks have been added

## 1.0.5

* Compatibility to Shopware 6.4 established
* Plugin-Setting: Show author
* Plugin-Setting: Date formats
* Plugin-Setting: Show direct links to categories and questions

## 1.0.4

* HTML-Interpretation für Seiten-Beschreibung
* FAQ Seiten Einstellung: Erste Frage aufgeklappt
* Kompatibilität mit Shopware 6.3 hergestellt

## 1.0.3

* Add media to faq items
* Compatibility to Shopware 6.3 established

## 1.0.2

* Compatibility to Shopware 6.2 established
* Deprecated mapApiErrors, use mapPropertyErrors
* https://github.com/shopware/platform/blob/v6.2.0/UPGRADE-6.2.md#seo-urls

## 1.0.1

* Add column default for active in list
* Bugfix: FAQ pages, categories and questions removed from httpCache

## 1.0.0

* New shopware 6 plugin
