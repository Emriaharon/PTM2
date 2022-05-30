# Backend
Stores flight data and analytics in SQL database and manages access to the database via queries. 

### Communication with Agent:
- Constantly receiving completed flight information and storing in the DB.

### Communication with Front-End:
- **Fleet overview**: when received a query extracting from the DB information about all the active planes in the Simulator (location, flight direction, call sign, height, speed, mileage, and other) along with the number of inactive gears and sending it to the Front in real time.
- **Time Capsule**: when received a query regarding a specific flight extracting all its data from the DB and sending it to the Front in CSV Time Series format.

### Managing communication between the Agent and the Front-End:
- **Monitoring**: when received a query regarding a specific plane requesting its data from the Agent and forwarding it to the Front in real time.
- **Teleoperation**: receiving joystick instructions from the Front and forwarding them to the agent in real time or alternatively receiving code for the automation and sending the instructions to the Agent after the interpretation.
# Model
**Services**:
- Storing flight information in the database
- Providing information from the DB about all active planes in the FlightGear
- Providing TimeSeries CSV containing all information regarding a requested flight stored in the DB
- Transferring real time data of the specific plane from Agent to the Front End 
- Interpreting code written in client’s language and converting it to flight instructions
- Sending flight instructions to Agent

# Controller
Waiting for a notification from View that a new task created or that Model finished calculation and adding a new command to a queue for execution.
# View
Responsible for getting requests from Front End and Agent, handling all the tasks.
# Side notes
Who is initiating a flight information saving and in what is the frequency? In what format?

Is there any additional charts in the Fleet Overview besides the required ones?

Is the Backend expected to do any manipulation on the data forwarded to the Agent during Monitoring?

