# Equipment Monitor

A learning project for engineering students and technicians exploring equipment monitoring with **Arduino UNO R4 WiFi and Node-RED**.

The Arduino sends simulated temperature readings over Wi-Fi. Node-RED displays live data, detects overheating and communication loss, and saves measurements and events for later analysis.

## Current features

- Live temperature dashboard and chart.
- Overheating alarms and alarm-clear notifications.
- ONLINE/OFFLINE monitoring.
- Automatic reconnection after a Node-RED restart.
- Persistent measurement logging to `measurements.csv`.
- Timestamped alarm and connection events in `events.jsonl`.
- Manually generated reports showing recorded event counts and invalid log entries.

**This prototype uses simulated temperatures. It is intended for learning and demonstration, not safety-critical monitoring.**

## Download

Open [Releases](../../releases), select **v1.6**, and download `equipment-monitor-github-v1.6.zip` under **Assets**.

## Requirements

- Arduino UNO R4 WiFi and Arduino IDE.
- Node.js and Node-RED.
- The dashboard nodes used by the supplied flow.
- Arduino and computer connected to the same local network.

## Getting started

1. Extract the ZIP.
2. Start Node-RED by running `node-red`, then open `http://localhost:1880`.
3. Use **Menu → Import** to import `equipment-monitor-v1.6.json`. Install any missing nodes identified by Node-RED.
4. Create `C:\EquipmentMonitor` for the logs, or update the file paths in the flow.
5. Open the supplied Arduino sketch in Arduino IDE. Set your Wi-Fi credentials and the Node-RED computer’s local IP address, then upload it to the board.
6. Click **Deploy** in Node-RED and open the dashboard. Simulated temperature readings should update, with alarms appearing during hot cycles.

Keep Wi-Fi passwords out of files committed to GitHub.

## Try it

- **Overheating:** watch a simulated temperature cycle produce an alarm and a clear event.
- **Communication loss:** disconnect the Arduino and wait for OFFLINE, then reconnect it and check for ONLINE.
- **Recovery:** stop and restart Node-RED while leaving the Arduino powered. Readings should resume without resetting the board.
- **Reporting:** click the small inject button beside **Generate report**, then expand the summary in Debug.

Reports count **recorded log entries**. Redeployments may produce additional ONLINE entries, so these counts do not necessarily represent distinct connection incidents.

## Progress — 8 November 2026

Verified automatic reconnection, persistent measurement and event logging, and event-summary generation. The tested event log contained **0 invalid lines**.

Next: add minimum, maximum and average temperature from `measurements.csv`, followed by advisory AI diagnostics.
