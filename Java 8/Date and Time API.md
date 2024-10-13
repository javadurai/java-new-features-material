# Date and Time API

The **Date and Time API** in Java, introduced in Java 8, addresses the deficiencies of the old java.util.Date and java.util.Calendar classes by providing a much more comprehensive and flexible way to handle dates and times. The new API is located in the java.time package and is built around the ISO-8601 calendar system, which is the modern international standard.

The key classes in the java.time package are:

1. **LocalDate:** Represents a date without a time zone (e.g., 2024-10-13).
1. **LocalTime:** Represents a time without a date and without a time zone (e.g., 10:15:30).
1. **LocalDateTime:** Represents both date and time without a time zone (e.g., 2024-10-13T10:15:30).
1. **ZonedDateTime:** Represents both date and time with a time zone (e.g., 2024-10-13T10:15:30+01:00[Europe/Paris]).
1. **Instant:** Represents a timestamp (date and time) in UTC, useful for machine time (e.g., 2024-10-13T10:15:30Z).
1. **Period and Duration:** Represents amounts of time, where Period deals with date-based values (e.g., "2 years, 3 months, and 4 days"), and Duration deals with time-based values (e.g., "5 hours, 15 minutes").

## 1. LocalDate

LocalDate is used to represent a date without a time and without a time zone.

### Example:

```java
import java.time.LocalDate;

public class DateExample {
    public static void main(String[] args) {
        LocalDate today = LocalDate.now();  // Current date
        System.out.println("Today's date: " + today);

        LocalDate specificDate = LocalDate.of(2020, 12, 25);  // A specific date
        System.out.println("Specific date: " + specificDate);

        LocalDate parsedDate = LocalDate.parse("2024-10-13");  // Parsing a date from a string
        System.out.println("Parsed date: " + parsedDate);

        // Adding days to a date
        LocalDate futureDate = today.plusDays(10);
        System.out.println("Date after 10 days: " + futureDate);
    }
}
```

### Output:

```yaml
Today's date: 2024-10-13
Specific date: 2020-12-25
Parsed date: 2024-10-13
Date after 10 days: 2024-10-23
```

## 2. LocalTime

LocalTime is used to represent a time without a date and without a time zone.

### Example:

```java
import java.time.LocalTime;

public class TimeExample {
    public static void main(String[] args) {
        LocalTime now = LocalTime.now();  // Current time
        System.out.println("Current time: " + now);

        LocalTime specificTime = LocalTime.of(10, 15, 30);  // A specific time
        System.out.println("Specific time: " + specificTime);

        LocalTime parsedTime = LocalTime.parse("09:30:15");  // Parsing time from a string
        System.out.println("Parsed time: " + parsedTime);

        // Adding hours to time
        LocalTime futureTime = now.plusHours(2);
        System.out.println("Time after 2 hours: " + futureTime);
    }
}
```

### Output:

```sql
Current time: 10:15:30
Specific time: 10:15:30
Parsed time: 09:30:15
Time after 2 hours: 12:15:30
```

## 3. LocalDateTime

LocalDateTime is used to represent both date and time, but without a time zone.
Example:

```java
import java.time.LocalDateTime;

public class DateTimeExample {
    public static void main(String[] args) {
        LocalDateTime now = LocalDateTime.now();  // Current date and time
        System.out.println("Current date and time: " + now);

        LocalDateTime specificDateTime = LocalDateTime.of(2024, 10, 13, 10, 15, 30);  // A specific date and time
        System.out.println("Specific date and time: " + specificDateTime);

        LocalDateTime parsedDateTime = LocalDateTime.parse("2024-10-13T10:15:30");  // Parsing from a string
        System.out.println("Parsed date and time: " + parsedDateTime);

        // Adding days and hours to a datetime
        LocalDateTime futureDateTime = now.plusDays(5).plusHours(3);
        System.out.println("Date and time after 5 days and 3 hours: " + futureDateTime);
    }
}
```

### Output:

```sql
Current date and time: 2024-10-13T10:15:30
Specific date and time: 2024-10-13T10:15:30
Parsed date and time: 2024-10-13T10:15:30
Date and time after 5 days and 3 hours: 2024-10-18T13:15:30
```

4. ZonedDateTime

ZonedDateTime is used to represent date and time with a time zone. It combines the features of LocalDateTime and ZoneId.

### Example:

```java
import java.time.ZonedDateTime;
import java.time.ZoneId;

public class ZonedDateTimeExample {
    public static void main(String[] args) {
        ZonedDateTime nowInParis = ZonedDateTime.now(ZoneId.of("Europe/Paris"));  // Current time in Paris
        System.out.println("Current time in Paris: " + nowInParis);

        ZonedDateTime specificZonedDateTime = ZonedDateTime.of(2024, 10, 13, 10, 15, 30, 0, ZoneId.of("Europe/London"));
        System.out.println("Specific ZonedDateTime: " + specificZonedDateTime);
    }
}
```

### Output:

```yaml
Current time in Paris: 2024-10-13T12:15:30+02:00[Europe/Paris]
Specific ZonedDateTime: 2024-10-13T10:15:30+01:00[Europe/London]
```

5. Instant

Instant represents a point on the timeline in UTC (Coordinated Universal Time), useful for timestamps and machine time.

### Example:

```java
import java.time.Instant;

public class InstantExample {
    public static void main(String[] args) {
        Instant timestamp = Instant.now();  // Current timestamp in UTC
        System.out.println("Current timestamp: " + timestamp);

        // Adding seconds to an instant
        Instant futureInstant = timestamp.plusSeconds(3600);  // Add one hour
        System.out.println("Timestamp after one hour: " + futureInstant);
    }
}
```

### Output:

```sql
Current timestamp: 2024-10-13T10:15:30Z
Timestamp after one hour: 2024-10-13T11:15:30Z
```

6. Period and Duration

- **Period:** Represents the amount of time in terms of years, months, and days.
- **Duration:** Represents the amount of time in terms of seconds or nanoseconds.

### Period Example:

```java
import java.time.LocalDate;
import java.time.Period;

public class PeriodExample {
    public static void main(String[] args) {
        LocalDate startDate = LocalDate.of(2020, 1, 1);
        LocalDate endDate = LocalDate.of(2024, 10, 13);

        Period period = Period.between(startDate, endDate);  // Calculate period between two dates
        System.out.println("Period between dates: " + period);
        System.out.println("Years: " + period.getYears() + ", Months: " + period.getMonths() + ", Days: " + period.getDays());
    }
}
```

### Output:

```yaml
Period between dates: P4Y9M12D
Years: 4, Months: 9, Days: 12
```

### Duration Example:

```java
import java.time.Duration;
import java.time.LocalTime;

public class DurationExample {
    public static void main(String[] args) {
        LocalTime startTime = LocalTime.of(10, 15, 30);
        LocalTime endTime = LocalTime.of(12, 45, 0);

        Duration duration = Duration.between(startTime, endTime);  // Calculate duration between two times
        System.out.println("Duration: " + duration);
        System.out.println("Hours: " + duration.toHours() + ", Minutes: " + duration.toMinutes());
    }
}
```

### Output:

```yaml
Duration: PT2H29M30S
Hours: 2, Minutes: 149
```

## Key Benefits of the New Date and Time API:

- **Immutability:** All classes in the java.time package are immutable, meaning their instances cannot be changed. This makes them thread-safe.
- **Clear API:** The new API is much clearer and avoids the confusion caused by the old Date and Calendar classes.
- **Support for Different Time Zones:** Classes like ZonedDateTime provide a robust way to handle different time zones.
- **Easy Parsing and Formatting:** The API provides extensive support for parsing and formatting dates and times using DateTimeFormatter.

---

Here are some advanced challenges with the Java 8 Date and Time API, followed by programs that demonstrate how to solve them.

## Challenge 1: Handling Time Zone Conversion

**Problem:** Convert a ZonedDateTime in one time zone to another time zone.

**Scenario:** You have a meeting scheduled at 2024-10-15 14:30 in Europe/Paris time zone, and you want to know what time it will be in the America/New_York time zone.

### Solution:

```java
import java.time.ZonedDateTime;
import java.time.ZoneId;

public class TimeZoneConversion {
    public static void main(String[] args) {
        // Meeting time in Paris
        ZonedDateTime parisMeetingTime = ZonedDateTime.of(2024, 10, 15, 14, 30, 0, 0, ZoneId.of("Europe/Paris"));
        System.out.println("Meeting time in Paris: " + parisMeetingTime);

        // Convert to New York time zone
        ZonedDateTime newYorkMeetingTime = parisMeetingTime.withZoneSameInstant(ZoneId.of("America/New_York"));
        System.out.println("Meeting time in New York: " + newYorkMeetingTime);
    }
}
```

### Output:

```less
Meeting time in Paris: 2024-10-15T14:30+02:00[Europe/Paris]
Meeting time in New York: 2024-10-15T08:30-04:00[America/New_York]
```

## Challenge 2: Calculating Time Difference Between Two ZonedDateTime Instances

**Problem:** Calculate the difference between two ZonedDateTime instances in hours and minutes.

**Scenario:** Find the time difference between 2024-10-13 10:15:30 in Europe/London and 2024-10-13 20:45:30 in Asia/Tokyo.

### Solution:

```java
import java.time.ZonedDateTime;
import java.time.Duration;
import java.time.ZoneId;

public class TimeDifference {
    public static void main(String[] args) {
        // London time
        ZonedDateTime londonTime = ZonedDateTime.of(2024, 10, 13, 10, 15, 30, 0, ZoneId.of("Europe/London"));

        // Tokyo time
        ZonedDateTime tokyoTime = ZonedDateTime.of(2024, 10, 13, 20, 45, 30, 0, ZoneId.of("Asia/Tokyo"));

        // Calculate the duration between two times
        Duration duration = Duration.between(londonTime, tokyoTime);

        // Output the difference in hours and minutes
        long hours = duration.toHours();
        long minutes = duration.toMinutes() % 60;  // Remaining minutes after hours
        System.out.println("Time difference: " + hours + " hours and " + minutes + " minutes");
    }
}
```

### Output:

```css
Time difference: 8 hours and 30 minutes
```

## Challenge 3: Parsing and Formatting Dates in Custom Patterns

**Problem:** Parse a date string in a custom pattern and then format it to another pattern.

**Scenario:** Parse a date string in the format "15-10-2024 14:30" and convert it into "October 15, 2024 at 02:30 PM".

### Solution:

```java
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class CustomDateParsingFormatting {
    public static void main(String[] args) {
        // Define the input pattern
        DateTimeFormatter inputFormatter = DateTimeFormatter.ofPattern("dd-MM-yyyy HH:mm");

        // Define the output pattern
        DateTimeFormatter outputFormatter = DateTimeFormatter.ofPattern("MMMM dd, yyyy 'at' hh:mm a");

        // Parse the input date
        String inputDate = "15-10-2024 14:30";
        LocalDateTime dateTime = LocalDateTime.parse(inputDate, inputFormatter);

        // Format to the output pattern
        String formattedDate = dateTime.format(outputFormatter);
        System.out.println("Formatted date: " + formattedDate);
    }
}
```

### Output:

```yaml
Formatted date: October 15, 2024 at 02:30 PM
```

## Challenge 4: Handling Daylight Saving Time (DST)

**Problem:** Check if a given date and time falls within Daylight Saving Time in a particular time zone.

**Scenario:** Check if 2024-03-31 02:30 in the Europe/London time zone falls within Daylight Saving Time.

### Solution:

```java
import java.time.ZonedDateTime;
import java.time.ZoneId;

public class DaylightSavingTimeCheck {
    public static void main(String[] args) {
        // Define the date and time in London
        ZonedDateTime dateTime = ZonedDateTime.of(2024, 3, 31, 2, 30, 0, 0, ZoneId.of("Europe/London"));
        System.out.println("Date and time: " + dateTime);

        // Check if it falls within Daylight Saving Time
        boolean isDST = dateTime.getZone().getRules().isDaylightSavings(dateTime.toInstant());
        System.out.println("Is DST: " + isDST);
    }
}
```

### Output:

```yaml
Date and time: 2024-03-31T02:30+01:00[Europe/London]
Is DST: true
```

## Challenge 5: Calculating Age from a Birth Date

**Problem:** Calculate the age of a person based on their birth date.

**Scenario:** Given the birth date 1990-05-15, calculate the person's age on the current date.

### Solution:

```java
import java.time.LocalDate;
import java.time.Period;

public class AgeCalculator {
    public static void main(String[] args) {
        // Birth date
        LocalDate birthDate = LocalDate.of(1990, 5, 15);

        // Current date
        LocalDate currentDate = LocalDate.now();

        // Calculate age
        Period age = Period.between(birthDate, currentDate);
        System.out.println("Age: " + age.getYears() + " years, " + age.getMonths() + " months, and " + age.getDays() + " days");
    }
}
```

### Output (Assuming today's date is 2024-10-13):

```makefile
Age: 34 years, 4 months, and 28 days
```

## Challenge 6: Finding the Next Tuesday from a Given Date

**Problem:** Find the next occurrence of a specific day of the week (e.g., Tuesday) from a given date.

**Scenario:** Starting from 2024-10-13, find the date of the next Tuesday.

### Solution:

```java
import java.time.LocalDate;
import java.time.DayOfWeek;

public class NextTuesdayFinder {
    public static void main(String[] args) {
        LocalDate today = LocalDate.of(2024, 10, 13);
        System.out.println("Today: " + today);

        // Find the next Tuesday
        LocalDate nextTuesday = today.with(java.time.temporal.TemporalAdjusters.next(DayOfWeek.TUESDAY));
        System.out.println("Next Tuesday: " + nextTuesday);
    }
}
```

### Output:

```yaml
Today: 2024-10-13
Next Tuesday: 2024-10-15
```

## Challenge 7: Working with Leap Years

**Problem:** Check if a given year is a leap year and find the number of days in February of that year.

**Scenario:** Check if the year 2024 is a leap year and calculate the number of days in February.

### Solution:

```java
import java.time.Year;
import java.time.Month;
import java.time.LocalDate;

public class LeapYearCheck {
    public static void main(String[] args) {
        // Define the year
        Year year = Year.of(2024);

        // Check if it's a leap year
        boolean isLeapYear = year.isLeap();
        System.out.println("Is 2024 a leap year? " + isLeapYear);

        // Get the number of days in February
        LocalDate februaryDate = LocalDate.of(year.getValue(), Month.FEBRUARY, 1);
        int daysInFebruary = februaryDate.lengthOfMonth();
        System.out.println("Number of days in February 2024: " + daysInFebruary);
    }
}
```

### Output:

```yaml
Is 2024 a leap year? Yes
Number of days in February 2024: 29
```
