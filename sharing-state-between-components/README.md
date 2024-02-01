# ![[tktk Module Name] - tktk Microlesson Name](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

This is the big microlesson of this module. 

There should be a child component that is a form with its own internal state and controlled form pattern going on.

It will submit its state upwards into a stateful parent component.

That parent component probably has a list of objects that lives in state and that list gets modified by the child functions/components. The code-along-with-me section should get through ADDING a new item to the list and seeing that item get rendered into a sibling display component to the form.

Parent stateful container component
Child form new object component.
Child display objects list component.

Discuss the timing of what should happen in that onSubmit event listener since the form values should probably get cleared and the state of the child gets updated in addition to calling the function that will update the state of the parent.

A challenge you-do section of this app would be then having a delete button on each individual item that removes it.