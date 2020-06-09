# Pausing execution

* Suggested way (in async context): `await Task.Delay(milliseconds);`.
* `Thread.Sleep(milliseconds);` is generally agreed to be a bad practice.

## Read more:

* https://stackoverflow.com/questions/8815895/why-is-thread-sleep-so-harmful
* http://www.albahari.com/threading/part2.aspx#_Signaling_with_Event_Wait_Handles