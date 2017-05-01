# Localizing UGS

We are currently using [POEditor](https://poeditor.com/join/project/2J2hB5I41Z) to manage localization.
If you would like to help please consider signing up to contribute through this service.

To join the project sign up here: [https://poeditor.com/join/project/2J2hB5I41Z](https://poeditor.com/join/project/2J2hB5I41Z)

# Adding a new language

You can add a new language from POEditor and start translating.

If you want to stop here, create a ticket on GitHub and I'll add your work to the project. To finish the job completely you'll need to know how to use [git](https://git-scm.com).

* Add a new file to `ugs-core/src/resources`.
* Open `src/com/willwinder/universalgcodesender/i18n/AvailableLanguages.java`
* Add your new translation to the `availableLanguages` object.
* [Create a GitHub pull request](https://help.github.com/articles/using-pull-requests/).

Finally I will link POEditor to the new file and future localization can be handled from there.
