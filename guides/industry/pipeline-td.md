# What a pipeline TD does

This page is for programmers who are thinking about working as a pipeline TD. It describes the job, the roles around it, and how people get into it, and it includes one pipeline TD's own account. If the word *pipeline* is new to you, read [What a VFX pipeline is](vfx-pipeline.md) first.

A **pipeline TD** (technical director) writes and supports the tools that move work through a VFX studio. Pipeline TDs work between artists and software engineers. They stay close enough to the artists to sit next to one and fix a broken shot, and they are technical enough to design the tools that keep it from breaking again.

The job exists to save artists' time. Every minute an artist spends looking for files, fixing names, or waiting for a broken tool is a minute not spent on the shot. A good pipeline tool is one that artists barely notice.

## A request, from the inside

Here is a real example from the author of this course, who works as a pipeline TD.

Colleagues at the studio asked for a Gantt chart. The vendor of their tracking system had suggested building a custom one in a web framework, so that became the request. But the goal was never a chart. The real need was simpler: a clear way to assign people's working hours across weekends, holidays, and overtime. A small algorithm that assigns the dates, shown in a plain table, did exactly that.

That is a large part of the job: finding the need behind the request before writing any code.

## The work

Most pipeline work is about how files are saved, loaded, published, and handed between departments. It is rarely about the images themselves. Day to day, that means:

- **Building tools.** Scripts, tools, and plugins that solve artists' problems and speed up their work. Many of them run inside the artists' applications, such as Maya (3D), Houdini (effects), and Nuke (compositing).
- **Supporting artists.** Solving problems directly, at the artist's desk or through a ticket system, and finding out why a shot doesn't load, render, or publish.
- **Connecting people.** Turning an artist's complaint into a clear problem for the software developers or the IT team, and explaining technical limits to the **production team**, the people who plan the studio's schedule and budget.
- **Testing and documenting.** Checking tools in real production and keeping their documentation up to date.

Most days mix building and supporting. At [one meetup](https://pipedev.org/posts/2023-05-17-what-makes-a-pipeline-person/), pipeline developers estimated the split at about 60% development and 40% support, and said the balance changes with the production schedule. Deadlines are also shorter than in most other engineering roles at a studio, because a **show**, the film or series the studio is working on, can't wait.

## One pipeline TD's view

In this section, the author of this course describes their own work as a pipeline TD at a small studio, interviewed for this guide. It is one person's experience, and other pipeline TDs may see the job differently.

**The route into the job.** The TD didn't start in VFX at all. They began in audio: live mixing at concerts, then sound for video. Video led to 3D, 3D led to a game engine and C++, and that led to modeling in Blender and writing Python scripts for it. Their computer was too slow for heavy rendering, so they practiced programming while they waited for a new one, and programming interested them more than anything else. The TD moved into software development, then into software architecture and design.

Then the TD met compositing artists who wanted to learn programming. The first tool the TD built for them was a small server that let the artists run code inside Nuke directly from their text editor. Slowly, helping those artists turned into a pipeline job.

**Building a pipeline from nothing.** At their current studio, the TD built the whole pipeline from nothing: no existing tools or files, only an idea of what it had to do. The first step was not code. The TD sat down with the studio's supervisors and drew a mind map of how work should flow through the studio: ideas and branches, more brainstorming than design.

Next came the decision the TD is proudest of. The TD wrote most of the code in-house instead of depending on third-party packages for everything. The TD also made the pipeline self-contained, so the studio never needs its IT team to update Python or the pipeline itself. "Best decision I ever made," the TD says. What the TD would do differently: release tools sooner and get feedback, instead of trying to make every detail perfect first.

**An ordinary day has little code in it.** "Writing code to fix a problem is easy, because it's fun," the TD says. But every new piece of code is tied to other pieces, and it has a cost that appears later: in upgrades, changes, bug fixes, and the time someone needs to understand it. A good ordinary day is one where the TD helps a colleague think a problem through and they find a solution that needs no new feature at all.

**Finding the need behind the request.** Artists, leads, and supervisors often don't have the words to describe a technical problem, and they can't see how the pipeline works inside. So they often believe that code can fix anything. The TD's job is to find the real problem without telling anyone "you don't know what you want." The TD's advice: respect the other person's point of view, and look into it seriously even when you think there is a better way. Someone who sees the work differently often has something to teach you. The Gantt chart at the top of this page is one example.

**When a client changes the rules.** Requirements can change in the middle of a show. For changes like these, the TD built a hook system: **hooks** are small pieces of code that the pipeline runs automatically at a chosen moment. The TD uses them in two separate ways.

- **Installing what the machines won't allow.** In one recent case, a client required a new color-management library that was still unfinished, and the studio's machines didn't allow installing extra libraries. The TD used hooks to install the library through the pipeline itself.
- **Updating work that has already started.** A change can reach hundreds of Nuke scripts (Nuke's project files, which artists are already working on) that all need the same metadata or export update. When a chosen event happens, a hook lets the VFX editor update those files afterward, without asking every artist to redo their work.

**What the TD wishes they had known.** "Pipeline is more about the people using the pipeline than the code itself. You are connecting people, not abstract interfaces of DCCs and databases." (A **DCC**, digital content creation application, is an artist's program such as Maya or Nuke.)

## How people get in

Pipeline TD is rarely a first job. Most people start as an **assistant TD**, also called a junior pipeline TD. They come from two directions:

- **From art.** Artists with strong technical interests move into TD work. They already understand what artists need.
- **From programming.** Computer science graduates and software developers join a studio and learn how a studio makes films while they work. Large studios accept either a computer science degree or equivalent industry experience.

The TD above mixed both routes: audio and 3D first, then software development, then pipeline work. Practitioners disagree about which background makes better TDs. They agree that whichever side you come from, you have to learn the other.

## Roles that are easy to confuse

"TD" is not one job. Studios use the title for very different roles, some close to art and some close to engineering. Three roles are often confused with pipeline TD:

| Role                                                        | What it does                                                                                   | How it differs from a pipeline TD                                                                       |
| ----------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Department TD (for example, an effects TD or a lighting TD) | Solves technical problems inside one department, and often creates work that appears on screen | Specializes in one department; a pipeline TD works across departments                                   |
| Software developer (R&D)                                    | Builds core systems and new technology, often over months or years                             | Longer projects, less direct artist support, and employers more often require a computer science degree |
| IT                                                          | Manages accounts, networks, storage, and machines                                              | Not pipeline work; giving one person both jobs often fails                                              |

"Pipeline TD" and "pipeline developer" have no standard difference. Some studios use both names for one role, and others use them for two. The useful difference is how much direct artist support the job includes.

## The ladder and the size of the studio

A common career path has five steps:

1. Assistant TD.
2. Pipeline TD.
3. Senior or lead pipeline TD.
4. **Pipeline supervisor**: manages the pipeline for one or more shows, and the pipeline TDs who work on them.
5. **Head of pipeline**: manages the whole pipeline team, its plans, and its budget.

In a large studio, the work is split across teams: pipeline TDs, supervisors, software developers, and people who design the overall system. At some large studios, a pipeline TD gets daily tasks from the show's **CG supervisor** (the person who leads the computer-graphics work on the show), while their manager sits in the technology department.

In a small studio, one pipeline TD often designs, builds, installs, documents, and supports everything, including work that software developers would do in a large studio. The TD interviewed above works this way.

## What studios ask for

Job postings and career profiles list these skills:

- **Required:** Python at an advanced level, Linux, building tools inside at least one artist application, and understanding how a film's visual effects are made, from filming to the finished shot.
- **Expected:** Qt and PySide for artist interfaces; Git, code review, testing, and continuous integration; and clear communication with artists and the production team.
- **Often a plus:**
  - production tracking systems and databases;
  - render farm software such as Deadline, which schedules rendering across many machines;
  - USD;
  - open-source VFX libraries such as OpenImageIO and OpenColorIO.
- **C++ is useful, but not the first thing to learn.** Career profiles often list C++ as essential, but [studio job postings](https://www.entertainmentcareers.net/industrial-light-and-magic/pipeline-technical-director-level-i-expression-of-interest/job/415259) usually list it as a plus or leave it out. It probably matters more for software developer and department TD roles. For a pipeline TD job, Python comes first.

## Why this course works the way it does

This course is built for programmers who come into the job from the programming side. Its habits come from the work described above:

- **Agree on the input and output first.** Each department relies on what the one before it promised, so every course tool starts from a written description of what it accepts and what it returns.
- **Check before you trust.** A problem found late costs the most, so the course's tools check what arrives before anyone works on it, like the delivery check in [What a VFX pipeline is](vfx-pipeline.md).
- **Never overwrite.** Versions let a studio return to earlier work and let departments agree on what they used.
- **Write clear messages and exit codes.** The reader of an error message is often an artist, and sometimes another tool.
- **Get a review before production.** A tool isn't finished when its author says so. Another TD tries it, and a lead TD decides whether it is ready. The course's peer reviews and lead TD reviews practice that step.

## Further reading

- ScreenSkills, [Pipeline technical director (TD)](https://www.screenskills.com/job-profiles/roles/pipeline-technical-director-td): the UK screen industry's career profile of the role, with links to related TD profiles.
- Industrial Light & Magic, [Pipeline Technical Director, Level I](https://www.entertainmentcareers.net/industrial-light-and-magic/pipeline-technical-director-level-i-expression-of-interest/job/415259) (2023): a real entry-level posting from a large studio.
- pipedev.org, [What Makes a Pipeline Person?](https://pipedev.org/posts/2023-05-17-what-makes-a-pipeline-person/) (2023): notes from a pipeline developers' meetup on the job, the development and support split, and career paths.
- Lidia Martinez, [All about Technical Directors](https://blog.lidia-martinez.com/all-about-technical-directors-part-1): a former TD on why "TD" means so many different jobs.
- Foundry, [What is a Technical Director? VFX roles explained](https://www.foundry.com/insights/technical-director-vfx-roles-explained) (2025): a pipeline TD describes their route and their work.
- The Rookies, [Working as a Pipeline TD at DNEG](https://www.therookies.co/blog/careers/marieke) (2020): an interview with a pipeline TD at a large studio.
