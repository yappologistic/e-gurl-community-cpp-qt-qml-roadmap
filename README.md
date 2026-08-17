# E Gurl Community Edition: C++23 + Qt 6 + QML Roadmap

**Free community learning guide · CC BY 4.0 · Last verified 2026-08-16**

[License](LICENSE.md) · [How to contribute](CONTRIBUTING.md)

> [!NOTE]
> **Start here:** This is a free, beginner-friendly path from a first C++ program to a polished Qt Quick application with a C++ backend and QML interface. Plan for roughly **24 weeks at 8–10 hours per week**. The weeks are pacing suggestions, not deadlines. Advance when you can pass each phase's completion test.

## What this roadmap teaches

- Modern programming fundamentals using **C++23**.
- Safe ownership, RAII, standard containers, algorithms, and error handling.
- CMake, Git, debugging, automated tests, sanitizers, and static analysis.
- Qt Core, `QObject`, signals and slots, events, files, JSON, networking, and models.
- QML, Qt Quick, Qt Quick Controls, layouts, states, animation, and accessibility.
- A maintainable C++ backend connected to a QML frontend.
- Testing, profiling, deployment, and a portfolio-quality capstone.
- An optional later route into Quickshell and Linux desktop-shell development.

It does **not** require prior C++, Qt, QML, or GUI experience.

---

# 1. The technology map

| Name | What it is | What it does in an application |
|---|---|---|
| **C++23** | A compiled programming-language standard | Implements data, rules, algorithms, services, and performance-sensitive work |
| **Qt 6** | A cross-platform C++ framework | Supplies application infrastructure such as events, files, networking, threads, models, and UI libraries |
| **QML** | Qt's declarative UI language | Describes object trees, properties, bindings, signals, and UI behavior |
| **Qt Quick** | The main visual QML library | Supplies visual items, input, animation, models, views, and scene-graph rendering |
| **Qt Quick Controls** | Ready-made QML controls | Supplies windows, buttons, text fields, menus, dialogs, sliders, and styles |
| **CMake** | A build-system generator | Describes source files, dependencies, targets, tests, installation, and deployment |
| **Compiler** | GCC, Clang, or MSVC | Translates C++ source code into native machine code |
| **IDE/editor** | A coding environment | Helps edit, build, navigate, run, and debug; Qt Creator is the easiest Qt-first option |

QML is not a separate product with its own independently installed “QML 6” release. The QML language, engine, modules, and tooling ship with Qt.

```mermaid
flowchart LR
    A["C++23 language"] --> B["Qt 6 C++ framework"]
    B --> C["QML engine"]
    C --> D["Qt Quick visual types"]
    D --> E["Qt Quick Controls"]
    E --> F["Desktop or embedded application"]
```

## What versions should a beginner use?

| Component | Recommendation |
|---|---|
| C++ | Learn **C++23**. Add C++26 features later as compiler support and teaching material mature. |
| Qt | Use the **latest stable Qt 6 patch** available. At the last verification, the newest official release was Qt 6.11.1. |
| QML imports | Prefer modern unversioned imports such as `import QtQuick` and `import QtQuick.Controls` in new Qt 6 projects. |
| Build system | Use modern target-based **CMake** and `qt_add_qml_module()`. |
| Qt UI stack | Prefer **QML + Qt Quick + Qt Quick Controls** for the applications targeted by this guide. |
| C++ compiler mode | Request C++23, but verify individual library features against the compiler's support table. |

Authoritative references:

- [Published ISO C++23 standard](https://www.iso.org/standard/83626.html)
- [Current ISO C++ status](https://isocpp.org/std/status)
- [Qt 6.11.1 release announcement](https://www.qt.io/blog/qt-6.11.1-released)
- [Current Qt 6 documentation](https://doc.qt.io/qt-6/)
- [Getting started with Qt Quick applications](https://doc.qt.io/qt-6/qmlapplications.html)
- [`qt_add_qml_module()` documentation](https://doc.qt.io/qt-6/qt-add-qml-module.html)

---

# 2. The complete visual roadmap

```mermaid
flowchart TD
    P0["Phase 0<br/>Tools and first compile<br/>1 to 2 days"] --> P1["Phase 1<br/>C++ foundations<br/>Weeks 1 to 4"]
    P1 --> P2["Phase 2<br/>Modern C++ and STL<br/>Weeks 5 to 8"]
    P2 --> P3["Phase 3<br/>CMake, Git, debugging, tests<br/>Weeks 9 to 10"]
    P3 --> P4["Phase 4<br/>Qt Core and object model<br/>Weeks 11 to 13"]
    P4 --> P5["Phase 5<br/>QML and Qt Quick<br/>Weeks 14 to 18"]
    P5 --> P6["Phase 6<br/>C++ and QML integration<br/>Weeks 19 to 21"]
    P6 --> P7["Phase 7<br/>Quality and deployment<br/>Weeks 22 to 24"]
    P7 --> CAP["Capstone<br/>Tested and packaged Qt application"]

    P1 -.-> M1["Console mini-projects"]
    P2 -.-> M2["Persistent CLI application"]
    P4 -.-> M3["Qt Core data application"]
    P5 -.-> M4["QML-only interface"]
    P6 -.-> M5["C++ plus QML application"]
```

## Phase overview

| Phase | Suggested time | Main outcome |
|---|---:|---|
| 0. Orientation | 1–2 days | Compile, run, and debug a program |
| 1. C++ foundations | 4 weeks | Write small multi-file console programs |
| 2. Modern C++ | 4 weeks | Manage lifetime safely and use the standard library |
| 3. Engineering tools | 2 weeks | Build, test, debug, analyze, and version projects |
| 4. Qt Core | 3 weeks | Understand Qt's event-driven C++ model |
| 5. QML and Qt Quick | 5 weeks | Build a responsive, accessible interface |
| 6. C++ and QML | 3 weeks | Connect a clean backend to a declarative frontend |
| 7. Shipping quality | 3 weeks | Test, profile, package, and document a capstone |

---

# 3. How to study effectively

Use this loop for every topic:

1. Read or watch one small lesson.
2. Type the example yourself; do not paste it.
3. Predict the result before compiling or running it.
4. Change at least two parts and explain what changed.
5. Recreate the core idea with the lesson closed.
6. Use it in a small exercise or project.
7. Write down only the insight or mistake worth remembering.

A sustainable 8–10 hour week:

| Activity | Approximate share | Example |
|---|---:|---|
| Writing and changing code | 50% | Exercises and application features |
| Debugging and testing | 20% | Breakpoints, test cases, warnings, sanitizers |
| Lessons and documentation | 20% | One course chapter or focused video |
| Review and notes | 10% | Recall practice and a weekly retrospective |

> [!WARNING]
> **Tutorial familiarity is not programming ability.**
> Watching somebody solve a problem feels easier than solving it. Every week must include at least one small program built from an empty folder without a tutorial open.

## The stuck protocol

When code fails:

1. Read the **first** compiler or runtime error completely.
2. Reduce the problem to the smallest reproducible example.
3. State what you expected and what actually happened.
4. Inspect values with a debugger or temporary logging.
5. Check the official documentation for the exact API.
6. Search the exact error only after collecting this evidence.
7. Record the cause and fix in one or two sentences.

---

# 4. Phase 0 — Tools and the first compile

**Time:** 1–2 days

## Install or locate

- A C++ compiler with useful C++23 support: recent GCC, Clang, or MSVC.
- CMake and preferably Ninja.
- Git.
- The latest stable Qt 6 development package, including Qt Core, QML, Qt Quick, and Qt Quick Controls.
- An editor or IDE. Qt Creator is the most direct beginner experience for Qt and QML, but the project remains a normal CMake project and is not locked to an IDE.

The [Qt download page](https://www.qt.io/download-open-source) provides the official open-source installer. Linux distributions also package Qt, although package names and versions vary.

Check the tools that apply to the system:

```bash
g++ --version
clang++ --version
cmake --version
ninja --version
git --version
qtpaths6 --qt-version
```

Only one working C++ compiler is required.

## First C++ program

Create `main.cpp`:

```cpp
#include <iostream>
#include <string>

int main()
{
    std::cout << "What is your name? ";

    std::string name;
    std::getline(std::cin, name);

    std::cout << "Hello, " << name << "!\n";
}
```

With GCC or Clang, compile with warnings enabled:

```bash
g++ -std=c++23 -Wall -Wextra -Wpedantic main.cpp -o hello
./hello
```

On Windows PowerShell, the final command is normally:

```powershell
.\hello.exe
```

## Completion test

Explain this path in plain language:

```text
source file -> preprocessor -> compiler -> object file -> linker -> executable -> operating system
```

Also recognize the difference between:

- **Compiler error:** a source file cannot be translated.
- **Linker error:** compiled pieces cannot be combined, often because a definition is missing.
- **Runtime error:** the executable starts but behaves incorrectly or terminates.

---

# 5. Phase 1 — C++ foundations

**Time:** Weeks 1–4

Use [LearnCpp](https://www.learncpp.com/) as the main written course. It is free and teaches modern C++ progressively. Use [cppreference](https://en.cppreference.com/w/cpp) to look up known topics; it is a reference, not a beginner course.

## Week 1 — Values and control flow

Learn:

- Program structure and `main()`.
- Statements, expressions, variables, initialization, and assignment.
- Integers, floating-point types, `bool`, and `char`.
- Console input and output.
- Operators, conversions, and integer division.
- `if`, `else`, `switch`, `while`, and `for`.
- Scope and compiler warnings.

Build:

- Temperature converter.
- Number-guessing game.
- Menu-driven calculator with input validation.

**Completion test:** write FizzBuzz and the calculator from an empty file.

## Week 2 — Functions and files

Learn:

- Function declarations, definitions, parameters, and return values.
- Pass by value, reference, and const reference.
- Local versus global scope; avoid mutable global state.
- Header/source separation and include guards.
- Namespaces, `const`, `auto`, `enum class`, and simple `struct` types.

Build:

- A multi-file unit converter.
- Rock-paper-scissors with functions for each rule.
- A small reusable math or text utility library.

**Completion test:** explain why each declaration and definition lives in its selected file.

## Week 3 — Strings, containers, and algorithms

Learn:

- `std::string` and `std::string_view`.
- `std::array` and `std::vector`.
- Range-based loops and basic iterator concepts.
- `std::find`, `std::count`, `std::sort`, and `std::transform`.
- Basic lambdas and predicates.
- Text-file input and output.
- Separating data, logic, and presentation.

Build:

- Word-frequency counter.
- Grade tracker with statistics.
- Contact list stored in a simple text format.

**Completion test:** load records, filter them, sort them, calculate a result, and save them.

## Week 4 — Classes and object design

Learn:

- Classes, access control, constructors, and invariants.
- Member functions and `const` member functions.
- Composition before inheritance.
- Basic inheritance and virtual functions for recognition.
- Operator overloading only where it makes a type clearer.
- Keeping input/output outside domain objects.

Build:

- Bank-account model with enforced invariants.
- Inventory containing products.
- Small turn-based combat model.

**Completion test:** design two collaborating classes without public mutable data.

---

# 6. Phase 2 — Modern C++ and the standard library

**Time:** Weeks 5–8

## Week 5 — Lifetime, ownership, and RAII

Learn:

- Automatic, static, and dynamic storage duration.
- References versus pointers.
- Stack and free-store concepts without treating them as absolute language guarantees.
- Constructors, destructors, and RAII.
- `std::unique_ptr`, `std::shared_ptr`, and `std::weak_ptr`.
- Why raw pointers usually express non-ownership.
- Rule of zero as the preferred class design.

Avoid manual `new` and `delete` in ordinary application code while learning. Understand them, then use containers and RAII types.

Build:

- Resource-owning class using a standard RAII type.
- Tree or scene structure with explicit ownership.
- Exercise that identifies dangling references and lifetime errors.

**Completion test:** draw the owner and expected lifetime of every object in a small program.

## Week 6 — Errors and vocabulary types

Learn:

- Preconditions, invariants, assertions, and exceptions.
- `std::optional`, `std::variant`, and `std::expected`.
- `std::filesystem` and `std::chrono`.
- Templates at a practical introductory level.
- Concepts as readable template constraints.

Build:

- Configuration parser returning useful errors.
- File organizer with `std::filesystem`.
- Timer or Pomodoro engine using `std::chrono`.

**Completion test:** model “missing,” “one of several states,” and “success or error” without magic sentinel values.

## Week 7 — Copying, moving, and library fluency

Learn:

- Copy and move construction conceptually.
- Lvalues, rvalues, and move semantics at a practical level.
- Rule of zero, five, and three; prefer zero.
- Maps, sets, queues, and their tradeoffs.
- Iterator invalidation and algorithm complexity.
- Lambdas with captures.

Build:

- Searchable catalog using an appropriate associative container.
- Benchmark comparing two reasonable container choices.
- Refactor loops into standard algorithms where clarity improves.

**Completion test:** justify a container choice using access pattern, ordering, invalidation, and complexity.

## Week 8 — C++20/23 essentials and a CLI project

Prioritize:

- Ranges and views.
- Concepts.
- `std::span`.
- Designated initializers where suitable.
- `std::format` if supported by the chosen standard library.
- `std::expected`.
- Modules as awareness only until the toolchain and project justify them.
- Coroutines as awareness only; learn ordinary control flow and Qt's asynchronous APIs first.

Build a persistent CLI task tracker with:

- Add, edit, delete, list, filter, and sort.
- File persistence.
- Clear error messages.
- Multiple source files.
- No raw owning pointers.

**Completion test:** add a feature without rewriting the whole program and without mixing all input/output into the data classes.

---

# 7. Phase 3 — CMake, Git, debugging, and tests

**Time:** Weeks 9–10

## CMake

Learn:

- Targets and target properties.
- `add_executable()` and `add_library()`.
- `target_sources()`, `target_link_libraries()`, and `target_include_directories()`.
- `PUBLIC`, `PRIVATE`, and `INTERFACE` usage requirements.
- Out-of-source builds and build types.
- `find_package()` and imported targets.
- CTest and installation rules.

Minimal non-Qt project:

```cmake
cmake_minimum_required(VERSION 3.20)

project(community_cli LANGUAGES CXX)

add_executable(community_cli
    main.cpp
)

target_compile_features(community_cli PRIVATE cxx_std_23)
```

Build it:

```bash
cmake -S . -B build -G Ninja
cmake --build build
ctest --test-dir build --output-on-failure
```

Read the free [official CMake tutorial](https://cmake.org/cmake/help/latest/guide/tutorial/) and the [Qt CMake manual](https://doc.qt.io/qt-6/cmake-manual.html).

## Git

Learn:

- Repository, working tree, staging area, commit, branch, merge, and remote.
- Small commits with messages describing one coherent change.
- `.gitignore` for generated build directories.
- How to inspect a diff before committing.
- How to recover from an ordinary mistake without deleting work blindly.

Read [Pro Git](https://git-scm.com/book/en/v2), which is free online.

## Debugging and quality tools

Practice:

- Breakpoints, stepping, call stacks, watches, and conditional breakpoints.
- Compiler warnings and treating warnings seriously.
- Debug builds with symbols.
- AddressSanitizer and UndefinedBehaviorSanitizer on supported compilers.
- A unit-test framework such as Qt Test, Catch2, or GoogleTest.
- Formatting with `clang-format`.
- Static analysis with `clang-tidy`.

Example sanitizer configuration for GCC or Clang:

```cmake
target_compile_options(community_cli PRIVATE
    $<$<CONFIG:Debug>:-fsanitize=address,undefined -fno-omit-frame-pointer>
)

target_link_options(community_cli PRIVATE
    $<$<CONFIG:Debug>:-fsanitize=address,undefined>
)
```

**Completion test:** configure, build, test, and debug a project from a fresh clone using only its README.

---

# 8. Phase 4 — Qt Core and the Qt object model

**Time:** Weeks 11–13

Start with [Create Your First Applications](https://doc.qt.io/qt-6/create-your-first-applications.html), the [Qt 6 documentation](https://doc.qt.io/qt-6/), and the examples installed with Qt.

## Week 11 — Qt foundations

Learn:

- `QCoreApplication` and the event loop.
- `QObject` identity and parent-child ownership.
- Signals, slots, and connection syntax.
- `QString`, `QByteArray`, Qt containers, and when the standard library is preferable.
- `QTimer` and event-driven thinking.
- Qt value types versus `QObject` subclasses.

Build:

- Console countdown timer using `QTimer`.
- Event-driven status monitor.
- Small signal-and-slot experiment with custom objects.

**Completion test:** explain why a long blocking operation freezes an event-loop thread.

## Week 12 — Files, JSON, settings, and networking

Learn:

- `QFile`, `QDir`, `QFileInfo`, and standard paths.
- `QJsonDocument`, objects, and arrays.
- `QSettings`.
- `QUrl`.
- `QNetworkAccessManager`, replies, errors, and asynchronous results.

Build:

- JSON-backed settings or notes service.
- Small API client with loading, success, empty, and error states.

**Completion test:** retrieve or load data asynchronously and report failures without blocking the UI thread.

## Week 13 — Models, threads, and Qt Test

Learn:

- Model/View ideas and roles.
- `QAbstractListModel` conceptually.
- Thread affinity and queued connections.
- Worker-object pattern.
- `QtConcurrent` or asynchronous APIs when appropriate.
- Qt Test structure and data-driven tests.

Do not move work to a thread automatically. First determine whether the work blocks and whether an asynchronous Qt API already exists.

Build:

- In-memory list model.
- Background calculation with safe result delivery.
- Tests for JSON conversion and domain rules.

**Completion test:** explain which thread owns each `QObject` and how results cross thread boundaries.

---

# 9. Phase 5 — QML, Qt Quick, and Controls

**Time:** Weeks 14–18

Use the official [QML for Beginners YouTube playlist](https://www.youtube.com/playlist?list=PLizsthdRd0YwxekSSxUr5QVKIMKm6Y7bu) and the free [Qt Academy catalog](https://www.qt.io/academy/course-catalog) as the primary course.

```mermaid
flowchart LR
    Q1["QML syntax and properties"] --> Q2["Bindings and signals"]
    Q2 --> Q3["Components and layouts"]
    Q3 --> Q4["Controls and navigation"]
    Q4 --> Q5["Models, views, delegates"]
    Q5 --> Q6["States, animation, accessibility"]
```

## Week 14 — QML language fundamentals

Learn:

- Object declarations and the object tree.
- IDs, typed properties, aliases, signals, and signal handlers.
- Declarative bindings versus imperative assignments.
- Reusable component files.
- JavaScript expressions used sparingly for presentation logic.
- Modern unversioned imports.

Build:

- Profile card.
- Counter with reusable controls.
- Unit converter with live property bindings.

**Completion test:** explain why assigning to a bound property may replace its binding.

## Week 15 — Layout and responsive UI

Learn:

- `Item`, `Rectangle`, `Text`, and `Image`.
- Anchors, positioners, and Qt Quick Layouts.
- `implicitWidth`, `implicitHeight`, and size propagation.
- Avoiding conflicting anchors and layout properties.
- DPI-aware sizing and responsive structure.
- Focus, keyboard navigation, and pointer handlers.

Build:

- Responsive dashboard that works at several window sizes.
- Reusable card, toolbar, and empty-state components.

**Completion test:** resize the interface aggressively without overlaps or clipped essential content.

## Week 16 — Controls and application structure

Learn:

- `ApplicationWindow` and common Qt Quick Controls.
- Control styling versus replacing internal implementation details.
- Pages, stack navigation, drawers, dialogs, menus, and actions.
- Resource organization and QML modules.
- Theme tokens instead of duplicated literal colors and dimensions.

Build:

- Multi-page settings application.
- Light/dark theme based on centralized tokens.

**Completion test:** add a new page and navigation action without editing unrelated components.

## Week 17 — Models, views, and delegates

Learn:

- Model, view, delegate, and role responsibilities.
- `ListModel` for prototypes.
- `ListView`, `GridView`, delegate reuse, and required properties.
- Selection, filtering, sorting, and empty states.
- Why delegates should not own authoritative application data.

Build:

- Contact browser.
- Media or application launcher UI with filtering.

**Completion test:** replace the prototype model without redesigning the delegate.

## Week 18 — States, animation, debugging, and polish

Learn:

- States, transitions, behaviors, and explicit animations.
- Loaders and delayed component creation.
- QML logging, debugger, profiler, and object inspection.
- `qmllint` and `qmlformat`.
- Accessible names, descriptions, keyboard use, contrast, and motion restraint.

Build:

- Animated notification center.
- Polished dashboard with loading, error, empty, and populated states.

**Completion test:** the application works by keyboard, communicates state clearly, and has no unexplained QML warnings.

---

# 10. Phase 6 — Connecting C++ and QML

**Time:** Weeks 19–21

## Target architecture

```mermaid
flowchart LR
    UI["QML presentation<br/>components, layout, animation"]
    API["Thin QML-facing API<br/>properties, signals, invokable actions"]
    DOMAIN["C++ domain layer<br/>rules and testable types"]
    SERVICES["Services<br/>files, JSON, network, settings"]

    UI -->|"user actions"| API
    API -->|"commands and queries"| DOMAIN
    DOMAIN -->|"I/O requests"| SERVICES
    SERVICES -->|"results or errors"| DOMAIN
    DOMAIN -->|"state changes"| API
    API -->|"notifications and models"| UI
```

Keep visual structure and small interactions in QML. Keep authoritative data, business rules, persistence, networking, and substantial computation in C++. Avoid C++ code that searches the QML object tree by object ID.

## Week 19 — Exposing types and state

Learn:

- `Q_PROPERTY`, notification signals, and bindable state.
- Invokable methods and slots.
- `QML_ELEMENT` and declarative type registration.
- Context properties for understanding legacy examples, not as the default architecture.
- Ownership boundaries between C++ and the QML engine.
- Converting domain values to QML-friendly APIs.

Use the free Qt Academy courses [How to Expose C++ to QML](https://www.qt.io/academy/course-catalog) and [Introduction to Signals and Slots](https://www.qt.io/academy/course-catalog).

Build:

- C++ settings service displayed and edited from QML.
- Backend status object with observable properties.

**Completion test:** a C++ state change updates QML through notification, without polling.

## Week 20 — C++ models in QML

Learn:

- Subclassing `QAbstractListModel`.
- Custom roles and `roleNames()`.
- Correct begin/end calls for insert, remove, reset, and move operations.
- Emitting `dataChanged()` with accurate indexes and roles.
- Proxy models where suitable.

Build:

- C++ task model displayed by a QML `ListView`.
- Add, edit, remove, filter, and persist tasks.

**Completion test:** individual changes update the correct delegate without resetting the entire model.

## Week 21 — Application architecture

Learn:

- Presentation, domain, and service boundaries.
- Dependency injection with ordinary constructors.
- Asynchronous operations and explicit loading/error state.
- Cancellation, timeouts, retries, and application shutdown.
- Test doubles around filesystem or network boundaries.
- Keeping domain logic independent of visual components.

Build a task manager with:

- C++ domain rules and list model.
- QML pages, delegates, dialogs, and responsive layout.
- JSON persistence.
- Unit tests for domain rules and serialization.
- Clear loading, error, empty, and populated states.

**Completion test:** domain tests run without starting a graphical application.

---

# 11. Phase 7 — Quality, performance, and deployment

**Time:** Weeks 22–24

## Week 22 — Testing

Create a small test pyramid:

- Many fast C++ unit tests for rules and transformations.
- Model tests for roles and mutation behavior.
- QML tests for important components.
- A few end-to-end flows for critical user journeys.

Learn Qt Test, [Qt Quick Test](https://doc.qt.io/qt-6/qtquicktest-index.html), CTest integration, fixtures, parameterized tests, and deterministic handling of time and network behavior.

**Completion test:** introduce a deliberate regression, observe a relevant test fail, fix it, and watch the test pass.

## Week 23 — Diagnostics and performance

Learn:

- Measure before optimizing.
- QML Profiler and C++ sampling profilers.
- Binding loops, unnecessary reevaluation, heavy delegates, and excessive object creation.
- Logging categories and actionable error messages.
- Sanitizers and static analysis in regular development.
- `qmllint` and QML compiler warnings.

**Completion test:** identify one measured bottleneck, improve it, and preserve before/after evidence.

## Week 24 — Deployment and capstone

Learn:

- Release builds and platform deployment tools.
- QML module and plugin deployment.
- Runtime assets, fonts, translations, and licenses.
- Versioning, changelog, README, screenshots, and installation instructions.
- Continuous integration that builds and tests a clean checkout.

Follow the official [Qt deployment documentation](https://doc.qt.io/qt-6/deployment.html) because deployment differs across Linux, Windows, macOS, mobile, and embedded targets.

---

# 12. Capstone specification

Build an **expense tracker**, **study planner**, **media organizer**, or similarly sized application.

Required features:

- A modern Qt 6 CMake project.
- C++23 domain types and rules.
- A QML/Qt Quick Controls frontend.
- A C++ list model exposed to QML.
- Persistent JSON or SQLite storage.
- Filtering, sorting, and search.
- Responsive layout and keyboard navigation.
- Loading, empty, populated, and error states.
- Automated tests for core rules and persistence.
- No unexplained compiler, QML, or static-analysis warnings.
- A release build and documented installation process.
- README with screenshots, architecture, controls, build instructions, known limitations, and license.

## Definition of done

The capstone is complete when another person can clone it, follow the README, build it, run its tests, understand its architecture, and use its primary workflow without private instructions.

---

# 13. Project ladder

| Level | Project | Main skills |
|---:|---|---|
| 1 | Calculator | Variables, input, functions, conditions |
| 2 | Number-guessing game | Loops, state, validation, random numbers |
| 3 | Grade or contact tracker | Strings, vectors, algorithms, files |
| 4 | CLI task tracker | Classes, architecture, persistence, errors |
| 5 | Qt Core timer or API client | Event loop, signals, slots, async behavior |
| 6 | QML dashboard | Bindings, components, layouts, controls |
| 7 | QML contact browser | Models, views, delegates, filtering |
| 8 | C++ and QML task manager | Properties, signals, C++ list model, storage |
| 9 | Capstone | Tests, profiling, accessibility, packaging |

Do not make every practice project a calculator. Reuse the same concept in different domains so the idea becomes transferable.

---

# 14. A modern Qt Quick starter project

This example uses C++23, CMake, Qt Quick, a QML module, and modern unversioned imports. It requires Qt 6.5 or newer so it remains usable across several recent Qt 6 releases.

## Directory structure

```text
community-hello/
├── CMakeLists.txt
├── main.cpp
└── Main.qml
```

## `CMakeLists.txt`

```cmake
cmake_minimum_required(VERSION 3.21)

project(CommunityHello VERSION 1.0 LANGUAGES CXX)

find_package(Qt6 6.5 REQUIRED COMPONENTS Quick)

qt_standard_project_setup(REQUIRES 6.5)

qt_add_executable(CommunityHello
    main.cpp
)

target_compile_features(CommunityHello PRIVATE cxx_std_23)

qt_add_qml_module(CommunityHello
    URI Community.Hello
    VERSION 1.0
    QML_FILES
        Main.qml
)

target_link_libraries(CommunityHello PRIVATE Qt6::Quick)

install(TARGETS CommunityHello
    BUNDLE DESTINATION .
    RUNTIME DESTINATION bin
)
```

## `main.cpp`

```cpp
#include <QGuiApplication>
#include <QQmlApplicationEngine>

int main(int argc, char* argv[])
{
    QGuiApplication app(argc, argv);

    QQmlApplicationEngine engine;
    engine.loadFromModule("Community.Hello", "Main");

    if (engine.rootObjects().isEmpty()) {
        return -1;
    }

    return app.exec();
}
```

## `Main.qml`

```qml
import QtQuick
import QtQuick.Controls
import QtQuick.Layouts

ApplicationWindow {
    width: 640
    height: 420
    visible: true
    title: qsTr("E Gurl Community")

    ColumnLayout {
        anchors.centerIn: parent
        spacing: 16

        Label {
            id: greeting
            text: qsTr("Hello, Qt 6!")
            font.pixelSize: 28
            Layout.alignment: Qt.AlignHCenter
        }

        Button {
            text: qsTr("Change greeting")
            Layout.alignment: Qt.AlignHCenter
            onClicked: greeting.text = qsTr("C++ and QML are connected!")
        }
    }
}
```

## Build and run

```bash
cmake -S . -B build -G Ninja
cmake --build build
./build/CommunityHello
```

The executable location can differ with multi-configuration generators and on Windows. An IDE can configure and run the same `CMakeLists.txt` directly.

Run the generated QML lint target when available:

```bash
cmake --build build --target CommunityHello_qmllint
```

---

# 15. Free curriculum and documentation

> [!IMPORTANT]
> **Resource status**
> The links in this section were checked on **2026-08-16**. The curriculum favors official documentation, actively maintained courses, and modern Qt 6/CMake practices. A resource can be older and still teach a timeless concept well; anything version-sensitive is clearly labeled.

## How to use the resources

Use three kinds of material together:

1. A **course** gives the next lesson in a sensible order.
2. A **reference** answers a precise question while coding.
3. A **project** proves that the idea can be used without following somebody else.

Do not attempt to watch every linked channel. Pick one primary course, use documentation alongside it, and open supplementary videos only for a topic currently being practiced.

## Primary learning path

1. **[LearnCpp](https://www.learncpp.com/)** — structured modern C++ course.
2. **[Mike Shah's Modern C++ playlist](https://www.youtube.com/playlist?list=PLvv0ScY6vfd8j-tlhYVPYgiIyXduu6m-L)** — a long, ordered video companion from fundamentals onward.
3. **[CMake tutorial](https://cmake.org/cmake/help/latest/guide/tutorial/)** — official build-system course.
4. **[Pro Git](https://git-scm.com/book/en/v2)** — free Git book.
5. **[Qt Academy course catalog](https://www.qt.io/academy/course-catalog)** — free Qt, QML, Qt Quick, CMake, and C++/QML courses.
6. **[Qt Academy QML for Beginners on YouTube](https://www.youtube.com/playlist?list=PLizsthdRd0YwxekSSxUr5QVKIMKm6Y7bu)** — official ordered beginner series published in 2026. The [Qt announcement](https://www.qt.io/blog/free-qml-beginner-course-learn-qml-on-youtube-with-qt-academy) confirms its eight-part learning order.
7. **[Qt's First Steps with QML](https://doc.qt.io/qt-6/qmlfirststeps.html)** — official text introduction.
8. **[QML and C++ integration overview](https://doc.qt.io/qt-6/qtqml-cppintegration-overview.html)** — official bridge between the two layers.
9. **[Qt examples and tutorials](https://doc.qt.io/qt-6/qtexamplesandtutorials.html)** — runnable examples for targeted study.

## Exact resource order by phase

| Roadmap phase | Primary resource | Supplement only when needed |
|---|---|---|
| Phases 0–1: first C++ programs | [LearnCpp](https://www.learncpp.com/) in chapter order | [Mike Shah's Modern C++ playlist](https://www.youtube.com/playlist?list=PLvv0ScY6vfd8j-tlhYVPYgiIyXduu6m-L) for a video explanation |
| Phase 2: modern C++ | Continue LearnCpp and build the CLI project | [C++ Weekly](https://www.youtube.com/@cppweekly) for the specific feature being studied |
| Phase 3: tools | [Official CMake tutorial](https://cmake.org/cmake/help/latest/guide/tutorial/) and [Pro Git](https://git-scm.com/book/en/v2) | [Compiler Explorer](https://godbolt.org/) to inspect compiler behavior |
| Phase 4: Qt Core | [Qt Academy](https://www.qt.io/academy/course-catalog), starting with signals/slots and CMake with Qt | Qt examples installed locally and [Qt 6 API docs](https://doc.qt.io/qt-6/classes.html) |
| Phase 5: QML | [Official 2026 QML for Beginners playlist](https://www.youtube.com/playlist?list=PLizsthdRd0YwxekSSxUr5QVKIMKm6Y7bu) in order | [First Steps with QML](https://doc.qt.io/qt-6/qmlfirststeps.html) and the corresponding Qt Academy challenges |
| Phase 6: C++ with QML | [QML/C++ integration overview](https://doc.qt.io/qt-6/qtqml-cppintegration-overview.html) and Qt Academy's C++ exposure courses | Somco for a second explanation; KDAB for deeper models and architecture |
| Phase 7: quality and shipping | Official testing, profiling, and [deployment documentation](https://doc.qt.io/qt-6/deployment.html) | Current KDAB and Qt Group talks for targeted advanced topics |

## Reference material

| Question | Best starting reference |
|---|---|
| What does this C++ type or function do? | [cppreference](https://en.cppreference.com/w/cpp) |
| Is a C++ feature supported by the compiler? | [GCC status](https://gcc.gnu.org/projects/cxx-status.html), [Clang status](https://clang.llvm.org/cxx_status.html), or [Microsoft status](https://learn.microsoft.com/en-us/cpp/overview/visual-cpp-language-conformance) |
| How does this Qt class work? | [Qt 6 C++ API index](https://doc.qt.io/qt-6/classes.html) |
| Which QML type should be used? | [All QML types](https://doc.qt.io/qt-6/qmltypes.html) |
| How should a QML application be structured? | [QML and Qt Quick best practices](https://doc.qt.io/qt-6/qtquick-bestpractices.html) |
| How is a QML application built? | [Building a QML application with CMake](https://doc.qt.io/qt-6/cmake-build-qml-application.html) |
| How should QML be formatted? | [QML coding conventions](https://doc.qt.io/qt-6/qml-codingconventions.html) |
| How are Qt applications deployed? | [Qt deployment guide](https://doc.qt.io/qt-6/deployment.html) |
| What practices does the C++ community recommend? | [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines) |
| What code does a compiler generate? | [Compiler Explorer](https://godbolt.org/) |
| What implicit C++ operations are happening? | [C++ Insights](https://cppinsights.io/) |

## Good English-language YouTube channels

| Channel | Current value | Best use | Start when |
|---|---|---|---|
| [Qt Group](https://www.youtube.com/@QtStudios) | Official source; its complete QML beginner course was released in 2026 | QML, Qt Quick, current Qt features, and official webinars | Phase 5; use the QML course playlist first |
| [Mike Shah](https://www.youtube.com/@MikeShah) | The Modern C++ course continues from beginner material into advanced topics | A sequential video companion for C++ | Phase 0 or 1; follow the course order |
| [C++ Weekly](https://www.youtube.com/@cppweekly) | Frequent focused coverage of modern C++ versions and compiler behavior | Short explanations of C++20/23/26 features and good practices | Phase 2; search for the current topic rather than binge-watching |
| [CppCon](https://www.youtube.com/@CppCon) | Current conference talks plus a large fundamentals archive | “Back to Basics,” debugging, design, safety, performance, and the standard library | Late Phase 2 onward; talks supplement a course |
| [KDAB](https://www.youtube.com/@KDABtv) | Professional Qt/QML material, including recent Qt 6 coverage | QML architecture, models, C++ integration, tooling, debugging, and performance | Phase 5 onward |
| [Somco Software](https://www.youtube.com/@somco-software) | Practical Qt/QML series with a useful C++ integration progression | A second explanation and project-oriented walkthrough | After the official QML beginner course |

Useful secondary playlists:

- [KDAB Complete QML Training](https://www.youtube.com/playlist?list=PL6CJYn40gN6hdNC1IGQZfVI707dh9DPRc)
- [KDAB QML Tips and Tricks](https://www.youtube.com/playlist?list=PL6CJYn40gN6jWHP5krsQrVGyYtKh3A3be)
- [Somco/Scythe Studio Qt QML Tutorial](https://www.youtube.com/playlist?list=PLP7UmEJ9z4mpi0JXcPS0VRK-7eFAfROZI)
- [CppCon 2023 Back to Basics](https://www.youtube.com/playlist?list=PLHTh1InhhwT7gQEuYznhhvAYTel0qzl72) — older than this guide, but the language fundamentals remain useful; check the channel for newer talks on the same topics.
- [KDAB's curated QML resources](https://www.kdab.com/top-100-qml-resources-kdab/)

## Resource quality rules for community members

Before following a tutorial, check:

- Does it clearly target **Qt 6**, not only Qt 5?
- Does a new project use **CMake**, not qmake and `.pro` files?
- Does it use `qt_add_qml_module()` for a modern QML module?
- Are QML imports and registration patterns consistent with current Qt 6 documentation?
- Does the C++ code use RAII, standard containers, and explicit ownership instead of habitual manual `new`/`delete`?
- Can the important claim be confirmed in Qt documentation or cppreference?
- Is the tutorial teaching a transferable concept, or only asking viewers to copy a finished project?

> [!TIP]
> **Handling older tutorials**
> Older material can still explain properties, signals, layouts, models, and delegates well. Do not copy Qt 5 setup blindly. For a new Qt 6 project, prefer CMake over qmake, `qt_add_qml_module()` over manually managed resources, current registration macros, and the imports shown in current Qt 6 documentation.

---

# 16. Topics to postpone

Delay these until the core roadmap is comfortable:

- Template metaprogramming beyond practical templates and concepts.
- Custom allocators and allocator internals.
- Lock-free concurrency.
- Advanced coroutine machinery.
- C++ modules in complex cross-platform builds.
- Writing a custom QML rendering item or scene-graph node.
- Qt internals and private APIs.
- Large plugin architectures.
- Premature abstraction and “enterprise” architecture in tiny projects.

Postponing is not avoiding. It protects the foundation needed to understand these topics later.

## Common traps

- Learning from Qt 5/qmake material as if it were the current build path.
- Using raw owning pointers where a value, container, or RAII owner is clearer.
- Treating QML as HTML/CSS rather than an object and binding system.
- Writing all business logic in QML JavaScript.
- Exposing the entire C++ application directly to QML.
- Blocking the GUI thread with file, network, or expensive computation.
- Resetting a complete list model for every small change.
- Optimizing without measuring.
- Starting a huge dream project before completing small ones.
- Depending on an IDE button without understanding the underlying CMake target.

---

# 17. Optional specialization — Quickshell and Linux shells

Quickshell is a Qt Quick/QML toolkit for building desktop-shell components. It is an excellent later project, but it is not a substitute for learning QML fundamentals.

Begin this path after completing at least Phase 5 and preferably Phase 6.

```mermaid
flowchart TD
    A["QML fundamentals"] --> B["Reusable Qt Quick components"]
    B --> C["Models, bindings, states, and animation"]
    C --> D["Quickshell basics"]
    D --> E["Panels, launchers, notifications, and OSDs"]
    E --> F["Hyprland IPC and compositor integration"]
    F --> G["A maintainable personal desktop shell"]
```

Suggested sequence:

1. Read the [Quickshell introduction](https://quickshell.outfoxxed.me/docs/guide/introduction/).
2. Review its [QML language guide](https://quickshell.outfoxxed.me/docs/guide/qml-language/).
3. Follow the current [installation and setup guide](https://quickshell.outfoxxed.me/docs/guide/install-setup/) for the target distribution.
4. Build a clock, then a bar, system-status widgets, an on-screen display, and a launcher.
5. Add compositor IPC only after static components behave reliably.
6. Put configuration in version control and document external dependencies.

Third-party Quickshell videos age quickly and may target a different Linux distribution. Use them for concepts and visual ideas; use official documentation for installation and current APIs.

---

# 18. Qt licensing in plain language

Qt is available under commercial and open-source licenses. Learning and experimenting with an open-source Qt distribution is free. Distribution obligations depend on the Qt modules, their licenses, how the application is linked and shipped, and whether Qt itself was modified.

Before distributing an application:

- Identify the license of every Qt module and third-party dependency used.
- Read Qt's [open-source licensing obligations](https://www.qt.io/development/open-source-lgpl-obligations).
- Preserve required copyright and license notices.
- Ensure recipients can exercise the rights required by the applicable LGPL/GPL terms.
- Do not assume every Qt add-on uses the same license.
- Obtain qualified legal advice for a commercial product when the obligations are unclear.

This section is an orientation, not legal advice.

---

# 19. Master progress tracker

## C++ foundation

- [ ] I can compile and run a C++23 program.
- [ ] I can explain initialization, assignment, scope, and lifetime.
- [ ] I can divide a program into functions and source/header files.
- [ ] I can use strings, vectors, algorithms, and file I/O.
- [ ] I can design small classes with enforced invariants.
- [ ] I can explain ownership and apply RAII.
- [ ] I choose smart pointers only when dynamic ownership is necessary.
- [ ] I can use `optional`, `variant`, and `expected` appropriately.
- [ ] I can explain a container choice.

## Engineering tools

- [ ] I can configure and build an out-of-source CMake project.
- [ ] I can read a compiler or linker diagnostic.
- [ ] I can use breakpoints, stepping, watches, and the call stack.
- [ ] I can run tests with CTest.
- [ ] I can run sanitizers and static analysis.
- [ ] I can create focused Git commits and inspect their diffs.
- [ ] A new contributor can build one of my projects from its README.

## Qt Core

- [ ] I understand the event loop.
- [ ] I understand `QObject` identity and parent-child ownership.
- [ ] I can connect signals and slots safely.
- [ ] I can use timers, files, JSON, settings, and asynchronous networking.
- [ ] I understand model roles and thread affinity.
- [ ] I can test nonvisual Qt code.

## QML and Qt Quick

- [ ] I understand object trees, properties, bindings, and signals.
- [ ] I can create reusable components.
- [ ] I can build responsive layouts without conflicting geometry rules.
- [ ] I can use Qt Quick Controls and navigation.
- [ ] I understand models, views, delegates, and roles.
- [ ] I can create purposeful states and animation.
- [ ] I can use QML linting, formatting, debugging, and profiling tools.
- [ ] My UI supports keyboard navigation and accessible descriptions.

## Integration and shipping

- [ ] I can expose a focused C++ API to QML.
- [ ] I can implement a correct `QAbstractListModel`.
- [ ] Domain rules can be tested without a GUI.
- [ ] Long-running work does not block the GUI thread.
- [ ] The application handles loading, empty, error, and success states.
- [ ] I have measured performance before optimizing.
- [ ] I can produce and document a release build.
- [ ] My capstone can be built and tested by someone else.

---

# 20. The first seven days

## Day 1

- Install or verify the compiler, CMake, Git, and an IDE/editor.
- Compile and run the first C++ program.
- Change the greeting and deliberately create one compiler error.

## Day 2

- Learn variables, initialization, types, and input/output.
- Build a temperature converter.

## Day 3

- Learn conditions and loops.
- Build FizzBuzz and begin a number-guessing game.

## Day 4

- Learn functions and scope.
- Refactor the guessing game into functions.

## Day 5

- Learn strings and vectors.
- Build a small grade tracker.

## Day 6

- Use a debugger on the guessing game.
- Fix at least one issue by inspecting state rather than guessing.

## Day 7

- Rebuild one program from an empty folder without notes.
- Commit the week's projects to Git.
- Write three lessons learned and choose next week's exercises.

---

# Final rule

Do not wait to feel ready. Build small things, let errors become specific, and use each project to expose the next skill. Consistent practice and completed software matter more than racing through the calendar.
