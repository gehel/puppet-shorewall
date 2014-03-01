# Puppet module: shorewall

This is a Puppet module for shorewall
It provides only package installation and file configuration.

Based on Example42 layouts by Alessandro Franceschi / Lab42

Official site: http://www.example42.com

Official git repository: http://github.com/example42/puppet-shorewall

Released under the terms of Apache 2 License.

This module requires the presence of Example42 Puppi module in your modulepath.


## USAGE - Basic management

* Install shorewall with default settings

        class { 'shorewall': }

* Install a specific version of shorewall package

        class { 'shorewall':
          version => '1.0.1',
        }

* Remove shorewall resources

        class { 'shorewall':
          absent => true
        }

* Enable auditing without without making changes on existing shorewall configuration *files*

        class { 'shorewall':
          audit_only => true
        }

* Module dry-run: Do not make any change on *all* the resources provided by the module

        class { 'shorewall':
          noops => true
        }


## USAGE - Overrides and Customizations
* Use custom sources for main config file 

        class { 'shorewall':
          source => [ "puppet:///modules/example42/shorewall/shorewall.conf-${hostname}" , "puppet:///modules/example42/shorewall/shorewall.conf" ], 
        }


* Use custom source directory for the whole configuration dir

        class { 'shorewall':
          source_dir       => 'puppet:///modules/example42/shorewall/conf/',
          source_dir_purge => false, # Set to true to purge any existing file not present in $source_dir
        }

* Use custom template for main config file. Note that template and source arguments are alternative. 

        class { 'shorewall':
          template => 'example42/shorewall/shorewall.conf.erb',
        }

* Automatically include a custom subclass

        class { 'shorewall':
          my_class => 'example42::my_shorewall',
        }



## TESTING
[![Build Status](https://travis-ci.org/example42/puppet-shorewall.png?branch=master)](https://travis-ci.org/example42/puppet-shorewall)
