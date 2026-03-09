Edits are the form of actions taken by the user, but represented as instance of a class extending
````PNEdit````. Examples of this can be the action "Creating a decision node" which is represented
by ````AddNodeEdit````, or "Adding a link from node A to node B" which is represented by
````AddLinkEdit````.

This allows to build a history of the actions made by the user, so he can undo actions with
````Ctrl + Z```` and redo them with ````Ctrl + Y````. This can be seen in practice in the following
video.

<video width="320" height="240" controls>
  <source src="https://github.com/OpenMarkov/wiki/raw/refs/heads/main/resources/edits/basic_edit_in_use.mp4" type="video/mp4">
</video>


[![Alt Text for Video](https://www.alleycat.org/wp-content/uploads/2019/03/FELV-cat.jpg)](https://github.com/OpenMarkov/wiki/raw/refs/heads/main/resources/edits/basic_edit_in_use.mp4)

To make an edit to take place, you only need to find the right edit, create an instance of it, and
then calling the ````execute```` method. For example, this would add a chance node in the network.

```java
new AddNodeEdit(probNet, variable, NodeType.CHANCE).executeEdit();
```

When executing the edit, a few underlying actions take place: First the edit will check it won't
violate any constraint via the ``PNEdit#checkConstraintsWillBeMet``[^1], and then it will call
``PNEdit#doEdit()`` for the action to take place[^2]. Once the action has been done, it
gets added[^3] to the Edits History to allow the user to use ````Ctrl + Z````.

[^1]: _If ``PNEdit#checkConstraintsWillBeMet()`` throws a ``ConstraintViolatedException``, the 
execution will be halted_.

[^2]: _If ``PNEdit#doEdit()`` throws a ``DoEditException``, the execution will be halted_.

[^3]: _Adding an edit to the history removes all of the edits that can be currently redone by using
````Ctrl + Y````._



## Events
When adding a PNEditListener to the ProbNet's listener (via
```probNet.getPNESupport().addListener(*Your PNEditListener*)```), said listener will be able to
react to certain events triggered by the edit. For this, the listener must implement the methods
that match the events it wants to listen to.

The list of events is the following:

- ``beforeEditExecutes(PNEdit)``: Happens before trying to execute the edit.
- ``afterEditExecutes(PNEdit)``: Happens after successfully executing the edit.
- ``onEditViolatesConstraints(PNEdit, ConstraintViolatedException)``: Happens before trying to
  execute the edit, and it means a constraint would be violated if this edit was to be executed.
  <br>If this event happens, then the execution of the edit won't take place.
  <br>If this event happens, then it will be impossible to reach the events ``beforeEditExecutes``,
  ``afterEditExecutes``, and ``onEditFailed``.
- ``onEditFailed(PNEdit, DoEditException)``: When an edit was tried to be executed, but the
  ```PNEdit#doEdit()``` operation threw a ```DoEditException```.
  <br>If this event happens, then the edit might have taken place if the implementation of the edit
  was badly implemented.
  <br>If this event happens, then it will be impossible to reach the event ``afterEditExecutes``,
  but the event ``beforeEditExecutes`` is guaranteed to have happened.
- ``afterUndoingEdit(PNEdit edit)``: Happens after undoing edit.
  <br>The undo operation shall not fail, and therefore there is no ``beforeUndoingEdit(PNEdit edit)``
  event.
- ``afterRedoingEdit(PNEdit edit)``: Happens after redoing edit.
  <br>The redo operation shall not fail, and therefore there is no ``beforeRedoingEdit(PNEdit edit)``
  event.
