```Java
package exMyClass;

public class Clock {
	private int hour;
	private int minutes;
	private int seconds;

	public Clock() {
		hour = 12;
		minutes = 0;
		seconds = 0;
	}

	public Clock(int hour, int minutes, int secondes) {
		if (hour >= 0 && minutes >= 0 && secondes >= 0) {
			this.hour = hour;
			this.minutes = minutes;
			this.seconds = secondes;
			this.checkTime(this);
		} else {
			System.out.println("enter a valid clock");
		}
	}

	public Clock(int seconds) {
		if(seconds>=0) {
			this.seconds = seconds;
			checkTime(this);
		}
		else System.out.println("enter a valid time clock");
	}
	
	public void setClock(int seconds) {
		this.seconds = seconds;
		this.hour = 0;
		this.minutes = 0;
		checkTime(this);
	}

	public int getSeconds() {
		return this.seconds;
	}
	
	public int getHours() {
		return this.hour;
	}
	
	public int getMinutes() {
		return this.minutes;
	}
	
	//setters
	
	public void setMinutes(int minutes) {
		if(minutes>0)this.minutes = minutes;
		checkTime(this);
	}
	
	public void setHours(int hours) {
		if(hours>0)this.hour = hours;
		checkTime(this);
	}
	
	public void setSeconds(int seconds) {
		if(seconds>0)this.seconds = seconds;
		checkTime(this);
	}
	
	public void tick() {
		this.seconds++;
		checkTime(this);
	}
	
	public void addClock(Clock addedclock) {
		this.hour += addedclock.hour;
		this.minutes += addedclock.minutes;
		this.seconds += addedclock.seconds;
		checkTime(this);
	}
	
	public void tickDown() {
		if(hour>0 || minutes>0 || seconds>0) {
			seconds-=1;
			if(seconds<0) {
				minutes--;
				seconds+=60;
				if(minutes<0) {
					minutes+=60;
					hour--;
				}
			}
		}
	}
	
	public void subClock(Clock obj) {
		this.hour -= obj.hour;
		this.minutes -= obj.minutes;
		this.seconds -= obj.seconds;
		
		
	}
	
	private void checkTime(Clock obj) {
		this.hour = obj.hour;
		this.minutes = obj.minutes;
		this.seconds = obj.seconds;
		while (this.seconds >= 60) {
			this.minutes++;
			this.seconds -= 60;
		}
		while (this.minutes >= 60) {
			this.hour++;
			this.minutes -= 60;
		}
		while (this.hour >= 24) {
			this.hour -= 24;
		}
	}
	
	

	@Override
	public String toString() {
		return String.format("%02d", hour) + ":"+ String.format("%02d", minutes)+":" + String.format("%02d", seconds);
	}

}
```