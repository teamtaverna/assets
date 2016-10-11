# Assets
Repository for all our docs, brand, design and development assets


### General workflow
* Pick a card on the `To Do` list on the [Trello board](https://trello.com)
* Add yourself as a member and move it to `In Progress` list
* Every Github issue has a corresponding Trello card with said issue's link. However, if there is no issue link, create a Github issue and add the link to as part of the description on the Trello card.
* Assign yourself to the issue on Github.
* Checkout to a new branch from staging using the issue number and a summary of the issue as the branch name. For example, `45__create_admin_page`.
* We encourage atomic commits on feature branches.
* Commit message should be in [imperative present tense](https://git-scm.com/book/ch5-2.html). In other words, use commands. `Instead of "I added tests for" or "Adding tests for," use "Add tests for."`
* Ensure that the code is test driven.
* Rebase continually with staging while working since that is the base branch for initial PR.
* `For python/django projects`, Run flake 8 checks on your code using this command ` flake8 .` before pushing. Remember the dot after flake8 in the command.
* Create a pull request to staging for review and move the Trello card to `Code review`.
* Type a title and description for your pull request referencing the issue number alongside.
* Ask two people to review your code by mentioning them on the GitHub issue/pull request.
* The two reviewers must approve your code and all tests must pass before it can be merged to staging.
* When the reviewers approve, merge to staging and move the Trello card to `QA`.
* Notify any of the project managers on Trello or whoever created the card as well as any of the code reviewers to check out the application on [staging](https://taverna-core-staging.herokuapp.com/) to ensure that the issue given was resolved. At least one code reviewer and one project manager or the person that created the card need to approve the card for the issue to be deployed to production. Their approval means moving the card to `Ready to deploy`. If they do not approve, it means the issue failed QA. Revert your PR merge following instructions [here](https://help.github.com/articles/reverting-a-pull-request/) so that others can rebase from staging without pulling your issue. If a database migration was done, call on someone with admin privilege on the Heroku instance of staging branch to roll back the migration to a consistent state with the reverted staging branch by doing just step 1 stated [here for Django projects](https://github.com/teamtaverna/core/wiki/Dealing-with-Migrations). Note: `heroku run -a <name-of-staging-app-instance-on-heroku>` should be prepended to the command.
* Create a pull request from staging to master branch.
* Type a title and description for your pull request referencing the issue number alongside.
* Ensure all tests pass and ask one of the code reviewers who approved the card for production to merge to master.
* Check that the application works well on production.
* Move the Trello card `Done`.
* Delete branch, close pull request and close issue.
