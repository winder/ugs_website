# Translations

Translations are greatly appreciated.

## Classic GUI

The Classic GUI is localized with properties files found in `src/resources`.

* Start with `MessagesBundle.properties`
* Rename to `MessagesBundle_<locale>.properties`
* Translate the file.

If you want to stop here, create a pull request and provide this file. I'm more
than happy to do the last steps.

To finish the job completely you'll need to know how to use [git](https://git-scm.com).

* Add your 
* Edit `src/com/willwinder/universalgcodesender/i18n/AvailableLanguages.java`
* Add your new translation to the `availableLanguages` object.
* [Create a pull request](https://help.github.com/articles/using-pull-requests/).

## UGS Platform

NetBeans platform provides facilities for localization, but they have not been
explored yet. If you're interesting in exploring this, [here is the
documentation][nbp_doc], create an issue on github with anything you find out!

[nbp_doc]: http://bits.netbeans.org/dev/javadoc/org-openide-modules/org/openide/modules/doc-files/i18n-branding.html 
