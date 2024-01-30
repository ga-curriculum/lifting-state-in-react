# ![[tktk Module Name] - tktk Microlesson Name](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

This is the big microlesson of this module. 

There should be a child component that is a form with its own internal state and controlled form pattern going on.

It will submit its state upwards into a stateful parent component.

That parent component probably has a list of objects that lives in state and that list gets modified by the child functions/components. The code-along-with-me section should get through ADDING a new item to the liste and seeing that item get rendered into a sibling display component to the form.

Parent stateful container component
Child form new object component.
Child display objects list component.
Grandchild(?) component for each individual list item, perhaps. This is a design decision you could discuss the pros and cons of, whether to have an intermediate layer like a ItemsListComponent that then renders individual children ItemComponents, or just go straight to putting the children data in a direct child of the main parent component. Up to you!

Discuss the timing of what should happen in that onSubmit event listener since the form values should probably get cleared and the state of the child gets updated in addition to calling the function that will update the state of the parent.

A challenge you-do section of this app would be then having a delete button on each individual item that removes it.

You could also do a mega challenge filter of the items, but that seems best saved for a lab.