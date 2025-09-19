## Integration of a Mathematical Calulations with a Chat Completion System using LLM Function-Calling

### AIM:
To calculate the area of a circle using the formula:

<img width="332" height="122" alt="image" src="https://github.com/user-attachments/assets/b8dc1330-4055-4e35-96ed-d2d53a48c1b2" />

where r is the radius of the circle, and also show the step-by-step calculation.

### PROBLEM STATEMENT:
Write a Python program to calculate the area of a circle using the formula 
The program should take radius as input and display the result with steps.
### DESIGN STEPS:

1)Start the program.
2)Import required modules:
   *math → for π (pi).
   *json → to format the output in JSON.

3)Define a function find_area_of_circle(radius) that:
a. Computes the area using the formula π × r².
b. Creates a dictionary containing:

Shape type ("circle").

4)Step-by-step explanation of the calculation.
c. Converts the dictionary into JSON format with indentation.
d. Returns the JSON string.

Call the function with radius = 7.

5)Print the result.

6)End the program.
### PROGRAM:
```python
from dotenv import load_dotenv
import google.generativeai as genai
import os

# Load API key from .env
load_dotenv()
genai.configure(api_key="AIzaSyChL3CmyEpJnCIkuOqSEmOWjv5XHdySSIE")

# Create a Gemini model
model = genai.GenerativeModel("gemini-1.5-flash")

import math
import json

# Function to actually calculate the area
def find_area_of_circle(radius):
    """Calculate the area of a circle given its radius"""
    area = math.pi * (radius ** 2)
    circle_info = {
        "shape": "circle",
        "radius": radius,
        "formula": "π × r²",
        "area": area,
        "steps": [
            f"Step 1: Square the radius ({radius}² = {radius ** 2})",
            f"Step 2: Multiply by π ({math.pi:.2f} × {radius ** 2})",
            f"Step 3: The area is {area:.2f}"
        ]
    }
    return json.dumps(circle_info, indent=4)

# Function definition schema
functions = [
    {
        "name": "find_area_of_circle",
        "description": "Calculate the area of a circle given its radius",
        "parameters": {
            "type": "object",
            "properties": {
                "radius": {
                    "type": "number",
                    "description": "The radius of the circle (e.g., 7.0)",
                }
            },
            "required": ["radius"],
        },
    }
]

# Example messages
messages = [
    {
        "role": "user",
        "content": "Find the area of a circle with radius 7"
    }
]

# Example usage
if __name__ == "__main__":
    print(find_area_of_circle(7))
```
## OUTPUT:
<img width="1652" height="323" alt="image" src="https://github.com/user-attachments/assets/037ff73f-078b-4345-9e73-cea2f781e3b8" />


## RESULT:
Hence,the python program to design and implement a Python function for converting miles to km,
integrating it with a chat completion system utilizing the function-calling feature of a large language model (LLM) is written successfully and executed.
