# Localizing UGS

We are currently using [POEditor](https://poeditor.com/join/project/2J2hB5I41Z) to manage localization.
If you would like to help please consider signing up to contribute through this service.

To join the project sign up here: [https://poeditor.com/join/project/2J2hB5I41Z](https://poeditor.com/join/project/2J2hB5I41Z)

# Adding a new language

You can add a new language from POEditor and start translating.

If you want to stop here, create a ticket on GitHub and someone will update the project. To finish the job completely you'll need to know how to use [git](https://git-scm.com).

* Create an empty property file for your language in `ugs-core/src/resources`.
* Open `src/com/willwinder/universalgcodesender/i18n/AvailableLanguages.java`
* Add your new translation to the `availableLanguages` object.
* Update the file in `update_languages.py` with a mapping between the POEditor key and your new file.
* Run `update_languages.py`, see README in scripts directory for configuration detail. Only commit the new file even if others were updated.
* [Create a GitHub pull request](https://help.github.com/articles/using-pull-requests/).

Future language syncs will be done periodically with the `update_languages.py` script.
