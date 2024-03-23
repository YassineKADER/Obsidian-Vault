# Application:

Is a single instance which creates the environment for you. It creates a `primaryStage` and launches the javafx ui thread.

# Stage:

Is a window. You can have as many `Stages` as you want. `Application`provides you with a `Stage` in the `start` method, which has some special properties, compared to manually created `Stages`.

# Scene:

Every `Stage` can hold exactly one `Scene` at a time. `Scenes` can be swapped out, but is discouraged to do so. It is better to just swap out the `root`of the `Scene`.

# Parent:

A simple `Node` that can hold other `Nodes` as children. Every `Scene`needs exactly one `Parent` as the `root`.

# FXML Files:

A single FXML file just describes the hierarchy of a `Node` (the root node that you get of the`FXMLLoader`) and it's children. You can have a FXML file describe a single `Button` or the root `Node` of a `Scene` and all its children. FXML is not bound to a single `Scene`.

If you want you can have the FXML file describe a `Label` and a `Textfield` inside a `GridPane` (like a standart input formular) and load it every time you need this arrangement somewhere (as often as you want, even in a single Scene).

# Node:

A `Node` is the `abstract` superclass of the graphical elements the scenegraph are "made of".

Some examples of classes inheriting from `Node`:

- `TextField`
- `AnchorPane`
- `Canvas`
- `Group`
- `VBox`
- `Button`
- `Label`

Before you understand what a `**Node**` is, it is also important to first of all understand what a `**Scene Graph**` is in `JavaFX`.

JavaFX applications consist of a `**Stage**` and a `**Scene**` or several scenes. The stage being the top-level container of your application. The Scene(s) on the other hand, contains all the content  
(User Interface elements) of your application (if your application has only one "page") or the content of one of the "pages" of your application, and exists in/on a stage. (To be clear here, by page I mean what the user interacts with, for instance, a login page.)  

`**The Scene Graph is a graphical illustration of how all the stuff in your scene are laid out. This graph is represented in the form of a tree data structure.**`

`**A Node is an item in the scene graph.**`

I think this image explains this clearly.

![[Untitled 29.png|Untitled 29.png]]