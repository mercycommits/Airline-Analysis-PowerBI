<h1>Airline Analysis - DAX Measures</h1>

<h2>DAX Measures</h2>
<table border="1" cellpadding="5" cellspacing="0">
  <tr>
    <th>Measure Name</th>
    <th>Formula</th>
    <th>Purpose</th>
  </tr>

  <tr>
    <td>Total Flights</td>
    <td><pre>SUM(FactFlights[On-Time]) + SUM(FactFlights[Flights Delayed])</pre></td>
    <td>Total number of flights that actually departed (excluding cancellations)</td>
  </tr>

  <tr>
    <td>Total Cancelled Flights</td>
    <td><pre>SUM(FactFlights[Flights Cancelled])</pre></td>
    <td>Total number of cancelled flights</td>
  </tr>

  <tr>
    <td>Avg Delay of Delayed Flights</td>
    <td><pre>DIVIDE(
    SUMX(FactFlights, FactFlights[Avg Delay (min)] * FactFlights[Flights Cancelled]),
    SUM(FactFlights[Flights Delayed])
)</pre></td>
    <td>Average delay in minutes for flights that were delayed</td>
  </tr>

  <tr>
    <td>On-Time %</td>
    <td><pre>DIVIDE(SUM(FactFlights[On-Time]), [Total Flights])</pre></td>
    <td>Percentage of flights that departed on time</td>
  </tr>

  <tr>
    <td>Delay %</td>
    <td><pre>DIVIDE(SUM(FactFlights[Flights Delayed]), [Total Flights])</pre></td>
    <td>Percentage of flights that were delayed</td>
  </tr>

  <tr>
    <td>Total Delay (min)</td>
    <td><pre>SUMX(
    FactFlights,
    COALESCE(FactFlights[Flights Delayed], 0) * COALESCE(FactFlights[Avg Delay (min)], 0)
)</pre></td>
    <td>Total delay in minutes across all delayed flights</td>
  </tr>

  <tr>
    <td>Worst HourID</td>
    <td><pre>CALCULATE(
    MAX(dimTime[HourID]),
    TOPN(
        1,
        SUMMARIZE(
            FactFlights,
            dimTime[HourID],
            "DelayRate", [Delay %]
        ),
        [DelayRate], DESC
    )
)</pre></td>
    <td>Identifies the hour with the highest delay percentage</td>
  </tr>

  <tr>
    <td>Worst Hour Label</td>
    <td><pre>CALCULATE(
    MAX(dimTime[Hour Label]),
    FILTER(dimTime, dimTime[HourID] = [Worst HourID])
)</pre></td>
    <td>Shows the label (e.g., “5 PM”) of the hour with the highest delays</td>
  </tr>

  <tr>
    <td>Worst Hour Delay %</td>
    <td><pre>CALCULATE(
    [Delay %],
    FILTER(dimTime, dimTime[HourID] = [Worst HourID])
)</pre></td>
    <td>Delay percentage for the hour with the highest delays</td>
  </tr>

</table>


