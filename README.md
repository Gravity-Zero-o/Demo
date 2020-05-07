#include<iostream>
using namespace std;
class Time
{
private:
	int hour, minute, second;
	static int baseHour, baseMinute, baseSecond;
	static int timeToSecond(Time t) {

		return  t.hour * 3600 + t.minute * 60 + t.second;
	}
public:
	Time(int a = 0, int b = 0, int c = 0) {
		hour = a;
		minute = b;
		second = c;
	}
	static int timeBaseDiffence(Time t)
	{
		int a1, a2, a3;
		a1 = t.hour - baseHour;
		a2 = t.minute - baseMinute;
		a3 = t.second = baseSecond;
		return 3600 * a1 + 60 * a2 + a3;

	}
	friend int diffence(Time t1, Time t2)
	{
		
		return  ( Time::timeToSecond(t1) - Time::timeToSecond(t2));
		
	}
	void show() { cout << hour << ":" << minute << ":" << second << endl; }
};
int Time::baseHour = 1;
int Time::baseMinute = 10;
int Time::baseSecond = 10;

int main()
{
	Time t1(1, 11, 2), t2(1, 12, 50);
	t1.show(); t2.show(); 
	cout << Time::timeBaseDiffence(t1) << endl;
	cout << Time::timeBaseDiffence(t2) << endl;
	cout << diffence(t1, t2);
	return 0;
}
