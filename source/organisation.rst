PySFML organisation
-------------------
Since recently, the source code of this project no longer lies in the
list of my personal Github repositories, and instead was moved to a
dedicated Github organisation. This is the begining of a new project which consists
of taking the whole thing one step further because Python has a huge
potential in the area of building multimedia applications. Unfortunately,
it remains unexploited nowadays and this is an attempt to fill the gap.

At this time of writing, there's still a lot of work ahead in term of
organisation but here is the big picture. This projects aims to...

- Provide well-maintained Python bindings for SFML with tutorials translated, an up-to-date API documentation and the official examples adapted.
- A lot of library based on SFML were developed; it could be great to have a large set of bindings that coerce well with the initial bindings.
- A set of documents to help people contribute and port other SFML-based librairies to Python (guidelines, developer notes).
- Exposing a Python C API is essential to implement to accomplish the above task.
- Given the complex (versioning, dependencies, etc...), set up a CI service (build bots) to make bindings accessible.
- Unit tests
- A website to keep track of the recent activities and show how fast that project is moving toward its goal
- Make application easily deployable for **Android** (& iOS)
- Writing applicationsq with PySFML is one thing, yet one need to understand how to distribute it; tutorials are provided.

Additional motivations include improving Cython and teach myself continious integration services!
