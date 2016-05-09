# Localizing UGS

We are currently using [POEditor](https://poeditor.com/join/project/2J2hB5I41Z) to manage localization.
If you would like to help please consider signing up to contribute through this service.

To request access to the project sign up here: [https://poeditor.com/join/project/2J2hB5I41Z](https://poeditor.com/join/project/2J2hB5I41Z)

| Language | Maintainers |
| -------- | ----------- |
| Afrikaans | Maintainer needed! |
| Dutch | Maintainer needed! |
| German | Maintainer needed! |
| Italian | Maintainer needed! |
| Spanish | Maintainer needed! |
| French | Maintainer needed! |

# Adding a new language

Localization property files are found in `ugs-core/src/resources`.

* Start with `MessagesBundle.properties`
* Rename to `MessagesBundle_<locale>.properties`
* Translate the file.

If you want to stop here, create a pull request and provide this file. I'm more
than happy to do the last steps.

To finish the job completely you'll need to know how to use [git](https://git-scm.com).

* Add your new file to `ugs-core/src/resources`.
* Open `src/com/willwinder/universalgcodesender/i18n/AvailableLanguages.java`
* Add your new translation to the `availableLanguages` object.
* [Create a GitHub pull request](https://help.github.com/articles/using-pull-requests/).
