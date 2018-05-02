# Implementation of listeners and event handlers

### Java
When using the platform JavaFX to design applications, event handlers and listeners can be added to UI elements via methods on the UI objects. The methods can either add or use a convenience method to set a handler or listener on the object. These methods take [lambda expressions](lambdas.md) or anonymous inner classes implementing an handler/listener interface as parameters.

```java
public class FinalProjectJavaFX extends Application {
    
	@Override
	public void start(Stage primaryStage) {
        
		StackPane root = new StackPane();
        
		//change listener added to stackpane, anonymous inner class passed as parameter
		root.widthProperty().addListener(new ChangeListener<Number>() {
			@Override public void changed(ObservableValue<? extends Number> observableValue, Number oldSceneWidth, Number newSceneWidth) {
				System.out.println("Width changed");
			} 
		});
        
		Button btn = new Button();
		btn.setText("Say 'Hello World'");
        
		//event handler set using convenience method, lambda function passed as parameter
		btn.setOnAction((ActionEvent event) -> {
			System.out.println("Hello World!");
		});
        
		root.getChildren().add(btn);
        
		Scene scene = new Scene(root, 300, 250);
        
		primaryStage.setScene(scene);
		primaryStage.show();
	}
    
	public static void main(String[] args) {
		launch(args);
	}
    
}
```

### Kotlin
Implementing listeners and handlers in Kotlin is similar to JavaFX. Functions on UI elements can set a listener to the object. The function is passed an anonymous class or a lambda expression which includes code (a callback function) to handle the event caught by the listener.

```kotlin
//handling an event with an anonymous class
button.setOnClickListener(object: View.OnClickListener { //sets listener to button object
	override fun onClick(v: View?) { //callback function which handles event
		statusText.text = "Clicked"
	}
}
```
```kotlin
//handling an event with a lambda function
button.setOnClickListener{
	statusText.text = "Clicked"
}
```

[Home](../README.md)