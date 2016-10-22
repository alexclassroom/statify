# Statify #
* Contributors:      pluginkollektiv
* Donate link:       https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=LG5VC9KXMAYXJ
* Tags:              stats, analytics, privacy, dashboard
* Requires at least: 3.9
* Tested up to:      4.6.1
* Stable tag:        1.4.3
* License:           GPLv3 or later
* License URI:       https://www.gnu.org/licenses/gpl-3.0.html

Visitor statistics for WordPress with focus on data protection, transparency and clarity. Perfect as a widget in your WordPress Dashboard.

## Description ##
The free and ad-free plugin Statify pursues a simple objective: to provide a straightforward and compact access to the number of site views.

No frills. No Cookies. No third party. No storage of personal data. No endless data privacy statements.

An interactive chart is followed by lists of the most common reference sources and target pages. The period of statistics and length of lists can be set directly in the dashboard widget.

### Data Privacy ###
In direct comparison to statistics services such as *Google Analytics*, *WordPress.com Stats* and *Piwik* *Statify* doesn't process and store personal data as e.g. IP addresses – *Statify* counts site views, not visitors.
Absolute privacy compliance coupled with transparent procedures: A locally in WordPress created database table consists of only 4 fields (ID, date, source, target) and can be viewed at any time, cleaned up and cleared by the administrator.

### Settings and Hooks ###
The plugin configuration can be changed directly in the *Statify* Widget on the dashboard by clicking the *Configure* link.

#### Period of data saving
*Statify* stores the data only for a limited period (default: 2 weeks), longer intervals can be selected as option in the widget. Data which is older than the period set is deleted by a daily cron job.

#### Display of the widget
The amount of links shown in the *Statify* Widget can be set as well as the option to only count views from today. Of course, older entries are not deleted when changing this setting.

The statistics for the dashboard widget are cached for four minutes.

Per default only administrators can see the widget. This can be changed with the `statify__user_can_see_stats` hook.

Example:

```
add_filter(
    'statify__user_can_see_stats',
    '__return_true'
);
```

has to be your theme's `functions.php` and adapted to your needs. This example would allow all users to see the widget.

Editing the configuration is still limited to users with `edit_dashboard` capability.

#### JavaScript tracking for caching compatibility
For compatibility with caching plugins like [Cachify](http://cachify.de) *Statify* offers an optional switchable tracking via JavaScript. This function allows reliable count of cached blog pages.

For this to work correctly, the active theme has to call `wp_footer()`.

#### Skip tracking for defined users or pages
The conditions for tracking views can be customized according to page type and user capabilities by using the hook `statify_skip_tracking`.

Example:

```
add_filter(
    'statify_skip_tracking',
    function() {
        if ( condition ) {
            return true;
        }

        return false;
    }
);
```

has to be added to the theme's `functions.php`. The condition has modified such that the method returns true if and only if the view should be ignored.


### Memory Usage ###
* Backend: ~ 0.2 MB
* Frontend: ~ 0.1 MB

### Credits ###
* Author: [Sergej Müller](https://sergejmueller.github.io/)
* Maintainers: [pluginkollektiv](http://pluginkollektiv.org/)
* Contributor: [Bego Mario Garde](https://garde-medienberatung.de)

## Installation ##
* If you don’t know how to install a plugin for WordPress, [here’s how](https://codex.wordpress.org/Managing_Plugins#Installing_Plugins).

### Requirements ###
* PHP 5.2.4
* WordPress 3.9


## Frequently Asked Questions

### Which views are not tracked?
*Statify* does not count the following views:

* feeds
* trackbacks
* searches
* previews
* views by logged in users
* error pages

This behavior can be modified with the `statify_skip_tracking` hook.

## Can you add browser or screen size tracking?
*Statify* only tracks page views, not visitors. Therefore this feature will not be added.


## Changelog ##

### 1.4.3 / 2016-08-15 ###
* Corrected tracking and display in Multisite
* Minor CSS fixes in the dashboard widget
* Removed deprecated links and updated URLs for donate and wiki links
* Administrative updates to plugin header and README
* Updated [plugin authors](https://gist.github.com/glueckpress/f058c0ab973d45a72720)

### 1.4.2 / 01.05.2015 ###
* Replace `filter_has_var(INPUT_SERVER)` calls with `isset($_SERVER[])` ([why](https://github.com/wp-stream/stream/issues/254))

### 1.4.1 / 29.04.2015 ###
* Renew the tracking mechanism

### 1.4.0 / 16.04.2015 ###
* WordPress 4.2 support
* Plugin-wide code refactoring
* Translations for English and Russian
* [GitHub Repository](https://github.com/pluginkollektiv/statify)

### 1.3.0 / 28.04.2014 ###
* Sourcecode optimization for plugin-finalization

For the complete changelog, check out our [GitHub repository](https://github.com/pluginkollektiv/statify).

## Upgrade Notice ##

### 1.4.3 ###

This is mainly a maintenance release ensuring compatibility with the latest version of WordPress. Works well with Multisite too!

## Screenshots ##
1. Statify dashboard widget
2. Statify dashboard widget options
