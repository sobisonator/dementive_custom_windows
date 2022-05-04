This is an example mod that shows how to make and call custom windows of any type with events.

There are two buttons that will open the two example custom windows on the top of the Trade View.

In Imperator there are event types, one of those event types is major_country_event. This event type is NOT used in the vanilla game.
However it does have an empty gui window that can be called by triggering an event with the major_country_event type.

So basically you can open a window with events and in those events you set a variable in the immediate that will determine what window to show.
You can then check for this variable with a scripted gui in the major_country_event section of the eventwindow.gui file.
So each window can be different and can have things inside of it that generated in the immediate field because they open with an event.
This makes is so:
	1. Console commands are not the only way to open a custom window
	2. You don't need to use on_actions to fill the contents of a custom window because the event immediate and options fields do it for you.
	3. The performance impact of making a custom window is made negligible by this system compared to other methods.

Im going to list out some steps that you can take to adapt the example I've made.

	1. Open the eventwindow.gui and scroll down to the 2nd window named "major_event_window". This is where your custom windows will go.
	2. Make a event that sets a variable in the immediate this for example: "window_1". Also remove the variable when the option is clicked.
	3. Make a scripted gui that checks for that variable in the is_valid field.
	4. Add that scripted gui to the top of a container inside the main container in eventwindow.gui
	5. Make the contents of your new window whatever you want, this can be done for as many windows as you want.
	6. Open your window with the event, there is a million ways to trigger an event. I did it with a button in this example but you can do anything.

There are some small bugs that I know of with the custom windows:
	1. Opening the window will pause the game because it is literally an event.

	2. Using the escape key will not close the window, again because that's how events work. However, it works with BUI because events can be closed with enter in BUI so there is a way to fix it.

	3. The horizontal size can't be changed for different windows with the way I have it setup(Vertical size can be though). Maybe someone who know more about GUI can fix this but I can't find a way. This is because the close button is the event option and there cannot be duplicates of the event option code in the gui file or it won't show up so the close button has to be outside of the individual custom window containers.
	
	4. You can't have two custom windows open at once. Don't try it. I've made triggers specifically so the player isn't able to make this happen.