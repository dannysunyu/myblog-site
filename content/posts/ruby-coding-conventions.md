---
title: "Some useful Ruby Coding Conventions"
date: 2022-04-19T08:46:35+08:00
draft: true
---

## 1. Implicit return values
You don't actually need the `return` keyword in a method. The value of the last expression evaluated
within a method automatically becomes that method's return value.

So, instead of
```ruby
def mileage(miles_driven, gas_used)
  return miles_driven / gas_used
end
```
You can actually write
```ruby
def mileage(miles_driven, gas_used)
  miles_driven / gas_used
end
```

