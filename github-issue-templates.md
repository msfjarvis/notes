---
date: 2020-10-24T15:45
---

# GitHub issue templates and YAML

After half an hour of fucking around with GitHub's issue template generator, I finally found the YAML quirk that caused my issue templates to be ignored in the APS repository. It seems GitHub tries to parse a list out of a string as opposed to just taking in a list, so my wrong (for both cases) YAML that looked like this:

```
---
labels: bug, 'triage: needed'
---
```

failed to parse and resulted in the templates being ignored by GitHub. I've fixed the YAML to this:

```
---
labels: 'bug, triage: needed'
---
```

and it started working in my test repo. Still kinda mad that GitHub didn't give an error or warning that the frontmatter was invalid :/
