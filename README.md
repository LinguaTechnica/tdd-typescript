# Enterprise Curriculum Block Template

This template provides a basic folder structure and configuration for a curriculum block in Learn.

The template sets up the following:

- `config.yaml` - YAML file defining the structure, descriptions, and filepaths for content in the block
- `assets/` - folder for any images or supplemental files needed in a unit
- `units/` - folder for holding units
- `units/sample-lesson.md` - a sample lesson with learning objectives, content, and checks for understanding
- `units/sample-checkpoint.md` - a sample checkpoint with a challenge
- `.vscode/settings.json` - settings needed to use gMark within VSCode
- `prettier.config.json` - configuration settings for formatting

A Block is a related collection of standards that together describe a larger learning achievement. Blocks consist of one or more units. Each unit is comprised of one or more lessons and **may** have exactly one checkpoint that assesses the standard the unit represents.

## Best Practices

- Lessons follow an I Do, We Do, You Do format
- Each lesson has between 2 to 4 learning objectives
- Learning objectives are specific and measurable
- Lessons have multiple Checks For Understanding throughout to assess student comprehension

## Useful Tools

- [gMark - VSCode extension](https://github.com/gSchool/gMark) - extension providing useful shortcuts & nippets for Learn curriculum development
- [InstallFest](https://github.com/gSchool/install-fest-ent) - a Hub repository of installation instructions for any and all software needed by students in class

## Quick References

- [Learn Documentation course](https://learn-2.galvanize.com/cohorts/667) - a helpful curriculum created by the Learn product team that walks through curriculum development and the Learn ecosystem in depth

---

:fire: If you have read all of this or just plain don't care, delete everything from here up :point_up:!

# Topic_Name Block

## Learn

This repo is deployed as a Learn block [here]().

## Prerequisites

<!-- Things taught _before_ this block ever starts -->

For Angular, this might look like the following:

Before releasing this block to students, they should have completed:

- TypeScript Fundamentals & Jasmine
- Component-Driven Architectures

---

## Block Structure, Lesson Dependencies, & Lesson Statuses

### Units

|       | Unit                                                             | Duration |
| ----- | ---------------------------------------------------------------- | -------- |
| 1.    | [Intro to Angular](#intro-to-angular)                            | 1 Block  |
| 2.    | [Angular Components and Binding](#angular-component-and-binding) | 6 Blocks |
| Total | 2 Units                                                          | 7 Blocks |

### Lessons

#### Intro to Angular

|     | Lesson                                                                           | Duration  | Dependencies |
| --- | -------------------------------------------------------------------------------- | --------- | ------------ |
| 1.  | [Learning Objectives](/units/1-introduction-to-Angular/i-learning-objectives.md) | > 1 Block |              |
| 2.  | [What is Angular](/units/1-introduction-to-Angular/ii-what-is-angular.md)        | > 1 Block |
| 3.  | [What is TypeScript](/units/1-introduction-to-Angular/iii-what-is-typescript.md) | > 1 Block |
| 4.  | [The Angular CLI](/units/1-introduction-to-Angular/iv-the-angular-cli.md)        | > 1 Block |
| 5.  | [Environment Setup](/units/1-introduction-to-Angular/v-environment-setup.md)     | > 1 Block |

#### Angular Component and Binding

|     | Lesson                                                                                            | Duration  | Dependencies         |
| --- | ------------------------------------------------------------------------------------------------- | --------- | -------------------- |
| 1.  | [Learning Objectives](/units/2-angular-components-and-bindings/i-learning-objectives.md)          | > 1 Block |                      |
| 2.  | [Components Overview](/units/2-angular-components-and-bindings/ii-components-overview.md)         | 1 Block   |                      |
| 3.  | [E2E Testing](/units/2-angular-components-and-bindings/iii-protractor-testing.md)                 | 1 Block   | Protractor           |
| 4.  | [My First Component](/units/2-angular-components-and-bindings/iv-my-first-component.md)           | 1 block   |
| 4.  | [Binding Overview](/units/2-angular-components-and-bindings/v-binding-overview.md)                | 2 Blocks  | Mocks, Stubs & Spies |
| 5.  | [Testing Your Components](/units/2-angular-components-and-bindings/iv-testing-your-components.md) | > 1 Block |
