# Amron_Barangay-Health-Center-Patient-Information_Group6
patients = {
    "Minerva, John": {
        "age": 22,
        "gender": "Male",
        "address": "Carmen, Cagayan de Oro",
        "contact": "09123456789",
        "date_of_visit": "2025-11-11",
        "existing_illness": "Yes",
        "illness_specify": "Hypertension",
        "smoke": "No",
        "drink": "Occasionally",
        "temperature": 36.7,
        "blood_pressure_systolic": 120,
        "blood_pressure_diastolic": 80,
        "checkup_history": ["Flu vaccination - November 2025"]
    },
    "Cinco, Kebb Jan": {
        "age": 21,
        "gender": "Male",
        "address": "Carmen, Cagayan de Oro",
        "contact": "09234567890",
        "date_of_visit": "2025-11-09",
        "existing_illness": "No",
        "illness_specify": "",
        "smoke": "No",
        "drink": "No",
        "temperature": 37.0,
        "blood_pressure_systolic": 118,
        "blood_pressure_diastolic": 79,
        "checkup_history": []
    },
    "Pambid, Joren": {
        "age": 23,
        "gender": "Male",
        "address": "Carmen, Cagayan de Oro",
        "contact": "09345678901",
        "date_of_visit": "2025-11-08",
        "existing_illness": "No",
        "illness_specify": "",
        "smoke": "Yes",
        "drink": "Occasionally",
        "temperature": 36.9,
        "blood_pressure_systolic": 122,
        "blood_pressure_diastolic": 82,
        "checkup_history": []
    }
}


def show_patient_info(name):
    p = patients[name]
    print(f"\nPatient Found: {name}")
    print(f"Age: {p['age']}")
    print(f"Gender: {p['gender']}")
    print(f"Address: {p['address']}")
    print(f"Contact: {p['contact']}")
    print(f"Date of Visit: {p['date_of_visit']}")
    print(f"Existing Illness: {p['existing_illness']} - {p['illness_specify']}")
    print(f"Smoker: {p['smoke']}")
    print(f"Drinks Alcohol: {p['drink']}")
    print(f"Temperature: {p['temperature']} °C")
    print(f"Blood Pressure: {p['blood_pressure_systolic']}/{p['blood_pressure_diastolic']} mmHg")

    print("\n--- Medical Details Menu ---")
    print("1. View Check-up History")
    print("2. Add Check-up Record")
    print("3. Back to Main Menu")
    choice = input("Enter choice: ")

    if choice == "1":
        if p["checkup_history"]:
            print(f"\nCheck-up History for {name}:")
            for record in p["checkup_history"]:
                print(f"- {record}")
        else:
            print("No previous check-up records.")
    elif choice == "2":
        record = input("Enter new check-up details: ")
        p["checkup_history"].append(record)
        print("Check-up record added successfully.")
    else:
        return


def add_new_patient():
    print("\nEnter New Patient Details:")
    name = input("Full Name (e.g., Dela Cruz, Juan): ")

    if name in patients:
        print("Patient already exists.")
        return

    age = int(input("Age: "))
    gender = input("Gender (Male/Female): ")
    address = input("Address: ")
    contact = input("Contact Number: ")
    date_of_visit = input("Date of Visit (YYYY-MM-DD): ")
    existing_illness = input("Existing Illness (Yes/No): ")

    illness_specify = ""
    if existing_illness.lower() == "yes":
        illness_specify = input("Specify Illness: ")

    smoke = input("Smoker (Yes/No): ")
    drink = input("Drinks Alcohol (Yes/No/Occasionally): ")

    temperature = float(input("Temperature (°C): ").replace("°C", "").strip())
    blood_pressure_systolic = int(input("Blood Pressure Systolic (mmHg): ").replace("mmHg", "").strip())
    blood_pressure_diastolic = int(input("Blood Pressure Diastolic (mmHg): ").replace("mmHg", "").strip())

    patients[name] = {
        "age": age,
        "gender": gender,
        "address": address,
        "contact": contact,
        "date_of_visit": date_of_visit,
        "existing_illness": existing_illness,
        "illness_specify": illness_specify,
        "smoke": smoke,
        "drink": drink,
        "temperature": temperature,
        "blood_pressure_systolic": blood_pressure_systolic,
        "blood_pressure_diastolic": blood_pressure_diastolic,
        "checkup_history": []
    }

    print(f"\nNew patient record added for {name}.")


def main():
    while True:
        print("\n=== Barangay Health Center Patient Record System ===")
        print("1. Search Patient")
        print("2. Add New Patient")
        print("3. View All Patients")
        print("4. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            print("\nAvailable Patients:")
            for n in patients.keys():
                print("-", n)
            name = input("\nEnter patient's full name: ")
            if name in patients:
                show_patient_info(name)
            else:
                print("Patient not found.")
        elif choice == "2":
            add_new_patient()
        elif choice == "3":
            print("\n=== All Patient Records ===")
            for name, p in patients.items():
               
