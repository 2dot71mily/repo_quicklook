# repo quicklook

## Can we access all commits in a PR?
Here we are looking at very [small repo](https://github.com/2dot71mily/toy_repo), composed of 2 PRs: 
- first one not-squashed and 
- second one squashed 


### GitHub "Events" granularity
Here on an even smaller repo we can more easily see several cases where a PR's "sub-commits" are not captured in the GitHub "Events" granularity.

This will arise for squashed PRs where not every commit is its own PushEvent (or somehow directly associated with another Event).

These are displayed in the cases labeled ` **** Is commit sha in EventsAPI json? False **** ` in the final notebook cell.


For example:
- the Events for this squashed PR commit:
https://github.com/2dot71mily/toy_repo/commit/673b77704f9908888716050414131ae3878d0a28
- do not record that the digit `3` was ever part of the repo's README.md in this PR:
https://github.com/2dot71mily/toy_repo/pull/2

### GitHub PR granularity
Rather these PR "sub-commits" can be accessed by using the GitHub Events API to find all PR numbers, and then doing an 2nd API call at the PR granularity to iterate through all the sub-commits in each PR.

(We also looked for check-runs at the PR sub-commit granularity in the notebook's bottom cell, but the repo looked at here had no checks.)

