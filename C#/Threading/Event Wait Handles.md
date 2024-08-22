## Overview
- Event wait handles are used for [[signaling]].

## Types of Event Wait Handles
Both classes inherit from the `EventWaitHandle` class.
##### AutoResetEvent
- https://www.albahari.com/threading/part2.aspx#_AutoResetEvent
- Automatically calls the `Reset()` method after the `Set()` method is called
##### ManualResetEvent
- https://www.albahari.com/threading/part2.aspx#_ManualResetEvent
- Need to manually call the `Reset()` method after the `Set()` method is called.
