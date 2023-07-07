# Jira JQL

## Find all linked tickets

```
issuekey in linkedIssues("ISSUEID")
```

## Query for Newly Changed Tickets

```
creator in ("PERSON1", "PERSON2", "PERSON3") OR issueFunction in commented("by PERSON1") OR issueFunction in commented("by PERSON2") OR issueFunction in commented ("by PERSON3") OR status changed by "PERSON1" OR status changed by "PERSON2" OR status changed by "PERSON3" ORDER BY updated ASC
```

## Look for Jira interaction from specific users

```
creator in ("PERSON1", "PERSON2", "PERSON3") OR issueFunction in commented("by PERSON1") OR issueFunction in commented("by PERSON2") OR issueFunction in commented ("by PERSON3") OR status changed by "PERSON1" OR status changed by "PERSON2" OR status changed by "PESON3" ORDER BY updated ASC
```

## Recently updated CAST tickets

Note: you don't need a filter, you can use other criteria.  Also the definition of a closed ticket tends to change from org to org.

`Filter = "FILTERNAME" AND updated > -15d AND status not in (Closed, Done)`

## Stale CAST tickets

Note: you don't need a filter, you can use other criteria.  Also the definition of a closed ticket tends to change from org to org.

```
project = 'PROJECT' AND status not in ("Done", "Closed") AND created < -10d AND updated < -10d AND issueFunction not in commented("after -10d")
```
