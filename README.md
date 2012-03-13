# Realtime Thermometer

Originally developed for the GiveCamp UK event. You can see the a blog post write-up detailing how to create the thermometer step-by-step here:
<http://blog.pusher.com/2011/10/20/a-realtime-charity-thermometer-for-givecamp-uk>

## Contents

* `/example`
  * An example widget taken from the original blog post. Contains client and server code.
* `src`
  * JavaScript and CSS for the thermometer.
  
## Getting Started

1. Renaming `example/config.example.php` to `example/config.php` and update the credentials
2. Update the application key which is passed into the `Pusher` constructor in `example/index.html`
3. Update the URL for the initial value AJAX call in `example/index.html`
4. A database also needs to be in place to persist the widget values. The structure of the table used by `example/current_total.php` is

        CREATE TABLE IF NOT EXISTS `givecampuk` (
          `id` int(11) NOT NULL auto_increment,
          `who` varchar(200) NOT NULL,
          `how_much` decimal(10,2) NOT NULL,
          `when` timestamp NOT NULL default CURRENT_TIMESTAMP,
          `running_total` decimal(10,2) NOT NULL,
          PRIMARY KEY  (`id`)
        ) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=9537 ;
        
**Note: `example/current_total.php` is not production ready. It was only provided as an example and is not production ready.
  
## Improvements

* **Configuration &amp; setup complexity**
    The initial configuration and set up is too complicated. It should be possible to provide some default values and remove the need to call the the initial set up function `addBehaviours`. Through encapsulation of the function within an object it would be possible to vastly improve setup and access to the widget/library.
* **Namespace**
    It would be nice to namespace the functions in `src/realtime-thermometer.js` so that they're not all global functions and variable.