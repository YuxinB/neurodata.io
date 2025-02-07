# neurodata.io

This is the static site generator code for [neurodata.io](https://neurodata.io)

## Prerequisites

At a minimum, you will need the following tools installed:

1. [Git](http://git-scm.com/)
2. [Grow](https://grow.io)

If you do not have Grow, you can install it using:

```sh
curl https://install.grow.io | bash
```

or (from a virtual environment)

```sh
pip install grow
```

Note that grow does not yet support Python 3.

## Running the development server

Prior to starting the development server, you may have to install dependencies used by your project. The `grow install` command walks you through this and tries to set up your environment for you.

The `grow run` command starts your development server. You can make changes to your project files and refresh to see them reflected immediately.

```sh
grow install
grow run
```

## Building

You can use the `grow build` command to build your whole site to the `build` directory. This is a good way to test and verify the generated code.

```sh
grow build
```

## Contributing

Please submit pull requests to `deploy` branch.


## [DEV/QC] Bib files and references

There is a LaTeX file that will build the references into a PDF, mostly
for QC. It is located in the root directory and can be built by running
`make` in the root directory.

## Bib addition rubric
When adding a new addition to the bib files, most normal bib entries will work, with the only additional step being the addition of a `keywords` value. Which keywords should be used for each bib file are displayed below, as they are used to organize the file.
General rules:
- When adding entries to either the pubs.bib or talks.bib files, include an entry called `author+an`, this serves to underline lab members and bold jovo's name in the publication sections of his CV. Looking at the order of authors for a bib entry, number which authors are lab members (`trainee`) and which is jovo (`highlight`). For example:
```
@article{example,
author = {<lab member> and <not lab member> and <jovo> and <lab member> and <not lab member>},
author+an = {1=trainee;4=trainee;3=highlight},
...
```
- DO NOT add an `@incollection` citation unless you are adding a new member to the `people.bib` file
- Make sure that `month` is an integer, as this prevents potential ordering issues
- Avoid symbols such as `&` and `$` in your entries, as they may cause issues with bib compiling

Categories for pubs.bib:
- For accepted and published peer-reviewed papers: `peer-reviewed`
- For papers currently under review: `in-review`
- For conference papers: `conference`
- For book entries: `book`
- For technical reports: `tech`
- For abstracts/posters: `abspos`
- For other publications: `other`
- For papers without Jovo as an author, but still referenced on the website: `omit`

categories for talks.bib:
- For local talks: `local`
- For international talks: `international`

Categories for press.bib:
- N/A


## Team member addition info
All information regarding team members for both the website's neurodata.io/about/team/ page, and Jovo's CV (neurodata.io/about/jovo, the Mentorship section) is derived from the bib file located in `content/bibs/people.bib`. It is very important that everyone keep their personal information up to date, as this will be reflected on Jovo's CV. In addition to the information added here, you will need to upload an image to `content/source/images/people` and state its name in the `file` category (for example, `john_doe.jpg`). See below if you wish to add someone to the website who shouldn't show up on either the cv or the Teams page.

```
@incollection{<ID>,
    author = {Full name},
    usera = {Job title},
    month = {Month, as an integer, that you started working},
    year = {starting year},
    number = {starting month/year -- ending month/year},
    series = {ending year},
    abstract = {What you do in the lab, 1-2 sentences, 3rd person},
    userb = {highest degree held},
    userc = {department/major, school},
    userd = {website category},
    keywords = {cv category},
    doi = {github username},
    note = {email address},
    url = {personal website (do not include https://)},
    usere = {training},
    file = {image name}
}
```
Some categories can be left blank if not applicable, the categories required to have information in them are: `<ID>`, `author`, `usera`, `month`, `year`, `number`, and `userd`. Some more notes:
- Abbreviations are heavily encouraged for `userb` and `userc`
- `year` and `series` should have all 4 digits of the year (i.e. 2019, not 19)
- `number` should be in the format of `{01/18 -- }` if the team member is still a member of the lab, and `{01/18 -- 04/21}` if they are no longer a member.
- Categories for `userd` are (in order of placement on the teams page):
    - `faculty`
    - `faculty - research`
    - `staff`
    - `postdoc`
    - `student`
    - `undergrad`
    - `associate`
    - `highschool`

- Categories for `keywords` are: 
    - Research Track Faculty Mentorship = `researchtrackfaculty`
    - Staff Research Scientist = `staffresearch`
    - Postdoctoral Fellow = `postdoc`
    - Ph.D. Student = `PhDstudent`
    - Visiting Doctoral Student = `visitingdoc`
    - Masters Student = `MSstudent`
    - Undergrad Student = `undergrad`
    - High School Student = `HS`
- Your image can be found here () if you are already on the website
- Current supported `usere` entries are:
    - `safe-zone`


An example entry is:
```
@incollection{johndoe,
    author = {John Doe},
    usera = {Research Assistant},
    month = {7},
    year = {2019},
    number = {7/19 -- },
    series = {},
    abstract = {Lead developer on <project>, helping with <something>...},
    userb = {BSE},
    userc = {BME, JHU},
    userd = {student},
    keywords = {MS},
    doi = {jnydoe},
    note = {jdoe234@jhu.edu},
    url = {www.heresjohnny.com},
    usere = {safe-zone},
    file = {john_doe.jpg}
}
```

## Adding someone who shouldn't appear on the Teams page or CV:
To do this, simply copy the entry below (yes, there should be spaces in the `number` and `series` sections) and change the relevant information. The `other` specification for both `userd` and `keywords` tell the website to ignore showing these people on the Teams page (though they will appear when referenced elsewhere) and for the CV to ignore them on generation.
```
@incollection{johndoe,
    author = {John Doe},
    usera = {},
    month = {},
    year = {},
    number = { },
    series = { },
    abstract = {},
    userb = {},
    userc = {},
    userd = {other},
    keywords = {other},
    doi = {},
    note = {jdoe234@gmail.com},
    url = {},
    usere = {},
    file = {john_doe.jpg}
}
```

## Hosting files on the website:
CURRENTLY UNDER DEVELOPMENT
