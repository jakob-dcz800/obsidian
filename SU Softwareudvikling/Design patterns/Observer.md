# Observer pattern
Reduces the amount of time an object has to pull data from another. Observers push data instead.
Allows the detection of changes to objects.

Decouple changes of values from something that is interested in the changes.
Examples: 
	• Arrival of a new order 
	• Log on to a new user

We're interested in our state changing.
Subject notifies the observer. 
Subject is active, observer is passive.

This is part of [[Dependency inversion]] design principle.

Idea: 
	• The (observed) subject allows the logging on and off of observers. 
	• Observers are waiting passively for notification by the subject. 
	• The subject has a notification mechanism and informs all registered observers that an event has occurred. 
	• The observer can obtain information about the subject after the notification of an event, which has occurred, thus completing the observation.

![[Pasted image 20250310113534.png]]

![[Pasted image 20250310113714.png]]

![[Pasted image 20250310113731.png]]

## Example

```csharp
namespace EventsObserver;  

public delegate void TemperatureProcessor(
	TemperatureSensor sensor, double  
	changedTemp);
	
public class TemperatureSensor {
	private double _Temperature=20.0;  

	public double Temperature {
		get {return _Temperature; }  
		set {_Temperature=value; OnChange();}
	}

	public event TemperatureProcessor? TemperatureChanged;  
	
	public void OnChange() {
		if(TemperatureChanged!=null)  
			TemperatureChanged(this, Temperature);
	}  
}

public class TemperatureDisplay {
	public int id {get; set; }  
	public TemperatureDisplay(int TempID) {  
		id=TempID;  
	}
	
	public void PrintTemperature(double temp) {  
		System.Console.WriteLine("Display #{0} shows temperature {1}", id, temp);  
	}
	  
	public void TemperatureChange(object sub, double changedTemp) {  
		PrintTemperature(changedTemp);  
	}  
}

public class MyApp {  
	public static void Main() {  
		TemperatureSensor tempSensor= new TemperatureSensor();  
		TemperatureDisplay tempDisp1=new TemperatureDisplay(1); 
		TemperatureDisplay tempDisp2=new TemperatureDisplay(2); 
		
		// Connecting events of sensor to processors  
		tempSensor.TemperatureChanged+= new  
		TemperatureProcessor(tempDisp1.TemperatureChange);  
		tempSensor.TemperatureChanged+= new  
		TemperatureProcessor(tempDisp2.TemperatureChange);
		  
		// change the temperatures for rising temperature  
		tempSensor.Temperature=12;  
		tempSensor.Temperature=13;  
		tempSensor.Temperature=14;  
	}  
}
```
