<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: Thilak Raj . P
<h3>Register Number: 212224040353
<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>
  
# PROGRAM :
~~~
import random

# Define the two rooms in the hospital
room_A = "Room A"
room_B = "Room B"
rooms = [room_A, room_B]

# Unhealthy threshold
UNHEALTHY_TEMP = 98.5

class Patient:
    def __init__(self, room, temperature):
        self.room = room
        self.temperature = temperature
        self.is_healthy = self.temperature <= UNHEALTHY_TEMP

class HospitalEnvironment:
    def __init__(self):
        # Place an unhealthy patient in a random room
        self.patient = Patient(room=random.choice(rooms), temperature=random.uniform(97.0, 101.0))
        self.agent_location = random.choice(rooms)
        self.performance = 0

    def perceive(self):
        # Return the patient's location and temperature
        return self.agent_location, self.patient.room, self.patient.temperature

    def prescribe_medicine(self):
        print(f"Agent is in {self.agent_location}.")
        print(f"Patient is in {self.patient.room} with temperature {self.patient.temperature:.2f}°F.")

        if self.agent_location != self.patient.room:
            print("Agent moving to patient's room...")
            self.agent_location = self.patient.room
            self.performance -= 1  # Movement cost

        if self.patient.temperature > UNHEALTHY_TEMP:
            print("Prescribing medicine for fever.")
            self.performance += 10
            self.patient.is_healthy = True
        else:
            print("Patient is healthy. No treatment needed.")

    def step(self):
        self.prescribe_medicine()
        print(f"Agent performance: {self.performance}\n")

# Main program
if __name__ == "__main__":
    hospital = HospitalEnvironment()

    # Agent checks both rooms in two steps
    for _ in range(2):
        hospital.step()

        # Simulate the patient moving or getting new fever again
        hospital.patient.room = random.choice(rooms)
        hospital.patient.temperature = random.uniform(97.0, 101.0)
        hospital.patient.is_healthy = hospital.patient.temperature <= UNHEALTHY_TEMP

~~~

# OUTPUT 
![image](https://github.com/user-attachments/assets/fc28ce9b-8681-4019-9eb7-b322d9922903)



# RESULT :
Thus, an AI agent is developed.
