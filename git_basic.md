`git add`:   stages a change. Any changes that are staged will become a part of the next snapshot and a part of the project’s history. Staging and committing separately gives developers complete control over the history of their project without changing how they code and work.

`git commit`: saves the snapshot to the project history and completes the change-tracking process. In short, a commit functions like taking a photo. Anything that’s been staged with git add will become a part of the snapshot with git commit.

`git status` shows the status of changes as untracked, modified, or staged.

`git branch`: shows the branches being worked on locally.

`git merge`: git merge merges lines of development together. This command is typically used to ==combine changes made on two distinct branches==. For example, a developer would merge when they want to combine changes from a feature branch into the master branch for deployment.

`git pull`: git pull updates the local line of development with updates from its remote counterpart. Developers use this command if a teammate has made commits to a branch on a remote,

`git push` updates the remote repository with any commits made locally to a branch.
