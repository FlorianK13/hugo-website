---
date: '2024-11-18T16:54:07+01:00'
draft: false
title: 'Using the ORCID API to Manage Publications in Your Personal Hugo Site'
---
I recently migrated my personal website from a React template to a Hugo PaperMod site. This decision was motivated by the simplicity Hugo offers: creating a clean, functional site without the need to write and maintain extensive `HTML` or `JavaScript` code. However, when I wanted to add my list of publications, I ran into a challenge.

Initially, Hugo seemed to only support Markdown files, which meant I would have to manually create a Markdown list of my publications. This was not only tedious but also presented a maintenance issue. Each time I published something new, I’d either have to update the Markdown file manually or risk having an outdated publication list—a common issue on many researchers’ websites.

I thought, There must be a way to integrate my ORCID publication list. Enter **Hugo Layouts**.

[Hugo Layouts](https://gohugo.io/templates/introduction/) are a powerful and simple way to build HTML templates, which are then populated with content from your Markdown files. They provide the flexibility of JavaScript, making them a great tool for tasks like this. Here's how to use them:

## Steps
1. Create a `publications.html` file in your hugo project, located in `layouts/_default/`.
1. Copy and paste this code in the file:

    ```html {linenos=true}
    {{ define "main" }}
    <h1>My Publications</h1>
    </br>
    <div id="publications">Loading...</div>
    <script>
    const orcid = "{{ .Params.orcid }}"
    fetch(`https://pub.orcid.org/v3.0/${orcid}/works`, {
        headers: { Accept: "application/json" },
    })
        .then((response) => response.json())
        .then((data) => {
        const publications = data.group
            .map((work) => {
            console.log(work)
            const title = work["work-summary"][0].title.title.value
            const journalTitle =
                work["work-summary"][0]["journal-title"]?.value || " "
            const externalUrl = work["work-summary"][0]["url"].value || "#"
            const publicationYear =
                work["work-summary"][0]["publication-date"]["year"]?.value || " "
            return `
            <li>
                <a href="${externalUrl}" target="_blank"><strong>${title}</strong></a><br>
                <i>${publicationYear}${
                journalTitle != " " ? ", " : ""
            }${journalTitle}</i>
            </li>
            `
            })
            .join("")
        document.getElementById(
            "publications"
        ).innerHTML = `<ul>${publications}</ul>`
        })
        .catch((error) => {
        document.getElementById("publications").textContent =
            "Failed to load publications."
        })
    </script>
    {{ end }}
    ```

1. Create a `publications.md` in your `content` directory:

    ```yaml {linenos=true}
    ---
    title: "Publications"
    layout: "publications"
    summary: "My publications based on my ORCID"
    orcid: "0000-0002-1825-0097"
    ---
    ```

1. If everything worked, head over to your [Publications](/publications) subpage. 

