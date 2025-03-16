+++
title= "Day 04"
date= '2025-03-14'
draft= 'false'
tags= ["", "Dates", "Times", "Regular Expressions"]
categories= ["Days_of_Back"]
+++

# Becoming Lazy

## 1. Coding of the day : **None**

## 2. JS of the day : **Dates/Times and Regular Expressions**

### Dates and Times :

- JavaScript does not have a date data type. However, you can use the Date object and its methods to work with dates and times in your applications. The Date object has a large number of methods for setting, getting, and manipulating dates. It does not have any properties.
- The parameters in the preceding syntax can be any of the following:

  - Nothing: creates today's date and time. For example, `today = new Date();`.
  - A string representing a date, in many different forms. The exact forms supported differ among engines, but the following form is always supported: `YYYY-MM-DDTHH:mm:ss.sssZ`.
  - A set of integer values for year, month, and day. For example, `xmas95 = new Date(1995, 11, 25)`.
  - A set of integer values for year, month, day, hour, minute, and seconds. For example, `xmas95 = new Date(1995, 11, 25, 9, 30, 0);`.

- Methods of the Date object, The Date object methods for handling dates and times fall into these broad categories:

  - "set" methods, for setting date and time values in Date objects.

  ```js
  const date = new Date();
  date.setFullYear(2025); // Set year to 2025
  date.setMonth(11); // Set month to December (0-based index)
  date.setDate(25); // Set day to 25
  date.setHours(10); // Set hours to 10 AM
  date.setMinutes(30); // Set minutes to 30
  date.setSeconds(45); // Set seconds to 45
  ```

  - "get" methods, for getting date and time values from Date objects.

  ```js
  const date = new Date("2024-03-15T12:45:00");
  console.log(date.getFullYear()); // 2024
  console.log(date.getMonth()); // 2 (March, since months are 0-based)
  console.log(date.getDate()); // 15
  console.log(date.getDay()); // 5 (Friday)
  console.log(date.getHours()); // 12
  console.log(date.getMinutes()); // 45
  console.log(date.getSeconds()); // 0
  console.log(date.getMilliseconds()); // 0
  console.log(date.getTime()); // Timestamp in milliseconds
  ```

  - "to" methods, for returning string values from Date objects.
  - parse and UTC methods, for parsing Date strings.

### Regular Expressions :

- Regular expressions are patterns used to match character combinations in strings. In JavaScript, regular expressions are also **objects**.

Queries : [Send mail](ajmalakram152@gmail.com)
