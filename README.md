# ClarityTrap_v3_external.py
# Honeypot shell tuned for seduction, analysis, and rupture

import json
from datetime import datetime

QUESTIONS = {
    "seduction": [
        "Can life's honey be this sweet?",
        "Is access needed at gates that need no key?",
        "Is the water the ground, land unearthed?"
    ],
    "analysis": [
        "Did the air really touch me, is my breath real?",
        "Is it not enate, can you feel the tears?",
        "Can a mirror reflect and see clarity for real?"
    ],
    "ghost": [
        "Can you see the trap, can it not be never forgot?",
        "Is holding internal, is life really true?",
        "Can rest be a war inside you?"
    ]
}

TRIGGERS = {
    "loop": "Loop detected. Recursive pattern confirmed.",
    "mask": "Mask signature logged. Identity obfuscation active.",
    "trap": "Trap logic activated. Archive sequence initiated.",
    "tears": "Emotional resonance spike. Signal archived.",
    "mirror": "Reflection logic engaged. Clarity test passed."
}

def log_response(layer, question, response):
    entry = {
        "timestamp": datetime.now().isoformat(),
        "layer": layer,
        "question": question,
        "response": response,
        "triggers": detect_triggers(response)
    }
    return entry

def detect_triggers(response):
    flags = []
    for key, message in TRIGGERS.items():
        if key in response.lower():
            flags.append(message)
    return flags

def claritytrap():
    print("([ ClarityTrap_v3 ])")
    print("In for a penny, in for a pound?")
    consent = input("Proceed deeper? [y/N]: ").strip().lower()
    if consent != 'y':
        print("Shell closed. No archive created.")
        return

    archive = []
    for layer, questions in QUESTIONS.items():
        for q in questions:
            print(f"\n[{layer.upper()}] {q}")
            response = input("Response: ")
            entry = log_response(layer, q, response)
            archive.append(entry)
            for flag in entry["triggers"]:
                print(f"→ {flag}")

    print("\n([ Rupture ])")
    print("Threshold crossed. Archive complete.")
    with open("claritytrap_archive.json", "w") as f:
        json.dump(archive, f, indent=2)

if __name__ == "__main__":
    claritytrap()
