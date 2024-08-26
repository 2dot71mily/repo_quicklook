# repo quicklook

## Can we access all commits in a PR?
Here we are looking at https://github.com/2dot71mily/repo_baby, a small repo composed of direct commits to main as well as 2 types of PRs: 
- first one not-squashed and 
- second one squashed 


### GitHub "Events" granularity
We can see several cases where a PR's "sub-commits" are not captured in the GitHub "Events" granularity.

This will arise for squashed PRs where not every commit is its own PushEvent (or somehow directly associated with another Event).

These are displayed in the cases labeled ` **** Is commit sha in EventsAPI json? False **** ` in the final notebook cell.

See the `smaller_repo` branch for a specific example of this.


### GitHub PR granularity
Rather these PR "sub-commits" can be accessed by using the GitHub Events API to find all PR numbers, and then doing an 2nd API call at the PR granularity to iterate through all the sub-commits in each PR.

We also looked for check-runs at the PR sub-commit granularity in the notebook's bottom cell. We added a GitHub workflow config as a later PR, so CI metadata can be found in the later PR files, e.g. [output_data/repo_baby_pull_f2af16a103f445845fc59ca5ad126789f1356cde_checkruns.json](output_data/repo_baby_pull_f2af16a103f445845fc59ca5ad126789f1356cde_checkruns.json).

From a quick read of the GitHub API docs, looking at these examples, it appears the a `PushEvent` is associated with GitHub CI and could be tracked if intra-PR CI is of interest.
