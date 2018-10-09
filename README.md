# Simple RecyclerView Touch Listener
## Getting Started
This is a library that abstracts, and completely hide, the GestureDetector part of an recyclerview click, and press, events implementation. Leaving to the developer only the task of implementing what happens whe such events occurs.

## Pre-requesites
To be able of testing and implementig this library, the developer should have a working recyclerview list with some data on it.
## Adding to your project
Lets start by adding a corresponding repository in your _root_ `build.gradle` file. (prefer at the end of all other)
```
	allprojects {
		repositories {
			...
			**maven { url 'https://jitpack.io' }**
		}
	}
 ```
The next task is to add the dependecy to your _app_ `build.gradle` file.
```
	dependencies {
          ...
	        implementation 'com.github.horaciocome1:simple-recyclerview-touch-listener:0.1.0'
	}
Now you ready to go. Except that you should _**sync your project**_ first.

```
## How to use
Using this library consists of creating an object "listener", and passing it to the addOnItemTouchListener() Recyclerview method.
```
// creating an instance of the object by passing the context, respective recyclerview, and an implementation of the callbacks
SimpleRecyclerViewOnItemTouchListener listener = new SimpleRecyclerViewOnItemTouchListener(this
                , mRecyclerView, new SimpleOnItemTouchListener() {
                
            @Override
            public void onItemClick(View view, int i) {
                // what to do when it is just a simple tap up on the list item
                Toast.makeText(view.getContext(), "Normal click: " + i, Toast.LENGTH_SHORT).show();
            }
    
            @Override
            public void onItemDoubleClick(View view, int i) {
                // what to do when it is about two quickly performed taps on the list item
                Toast.makeText(view.getContext(), "Double click: " + i, Toast.LENGTH_SHORT).show();
            }
    
            @Override
            public void onItemLongPress(View view, int i) {
                // what to do when the user press and hold the list item
                Toast.makeText(view.getContext(), "Long press: " + i, Toast.LENGTH_SHORT).show();
            }
            
        }));
  
  // adding the listener to its recyclerview
  mRecyclerView.addOnItemTouchListener(listener);
```
## How to contribute
I am open to suggestions of any kind.
Please be expressive!