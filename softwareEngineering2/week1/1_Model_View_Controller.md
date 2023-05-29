# Model View Controller
![[Pasted image 20230529164845.png]]
* Is used to separate the ways that information is stored internally from the way that it is presented to users.
## Model
* The `Model` contains and manages the internal representation of the data as well as the rules as to how it can be modified. This is usually an interface to a database.
* The nodes of a model should all be on the same problem level and there must be a 1 to 1 correspondence between the model and how it is perceived by the owner.
## View
* The `View` allows for different representations of a subset of the data, eg using dates in the model to create a timeline or a table.
* It needs to know of the terminology of the model and have a good understanding about it.
## Controller
* The `Controller` is what the user interacts with and passes on commands to the view.
* It should never supplement the views eg by connecting nodes of the model.
* Furthermore, it should never send direct user inputs to the view, it should be possible to send messages to the view for the semantics of any given series of user inputs.
## Editors
* Not necessarily part of the MVC model however it is a specific view that provides a controller that allows the user to modify the information presented by the view.