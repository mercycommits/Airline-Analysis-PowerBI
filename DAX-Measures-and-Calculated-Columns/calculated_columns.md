<h1>Calculated Columns (Power BI Data Model)</h1>
<p>This document lists all calculated columns created in the <strong>FactFlights</strong> table to support proper sorting, relationships, and time-based analysis.</p>

<hr>

<h2>🗓️ 1. Month Number</h2>
<p>Used to sort Month names chronologically (January → 1, February → 2, etc.)</p>

<pre>
<code>
Month Number =
SWITCH(
    TRUE(),
    FactFlights[Month] = "January", 1,
    FactFlights[Month] = "February", 2,
    FactFlights[Month] = "March", 3,
    FactFlights[Month] = "April", 4,
    FactFlights[Month] = "May", 5,
    FactFlights[Month] = "June", 6,
    FactFlights[Month] = "July", 7,
    FactFlights[Month] = "August", 8,
    FactFlights[Month] = "September", 9,
    FactFlights[Month] = "October", 10,
    FactFlights[Month] = "November", 11,
    12   -- December
)
</code>
</pre>

<hr>

<h2>📅 2. Day-of-Week Number</h2>
<p>Used to sort days correctly (Monday → 1 ... Sunday → 7)</p>

<pre>
<code>
Day-Of-Week Number =
SWITCH(
    TRUE(),
    FactFlights[Day of Week] = "Monday", 1,
    FactFlights[Day of Week] = "Tuesday", 2,
    FactFlights[Day of Week] = "Wednesday", 3,
    FactFlights[Day of Week] = "Thursday", 4,
    FactFlights[Day of Week] = "Friday", 5,
    FactFlights[Day of Week] = "Saturday", 6,
    7   -- Sunday
)
</code>
</pre>

<hr>

<h2>🛬 3. AirportID</h2>
<p>Links FactFlights to <strong>dimAirport</strong>.</p>

<pre>
<code>
AirportID =
SWITCH(
    TRUE(),
    FactFlights[Origin Airport] = "BWI", 1,
    FactFlights[Origin Airport] = "DCA", 2,
    FactFlights[Origin Airport] = "IAD", 3
)
</code>
</pre>

<hr>

<h2>🛫 4. AirlineID</h2>
<p>Links FactFlights to <strong>dimAirline</strong>.</p>

<pre>
<code>
AirlineID =
SWITCH(
    TRUE(),
    FactFlights[Airline Name] = "AirTran Airways Corporation", 1,
    FactFlights[Airline Name] = "American Airlines Inc.", 2,
    FactFlights[Airline Name] = "American Eagle Airlines Inc.", 3,
    FactFlights[Airline Name] = "Comair Inc.", 4,
    FactFlights[Airline Name] = "Delta Air Lines Inc.", 5,
    FactFlights[Airline Name] = "Expressjet Airlines Inc.", 6,
    FactFlights[Airline Name] = "Mesa Airlines Inc.", 7,
    FactFlights[Airline Name] = "Southwest Airlines Co.", 8,
    FactFlights[Airline Name] = "United Air Lines Inc.", 9,
    FactFlights[Airline Name] = "US Airways Inc.", 10
)
</code>
</pre>

<hr>

<h2>⏱️ 5. DepartureHourNumeric</h2>
<p>Extracts the numeric hour (0–23) from the text-based <i>Departure Hour</i> field. Used to link to <strong>dimTime[HourID]</strong>.</p>

<pre>
<code>
DepartureHourNumeric =
HOUR(
    TIMEVALUE(
        LEFT(
            FactFlights[Departure Hour],
            FIND("-", FactFlights[Departure Hour]) - 1
        )
    )
)
</code>
</pre>

<hr>
