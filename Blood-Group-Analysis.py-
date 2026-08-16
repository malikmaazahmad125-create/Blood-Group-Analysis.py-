import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns


print("=" * 50)
print("          BLOOD GROUP ANALYZER")
print("=" * 50)


# ==========================================
# PATIENT DATA
# ==========================================

patients = [
    {"Name": "Hadiya Noor", "Blood_Group": "A+"},
    {"Name": "Amna Sajid", "Blood_Group": "B+"},
    {"Name": "Rehman Ali", "Blood_Group": "A+"},
    {"Name": "Nabeel Ullah", "Blood_Group": "O+"},
    {"Name": "Marwah Chaudhary", "Blood_Group": "B+"},
    {"Name": "Ijaz Khaleel", "Blood_Group": "A+"},
    {"Name": "Sheroz Khaliq", "Blood_Group": "O+"},
    {"Name": "Irha Malik", "Blood_Group": "AB+"},
    {"Name": "Raheem Farooq", "Blood_Group": "O+"},
    {"Name": "Mahad Ali", "Blood_Group": "O+"}
]


# ==========================================
# CREATE PANDAS DATAFRAME
# ==========================================

df = pd.DataFrame(patients)

print("\nPATIENT DATA:")
print(df)


# ==========================================
# BLOOD GROUP COUNT
# ==========================================

blood_group_count = df["Blood_Group"].value_counts()

print("\nBLOOD GROUP COUNT:")
print(blood_group_count)


print("\nMOST COMMON BLOOD GROUP:")
print(blood_group_count.idxmax())


# ==========================================
# SHOW PATIENTS BY BLOOD GROUP
# ==========================================

def show_patients(blood_group):
    result = df[df["Blood_Group"] == blood_group]

    print(f"\n{blood_group} PATIENTS:")

    if not result.empty:
        print(result["Name"].to_string(index=False))
    else:
        print("No patients found.")


show_patients("O+")


# ==========================================
# BLOOD DONATION COMPATIBILITY
# ==========================================

compatibility = {
    "A+": ["A+", "AB+"],
    "B+": ["B+", "AB+"],
    "O+": ["O+", "A+", "B+", "AB+"],
    "AB+": ["AB+"]
}


def can_donate(donor_group):

    if donor_group in compatibility:
        print(f"\n{donor_group} CAN DONATE TO:")

        for receiver in compatibility[donor_group]:
            print(receiver)

    else:
        print("Invalid blood group.")


# ==========================================
# FIND COMPATIBLE DONORS
# ==========================================

def find_donor(recipient_group):

    compatible_donors = []

    for donor_group, recipients in compatibility.items():

        if recipient_group in recipients:
            compatible_donors.append(donor_group)

    print(f"\nCOMPATIBLE DONORS FOR {recipient_group}:")

    for donor in compatible_donors:
        print(donor)


# ==========================================
# SEARCH PATIENT
# ==========================================

def find_blood_group(name):

    result = df[
        df["Name"].str.lower() == name.lower()
    ]

    if not result.empty:

        print("\nPATIENT FOUND:")
        print(result.to_string(index=False))

    else:
        print("Patient not found.")


# ==========================================
# BLOOD GROUP STATISTICS
# ==========================================

total_patients = len(df)

statistics = blood_group_count.reset_index()

statistics.columns = [
    "Blood_Group",
    "Total_Patients"
]

statistics["Percentage"] = np.round(
    (statistics["Total_Patients"] / total_patients) * 100,
    2
)

print("\nBLOOD GROUP STATISTICS:")
print(statistics)


# ==========================================
# USER INPUT
# ==========================================

donor = input(
    "\nEnter donor blood group: "
).upper().strip()

can_donate(donor)


recipient = input(
    "\nEnter recipient blood group: "
).upper().strip()

if recipient in compatibility:
    find_donor(recipient)
else:
    print("Invalid blood group.")


name = input(
    "\nEnter patient name: "
).strip()

find_blood_group(name)


# ==========================================
# DATA VISUALIZATION
# ==========================================

sns.set_theme(style="whitegrid")


# BAR CHART

plt.figure(figsize=(8, 5))

sns.barplot(
    x=blood_group_count.index,
    y=blood_group_count.values
)

plt.title("Blood Group Distribution")
plt.xlabel("Blood Group")
plt.ylabel("Number of Patients")

plt.show()


# PIE CHART

plt.figure(figsize=(7, 7))

plt.pie(
    blood_group_count.values,
    labels=blood_group_count.index,
    autopct="%1.1f%%",
    startangle=90
)

plt.title("Blood Group Distribution")

plt.show()


# SEABORN COUNT PLOT

plt.figure(figsize=(8, 5))

sns.countplot(
    data=df,
    x="Blood_Group"
)

plt.title("Blood Group Count Plot")
plt.xlabel("Blood Group")
plt.ylabel("Number of Patients")

plt.show()


print("\n" + "=" * 50)
print("     END OF BLOOD GROUP ANALYZER")
print("=" * 50)
