```Java
public class MyDate {
private int year;
private int day;
private int month;
private String[] MONTH = { "jan", "feb", "mar", "apr", "may", "jun", "jul", "aug", "sep", "oct", "nov", "dec" };
private String[] DAY = { "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday" };
private int[] Days_In_Months = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
```

```Java
public boolean IsLeapYear(int year) {
	return (this.year % 4 == 0 || this.year % 400 == 0);
}

public MyDate(int day, int month, int year) {
	if(IsValid(day,month,year)) {
		this.day = day;
		this.month = month;
		this.year = year;
	}
}

public boolean IsValid(int day, int month, int year) {
	return (year<9999 && year>0 && month>0 && month<=12 && day>0 && day<=Days_In_Months[month-1]);
}

public int get_day_of_week(int day, int month, int year) {
	year -= ((month<3) ? 1 : 0);
	return ((year+year/4-year/100+year/400+month-1+day)%7);
}

@Override
public String toString() {
	return "MyDate [year=" + year + ", day=" + day + ", month=" + month + "]";
}

public MyDate nextDay() {
	MyDate obj = new MyDate(this.day, this.month, this.year);
	obj.day++;
	if(obj.day>obj.Days_In_Months[obj.month-1]) {
		obj.day=1;
		obj.month++;
		if(obj.month<=12) {
			obj.year++;
		}
	}
	return obj;
}

public MyDate nextMonth() {
	MyDate obj = new MyDate(this.day, this.month, this.year);
	obj.month++;
	if(obj.month>12) {
		obj.month=1;
		obj.year++;
	}

	return obj;
}

public MyDate nextYear() {
	MyDate obj = new MyDate(this.day, this.month, this.year);
	obj.year++;
	return obj;
}

public MyDate prevsDay() {
	MyDate obj = new MyDate(this.day, this.month, this.year);
	obj.day--;
	if(obj.day==0) {
		obj.month--;
		if(obj.month==0) {
			obj.month=12;
			obj.year--;
		}
		obj.day=obj.Days_In_Months[obj.month-1];
	}
	return obj;
}

public MyDate prevsMonth() {
	MyDate obj = new MyDate(this.day, this.month, this.year);
	obj.month--;
	if(obj.month==0) {
		obj.month=12;
		obj.year--;
	}
	return obj;
}

public MyDate prevsYear() {
	MyDate obj = new MyDate(this.day, this.month, this.year);
	obj.year--;
	return obj;
}
}
```