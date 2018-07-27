# Contributing
 
If you are interested in contributing to make UGS even more awesome, there are 
many places you can pitch in.

Browse through the already reported [issues][github_issues_link] or check out the [discussion forum][discussion_forum_link]. 
You might know how to code, have ideas on how to improve the documentation or want to 
translate the software to your language?


## Code

Pull requests are welcome! Is there a feature you would like to see, or a bug
thats been bothering you? Feel free to dig in. Not sure where to start? Ask on
github, use an existing ticket or create a new one.

If you're planning to make a lot of changes please create an issue to discuss
implementation details. A lot of effort has gone into the current design so we
want to make sure everything will to work together.


## Documentation

If you find any errors in the documentation or if there are missing pages, you are welcome to contribute! 
It is written using [MkDocs](http://www.mkdocs.org/user-guide/writing-your-docs/) and [Markdown](https://guides.github.com/features/mastering-markdown/). Follow these instructions to get started:

* [Fork and clone](https://help.github.com/articles/committing-changes-to-a-pull-request-branch-created-from-a-fork/) the repository [https://github.com/winder/ugs_website](https://github.com/winder/ugs_website).
* Make sure you have [Python](https://www.python.org/downloads/) installed with this command in your terminal:

        python --version
        
* Install MkDocs and the theme modules 

        sudo pip install mkdocs
        sudo pip install mkdocs-bootswatch

* From your cloned ugs_website directory run 

        mkdocs serve
        
* Go to [http://localhost:8000/](http://localhost:8000/) in your browser

Now, make your changes and see them live updating in your web browser. Create a [pull request](https://help.github.com/articles/using-pull-requests/) in github and we will review and add your changes.


## Translations

We are currently using [POEditor](https://poeditor.com/join/project/2J2hB5I41Z) to manage localization.
If you would like to help please consider signing up to contribute through this service.

To join the project sign up here: [https://poeditor.com/join/project/2J2hB5I41Z](https://poeditor.com/join/project/2J2hB5I41Z)

### Adding a new language

You can add a new language from POEditor and start translating.

If you want to stop here, create a ticket on GitHub and someone will update the project. To finish the job completely you'll need to know how to use [git](https://git-scm.com).

* Create an empty property file for your language in `ugs-core/src/resources`.
* Open `src/com/willwinder/universalgcodesender/i18n/AvailableLanguages.java`
* Add your new translation to the `availableLanguages` object.
* Update the file in `update_languages.py` with a mapping between the POEditor key and your new file.
* Run `update_languages.py`, see README in scripts directory for configuration detail. Only commit the new file even if others were updated.
* [Create a GitHub pull request](https://help.github.com/articles/using-pull-requests/).

Future language syncs will be done periodically with the `update_languages.py` script.

[github_issues_link]: https://github.com/winder/Universal-G-Code-Sender
[discussion_forum_link]: https://groups.google.com/forum/#!forum/universal-gcode-sender
