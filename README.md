
import requests

print("AI RESUME ANALYZER")

with open("resume.txt", "r", encoding="utf-8") as file:
    resume = file.read()

prompt = f"""
Analyze the following resume.

1. Identify the candidate's skills and qualifications.
2. Generate a brief resume summary.
3. Suggest areas for improvement.

Resume:
{resume}
"""

url = "http://localhost:11434/api/generate"

data = {
    "model": "llama3.2",
    "prompt": prompt,
    "stream": False
}

response = requests.post(url, json=data)

result = response.json()["response"]

print("\nRESUME ANALYSIS:")
print(result)
