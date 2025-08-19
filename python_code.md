from collections import deque
import datetime

class HospitalQueue:
    def __init__(self):
        self.queue = deque()

    def add_patient(self, name, age, issue):
        patient = {
            "name": name,
            "age": age,
            "issue": issue,
            "time": datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        }
        self.queue.append(patient)
        print(f"Patient '{name}' added to the queue.")

    def serve_patient(self):
        if self.queue:
            patient = self.queue.popleft()
            print("\n Serving Patient:")
            print(f"Name  : {patient['name']}")
            print(f"Age   : {patient['age']}")
            print(f"Issue : {patient['issue']}")
            print(f"Time  : {patient['time']}\n")
        else:
            print("No patients in the queue.")

    def show_queue(self):
        if not self.queue:
            print("No patients in the queue.")
            return
        print("\nCurrent Patient Queue:")
        for idx, patient in enumerate(self.queue, start=1):
            print(f"{idx}. {patient['name']} (Age: {patient['age']}, Issue: {patient['issue']})")

# -------- MENU BASED PROGRAM --------
if __name__ == "__main__":
    hospital = HospitalQueue()

    while True:
        print("\n====== Hospital Patient Queue ======")
        print("1. Add Patient")
        print("2. Serve Patient")
        print("3. Show Queue")
        print("4. Exit")

        choice = input("Choose option: ")

        if choice == "1":
            name = input("Enter patient name: ")
            age = input("Enter patient age: ")
            issue = input("Enter health issue: ")
            hospital.add_patient(name, age, issue)

        elif choice == "2":
            hospital.serve_patient()

        elif choice == "3":
            hospital.show_queue()

        elif choice == "4":
            print("Exiting... Goodbye!")
            break

        else:
            print("⚠️ Invalid choice! Please try again.")
