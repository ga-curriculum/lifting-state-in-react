# ![[tktk Module Name] - Concepts](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

CREATOR GUIDANCE

Describe the problem of trying to pass data UPWARDS from a child component to a parent component, particularly a child form that wants to change state in its parent. You could also include a three component diagram of A. shared parent component
B. child form component
C. child presentational component that gets updated by the sibling form

This is the time to use and explain the term unidirectional data flow, and that it's a good thing for react over all, but means we need a pattern that allows children to update parents and siblings. Data can't pass from child to parent directly, nor can it pass from sibling to sibling.

The solution: a function! Don't overcomplicate it: all we're doing is sending a function down as a prop, and using that function to update state. The end.