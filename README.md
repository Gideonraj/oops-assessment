# oops-assigment
THIS IS MY IIT MANDI ASSIGMENT OOPS PYTHON <BR>

from abc import ABC, abstractmethod <BR>

# Abstract class
class SmartDevice(ABC):
    def __init__(self, name):
        self._name = name
        self.__is_on = False  # private attribute

    @abstractmethod
    def operate(self):
        pass

    def turn_on(self):
        self.__is_on = True

    def turn_off(self):
        self.__is_on = False

    def is_on(self):
        return self.__is_on

    def show_status(self):
        status = "ON" if self.__is_on else "OFF"
        print(f"{self._name} is {status}.")


# SmartLight class
class SmartLight(SmartDevice):
    def __init__(self, name):
        super().__init__(name)
        self.__brightness = 70  # private attribute

    def operate(self):
        self.turn_on()
        print(f"{self._name} is now ON with brightness at {self.__brightness}%.")

    # Getter and Setter
    def get_brightness(self):
        return self.__brightness

    def set_brightness(self, level):
        if 0 <= level <= 100:
            self.__brightness = level
        else:
            print("Brightness must be between 0 and 100.")


# SmartFan class
class SmartFan(SmartDevice):
    def __init__(self, name):
        super().__init__(name)
        self.__speed = "Medium"  # private attribute

    def operate(self):
        self.turn_on()
        print(f"{self._name} is now ON at {self.__speed} speed.")

    # Getter and Setter
    def get_speed(self):
        return self.__speed

    def set_speed(self, speed):
        if speed in ["Low", "Medium", "High"]:
            self.__speed = speed
        else:
            print("Speed must be 'Low', 'Medium', or 'High'.")


# SmartAC class
class SmartAC(SmartDevice):
    def __init__(self, name):
        super().__init__(name)
        self.__temperature = 24  # private attribute

    def operate(self):
        self.turn_on()
        print(f"{self._name} is now ON, cooling to {self.__temperature}°C.")

    # Getter and Setter
    def get_temperature(self):
        return self.__temperature

    def set_temperature(self, temp):
        if 16 <= temp <= 30:
            self.__temperature = temp
        else:
            print("Temperature must be between 16°C and 30°C.")


# Demonstration
light = SmartLight("Living Room Light")
fan = SmartFan("Bedroom Fan")
ac = SmartAC("Office AC")

# Operate and show status
print("\n--- Operating Devices ---")
light.operate()
light.show_status()

fan.operate()
fan.show_status()

ac.operate()
ac.show_status()

# Attempt to directly access private attributes (should fail)
print("\n--- Attempting to Access Private Attributes Directly ---")
try:
    print(light.__brightness)
except AttributeError as e:
    print("Error:", e)

try:
    print(fan.__speed)
except AttributeError as e:
    print("Error:", e)

try:
    print(ac.__temperature)
except AttributeError as e:
    print("Error:", e)

# Use getters/setters
print("\n--- Using Getters and Setters ---")
light.set_brightness(85)
print(f"Updated Brightness: {light.get_brightness()}%")

fan.set_speed("High")
print(f"Updated Fan Speed: {fan.get_speed()}")

ac.set_temperature(22)
print(f"Updated AC Temperature: {ac.get_temperature()}°C")

