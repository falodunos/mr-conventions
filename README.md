## Why Conventions?
As projects grow large and teams expand, it's not uncommon to not have any of the original Engineers on the team. Apart from on-boarding new Engineers, you  find that it's difficult to keep track of the work that's done by people on the team if everyone communicates in the way they feel is appropriate.

As products become successful and support the business to the point where they've become mission critical, you'll find the increasing need for tracking changes. This not only serves as documentation for work achieved but helps in tracking bugs seeing Version Control Systems are meant to help us do exactly that.

It's important to note that conventions are NOT an imposed rule by which the team must abide by. Rather, they are an **agreed** upon set of rule, standards, styles and workflow which a particular team chooses to abide by. This means they can differ from team to team BUT must be adhered to by all members on a particular team.

## Commit Message Conventions

### Format of the commit message
```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

Any line of the commit message cannot be longer 100 characters! This allows the message to be easier to read on github as well as in various git tools.

### Subject line  
Subject line contains succinct description of the change.

#### Allowed `<type>`
- feat (feature)
- fix (bug fix)
- docs (documentation)
- style (formatting, missing semi colons, …)
- refactor
- test (when adding missing tests)
- chore (maintain)

#### Allowed `<scope>`
Scope could be anything specifying place of the commit change. For example $location, $browser, $compile, $rootScope, ngHref, ngClick, ngView, etc... or could be context for the commit e.g. user-validation, hospital-configuration.

#### `<subject>` text
- use imperative, present tense: “change” not “changed” nor “changes”
- don't capitalize first letter
- no dot (.) at the end

#### Message body
Do's use this to explain the motivation behind the change and not the actual change. The files already show the actual change.

What you want to do is use this as an opportunity to explain the reason, what it implies and caveats.

#### Message footer
The footer should be used for referencing issues/stories. e.g:

```
Closes #IR-308, #IR-245, #IN-992
```

### The seven rules of a great Git commit message
- Separate subject from body with a blank line
- Limit the subject to 50 characters.
- Do not capitalize the subject line
- Do not end the subject line with a period.
- Use the imperative mood in the subject line
- Wrap the body at 72 characters
- Use the body to explain what and why vs how.

These rules are adopted from [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit).

### Examples

```
fix($compile): add unit tests for IE9

Older IEs serialize html uppercased, but IE9 does not...
Would be better to expect case insensitive, unfortunately jasmine does
not allow to user regexps for throw expectations.

This commit implements the tests to make sure when incompatible
features are used, we know!

Closes #IR-392
```

```
chore (processor): add CPU arch filter scheduler support
  
In a mixed environment of running different CPU architecutres,
one would not want to run an ARM instance on a X86_64 host and
vice versa.
  
This scheduler filter option will prevent instances running
on a host that it is not intended for.
  
The libvirt driver queries the guest capabilities of the
host and stores the guest arches in the permitted_instances_types
list in the cpu_info dict of the host.
  
The Xen equivalent will be done later in another commit.
  
The arch filter will compare the instance arch against
the permitted_instances_types of a host
and filter out invalid hosts.
  
Also adds ARM as a valid arch to the filter.
  
The ArchFilter is not turned on by default.

Closes PC-999
```

## MR Conventions

#### MR Title
***
The MR title should be named using the following format:

```
#<story id> <story title>
```

#### MR Description Template
The description of the MR should contain the following headings and corresponding content in Markdown format.

```
#### What does this MR do?
#### How should this be manually tested?
```

#### Example


**Title:** 
```
#IR-916 Implement Hospital management
```

**Body:**
```
#### What does this MR do?
This MR fixes the bug observed in the number of interests column and also corrects the typographical error on the Preferred location column header.

#### How should this be manually tested?

- Login to the application.
- Navigate to `pending` page.
- Confirm that the typographical error on `Preferred location` column has been corrected.
- Click on the `number of interests` column header.
- Then the column records should be properly sorted in either ascending or descending order.
```