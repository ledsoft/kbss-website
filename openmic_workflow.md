# Open Mic Workflow

## What is Open Mic:

Open Mic session is an activity going on approximately every other week. A KBSS team member or a guest presents an
interesting topic to the rest of the team and anyone willing to listen.

## Open Mic Structure

It consists of two posts:

- [Open Mic Announcement](_drafts/open-mic-announcement-template.markdown): includes when and where the next open mic
  session will take place.
  - It should be published around two weeks before the session
  - We should update the topic of the session at least 3 days before the session
- [Open Mic Session](_drafts/open-mic-session-template.markdown): includes the session materials (video and
  presentation)

### How To Create The Posts:

If you have access to GitHub actions (tab `Actions`) of this repository, they can help you create posts [semi-automatically](#using-github-action).
Otherwise, you have to do it [manually](#manually). 


#### Using Github Action

There are two GitHub that can be used to create posts: one for [sessions](https://github.com/kbss-cvut/kbss-website/actions/workflows/open-mic-summary-post.yml) and one
for [announcements](https://github.com/kbss-cvut/kbss-website/actions/workflows/open-mic-announcement-post.yml). The actions can be started using `Run workflow` button
which opens a modal dialog to enter required information (e.g. date of the session). After a successful run of the workflow, a pull request (PR) is created, which one 
can revise and fine-tune.

#### Manually

There are two templates, one for [sessions](_drafts/open-mic-session-template.markdown) and one
for [announcements](_drafts/open-mic-announcement-template.markdown). Templates are located in the `_drafts` folder and
contain instructions:

- CREATE A COPY TO THE _POSTS FOLDER AND RENAME IT TO [date]-[name].markdown and then follow instructions in it how it
  shall look like. **Use the current date for the file name, otherwise it will not be displayed.**
- Create new post both for announcement and past session.
- Create a **PULL REQUEST** and send it for **REVIEW** and **MERGE**

### Where Can I Find The Open Mic Session Link

- KBSS calendar: includes info  **where** and **when** the session takes place
- KBSS website: it should contain a public link to join the session

## Open Mic Software

Jitsi:
- [Meeting link](https://meet.jit.si/open-mic-kbss)
