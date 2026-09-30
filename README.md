# PID-motor-speed-controller
# PID Motor Speed Controller

Kp = 0.8
Ki = 0.2
Kd = 0.1

set_speed = 1000       # Desired speed in RPM
actual_speed = 700     # Initial motor speed

integral = 0
previous_error = 0

print("PID MOTOR SPEED CONTROLLER")
print("--------------------------")

for i in range(1, 11):

    error = set_speed - actual_speed

    # PID calculations
    integral = integral + error
    derivative = error - previous_error

    control = (Kp * error) + (Ki * integral) + (Kd * derivative)

    # Update motor speed
    actual_speed = actual_speed + control * 0.1

    previous_error = error

    print(f"Step {i}")
    print(f"Target Speed : {set_speed:.2f} RPM")
    print(f"Actual Speed : {actual_speed:.2f} RPM")
    print(f"Control Signal: {control:.2f}")
    print("--------------------------")
