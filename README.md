SilverStripe HasOneAutocompleteField
===================================

Overview
--------------

This module adds a field for using an autocomplete dropdown to assign a has_one relationship. It's styled after the
URLSegment field.

FORK CHANGES: Added support for functions as result list title ( fields are accessible as get{FieldName} functions just
with the function name )


Maintainer Contacts
-------------------

* Nathan Cox (<nathan@flyingmonkey.co.nz>)
* Primoz Skerbis (<primoz2500@gmail.com>)

Requirements
------------

* SilverStripe 5.0+

Installation Instructions
-------------------------

Via composer:

```
composer require primoz2500/hasoneautocompletefield
```

Or manually download the module and place it in a folder called hasoneautocompletefield in your site root.

Visit yoursite.com/dev/build?flush=1

Documentation
-------------


Example code:

```php
<?php

use SilverStripe\CMS\Model\SiteTree;
use NathanCox\HasOneAutocompleteField\Forms\HasOneAutocompleteField;

class Page extends SiteTree
{
    private static $db = [];

    private static $has_one = [
        'LinkedPage' => 'Page'
    ];

    public function getCMSFields()
    {
        $fields = parent::getCMSFields();

        $fields->addFieldToTab('Root.Content', $pageField = HasOneAutocompleteField::create('LinkedPageID', 'Linked Page', 'Page', 'Title'));
        $pageField->setSearchFields(array('Title', 'Content'));
        $pageField->enableClearButton();

        return $fields;
    }
}

```

Known Issues
------------
[Issue Tracker](https://github.com/primoz2500/silverstripe-hasoneautocompletefield/issues)
