First CI failure of my langchain4j PR: spotless failed on lines I never wrote.
The ratchet model: unmodified files are exempt from format drift, but the
moment you touch a file, the WHOLE file must satisfy current config. The
pre-existing violations were invisible on main and became mine on contact.

Fix: run the repo's own formatter (spotless:apply) and commit the format-only
hunk separately. Lesson: green tests are not green CI. Run the repo's own
lint gate before pushing.
