# cms2cmd
Occasionally during a CTF (or a pen test?) you might gain admin access to a CMS. In most configurations that gives you RCE. **cms2cmd** is a clean (i.e. no need to change templates or otherwise "break" the CMS instance) and simple command execution plugin that works for a number of various CMS systems (current version has been tested on Drupal 7, Drupal 8, Joomla 3.x, and Wordpress 3.9.x).

The same **mod_cmd.zip** file is recognized as a valid plugin by all the supported CMS systems. mod_cmd.zip is just a ZIP archive containing mod_cmd directory, you can create it yourself - see **build.sh**. **cms2cmd** will send a 404 HTTP response if called without providing a command to execute, which makes it *a bit* sneakier and safer in CTF type environment.

# Usage
## Drupal 7
### Installation
* Login as CMS administrator.
* Select Modules in the menu.
* Select "Install new module". If this option is not available, enable "Update manager" module and refresh.
* Upload **mod_cmd.zip**
* Go back to module list and enable **cms2cmd** module.

### Usage
Test with: http(s)://<YOUR_DRUPAL_BASE_URI>/?q=mod_cmd&cmd=id

Replace **id** with the command you'd like to execute. Note: if command is not provided, the module will return a 404 HTTP response.

## Drupal 8
### Installation
* Login as CMS administrator.
* Select Extend in the menu.
* Select "Install new module". If this option is not available, enable "Update Manager" module and refresh.
* Upload **mod_cmd.zip**
* Go back to module list, find **cms2cmd** and "install" it - this enables the module.

### Usage
Test with: http(s)://<YOUR_DRUPAL_BASE_URI>/mod_cmd?cmd=id

Replace **id** with the command you'd like to execute. Note: if command is not provided, the module will return a 404 HTTP response.

## Joomla
### Installation
* Login as CMS administrator.
* Select Extensions -> Manage -> Install in the menu.
* Upload **mod_cms.zip**

### Usage
Test with: http(s)://<YOUR_JOOMLA_BASE_URI>/modules/mod_cmd/mod_cmd.php?cmd=id

Replace **id** with the command you'd like to execute. Note: if command is not provided, the module will return a 404 HTTP response.

## Wordpress
### Installation
* Login as CMS administrator.
* Select Plugins from the menu.
* Select Add New, then Upload Plugin.
* Upload and activate **mod_cmd.zip**

### Usage
Test with: http(s)://<YOUR_BASE_WORDPRESS_URI>/wp-content/plugins/mod_cmd/mod_cmd.php?cmd=id

Replace **id** with the command you'd like to execute. Note: if command is not provided, the module will return a 404 HTTP response.
