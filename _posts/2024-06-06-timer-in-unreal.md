---
title: Using C++ Timers in Unreal Engine
author: chris
date: 2024-06-06 00:34:00 +0100
categories: [Other, Teaching]
tags: [quick tips, unreal engine]
pin: false
image:
  path: /assets/img/posts/timer.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: Marty and Doc confused about how to use timers in Unreal Engine.
---


The most straightforward way to use timers in C++ is to declare a `UFUNCTION` and a `FTimerHandle` in your class


```cpp
UFUNCTION()
void HandleTimerExpired();

FTimerHandle MyHandle;
```

and starting the timer with the registered callback function from anywhere in your code, like so:
```cpp
GetWorld()->GetTimerManager().SetTimer(MyHandle, this, &ThisClass::HandleTimerExpired, Seconds, bLoop);
```


In a lot of cases the above example is already getting the job done, but there is a big limitation: The specified callback function must be a **void function with no input parameters**.

So how does one call a function that has **input parameters** via a timer?

```cpp
UFUNCTION()
void HandleTimerExpired(bool bInputFlag, int32 InputValue);
```

In that case we can create a `FTimerDelegate` as UObject-based member function delegate and pass our parameters directly when creating the delegate. In the `SetTimer` call we now use our `FTimerDelegate`:

```cpp
FTimerDelegate MyDelegate = FTimerDelegate::CreateUObject(this, &ThisClass::HandleTimerExpired, true, 10);

GetWorld()->GetTimerManager().SetTimer(MyHandle, MyDelegate, Seconds, bLoop);
```

So far so good that still leave the question of how to call a function with **return type** via timer? 

```cpp
UFUNCTION()
bool TryHandleTimerExpired();
```

 `FTimerDelegate` doesn't allow a return type, but we can work around this limitation with the help of a lambda functions. The general syntax for lambda functions in C++ follows the pattern `[ captures ] ( params ) { body }` ---check [cpp reference](https://en.cppreference.com/w/cpp/language/lambda) to learn more.

Here is a simple example of creating a `FTimerDelegate` from a lambda function that wraps our callback function:


```cpp
FTimerDelegate MyDelegate = FTimerDelegate::CreateLambda( [this] ()
  {
      if (TryHandleTimerExpired()) 
      {
        // Do even more stuff if function returns true.
      }
  });

GetWorld()->GetTimerManager().SetTimer(MyHandle, MyDelegate, Seconds, bLoop);

```

There are even more ways to create a `FTimerDelegate` but those three simple examples are covering the most common use cases already.


Don't forget to clear your timer handle during `EndPlay` to not leave any timers running if the object gets destroyed: 
```cpp
GetWorld()->GetTimerManager().ClearTimer(MyHandle);
```



