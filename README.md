# CT548 04/15/2020 Assignment 4
There are four packages for different purpose.

1. assignment4.controller: It provides the overall control of the model and view.

2. assignment4.model: It used to store the Json data for the 5 items. The strategy and abstract factory related classes are also under here.
3. assignment4.runtime: The main program and the Container class are under the package
4. assignment4.view: There are 5 windows under this package.

-----

### DOCUMENTATION

#### Describe the reasoning behind your design choices in terms of design patterns, classes, and user interaction.

1. **Abstract Factory Design Pattern:**
   
   The FactoryProvider only provides the idea of "Produce" something, so it can be defined as an interface or an abstract class. 

   Consider that the Factory pattern only produce one-type product. Here I use "Abstract" Factory Pattern hence there are two items to produce: Films and TvSeries. Because these two class's properties are totally same. 
   
   So I created the AbstractFactory.class acts as the Parent, it has all the common properties defined. The children: Films and TvSeries inherit all the properties by extending the AbstractFactory.class.
   
2. **Strategy Design Pattern:**
   It provides an interface or a method to present the same behavior. Usually needs 2 or more classes have the same action in a group of classes. 
   
   In our case, obviously "list by year" and "list by genre" takes the same action--"Sorting". Therefore, I created a Strategy interface defining an action:"sort" and the concrete strategy classes: Films and Genres implementing the Strategy interface to realize the sorting action. 
   
   Context.class provides an index for the external classes, so the user can  determine to choose which method to sort by click the "ListByYear" or "ListByGenre" button, system will dynamically allocate the corresponding sorting method in the runtime. 
   
3. **MVC(Model-View_controller):**  

   MVC supports rapid and parallel development. We can create multiple views for a model. If we want to change something like adding some colors we only need to change the view part without touching the models which is easily impact the whole architecture.

   **Model:** This is the part we use to store the read in Json data(Films, Tvseries etc) that already formatted to object or a group of objects. Whenever changes happen in the model, it will notify the observers automatically.

   **View:**  It creates an interface to show the actual output to the user. The user can operate in this level randomly without touching the data  in the Model.   This is more safe to protect the whole coding architecture. 

   But actually the view is nothing itself. Only by collecting the user's action like click the button  it sends the command to the controller to handle and then controller allocate related data and give feedback to the view that represents to the user. In our case, the model also tells the view what to present.

   **Controller:**  The controller acts as a bridge between the model and the view. Just as the brain, it receives commands from the user via the View and handles the events. It fetches the data from the model and after a set of analysis and operation. It gives final feedback to the user by presenting appropriate views. 

#### Provide a small guide for the using the system (i.e. help for the user)

1. When running the system, the main window about the video catalogue will prompt and show you all the system details: 4 buttons, 5 films title's with hyperlink followed by its published year and genre's name. 
   
2. If you click the "Switch Profile" button. A sub-window will prompt and show you 4 selection buttons.
    If you choose any one of them, then another new window will jump out and tell you the data you selected  has been recorded successfully and the main window left corner will update the file you selected accordingly.

3. When a "Add new" button clicked. A new window will show up in which you can enter the details
   as you like. When the "Save" button clicked, another window will show you the details that
   you just entered. These data will be stored in the memory.

4. For the "List by Year" and "List by Genre" button,when clicked, a new window will show up 
   with the details that sorting by year or the genre name accordingly.

5. The 5 hyperlink will redirect to the "Add Item" window with it's own data appearing on the screen.

#### Discuss at least one more way in which the system can be extended.
​	Extention Principle: Open for extension but close for change.

1. Extention1: Abstract Factory Design Pattern:

   It's benefit is when a new class comes in, it can directly use "createItem()" to produce a new type product. No need to re-write or edit on the original codes.

2. Extention2: Strategy Design Pattern:
   It's benefit is providing an additional interface for better extension for future changes. When new class added, we only need to write its own sorting method by implementing the Strategy interface. There's no need to modify the original codes. We just need to use the "Context" and it will dynamically find related sorting method.