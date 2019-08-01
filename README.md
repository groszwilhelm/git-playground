## Playing arround with GIT :D 

### Setup 
- git clone https://github.com/groszwilhelm/git-playground.git
- cd git-playground

### Helpers
  If you don't use sourcetree add the following alias to ~/.gitconfig (I have no idea where it is on Windows 😋)
  [alias]
  lg = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all

## Info

- We'll be using **develop** branch in order to merge all feature branches into it (will deploy automatically to DEV and QA).
- We'll be using **master** branch in order to create production releases, all features that need to be released will be merged in the master branch as well. Master will automatically deploy to STAGE -> After it has been tested we deploy it to PROD.

## Proposal
- All the changes affecting the **develop** and **master** branches should be done through a **feature** branch, so that we can merge them easily in both places. **So don't delete the feature branches** (only after they were merged to master 😁).
- **develop** and **master** branches should be decoupled in the sense that we won't directly merge one into the other.
- In order to keep the master branch clean we should merge the feature branch into it using squash. This will help us also for the changelog (maybe use bisnode components commit structure when squashing).
- In order to update our feature branches we could directly merge develop into our feature branch (if we go with the squash idea).

## Playground
- we have 2 feature branches that both should be merged into develop
  - git checkout develop
  - git merge feature/should-be-released
  - git merge this-shouldnt-be-released

- merge feature/should-be-released into master
  - git merge --squash feature/should-be-released
  - Approach 1: git commit -m "feature (NorwegianCreditReport): adds financial section to the norwegian credit report (KI1FI-223)" -> maybe use bisnode/components message structure (👍)
  - Approach 2: git commit -> Keep all the squashed commits grouped together (👎) This could be a nice approach when merging into the development branch (🤷‍)

- play arround with stuff
