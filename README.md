import java.util.*;
// Pet class
class Pet {
String id, name, age, owner, address, contact;
Pet(String id, String name, String age, String owner, String address, String contact) {
this.id = id;
this.name = name;
this.age = age;
this.owner = owner;
this.address = address;
this.contact = contact;
}
}
// Appointment class
class Appointment {
String appID, petID, petName, serviceType, serviceName, date, time;
double price;
boolean completed;
Appointment(String appID, String petID, String petName, String serviceType, String
serviceName, double price, String date, String time) {
this.appID = appID;
this.petID = petID;
this.petName = petName;
this.serviceType = serviceType;
this.serviceName = serviceName;
this.price = price;
this.date = date;
this.time = time;
this.completed = false;
}
}
public class Main {
public static void main(String[] args) {
Scanner input = new Scanner(System.in);
ArrayList<Pet> pets = new ArrayList<>();ArrayList<Appointment> appointments = new ArrayList<>();
// ===== CREDENTIALS (changeable) =====
String currentUsername = "admin";
String currentPassword = "123456";
while (true) {
System.out.println("\n-------------- CDO Pet Doctor System --------------");
System.out.println("1. Login");
System.out.println("2. Exit");
System.out.print("Input your choice: ");
int choice = input.nextInt();
input.nextLine();
if (choice == 1) {
// ===== LOGIN WITH ATTEMPT LIMIT =====
int attempts = 0;
final int MAX_ATTEMPTS = 3;
boolean loginSuccess = false;
while (attempts < MAX_ATTEMPTS) {
System.out.print("Enter username: ");
String username = input.nextLine();
System.out.print("Enter password: ");
String password = input.nextLine();
if (username.equals(currentUsername) && password.equals(currentPassword)) {
loginSuccess = true;
break;
} else {
attempts++;
if (attempts < MAX_ATTEMPTS) {
System.out.println("Invalid username or password. Please try again.");
}
}
}
if (!loginSuccess) {
System.out.println("\nToo many failed login attempts. The program will now terminate.");
input.close();
System.exit(0);
}System.out.println("Login successful!");
boolean loggedIn = true;
while (loggedIn) {
System.out.println("\n-------------- MENU --------------");
System.out.println("1. Add Pet Record");
System.out.println("2. Manage Records");
System.out.println("3. Add Appointment");
System.out.println("4. Manage Appointments");
System.out.println("5. Log Out");
System.out.print("Enter choice: ");
int menuChoice = input.nextInt();
input.nextLine();
// ===== ADD PET =====
if (menuChoice == 1) {
System.out.println("Please Input Your Pet Information");
System.out.print("Pet ID: ");
String petID = input.nextLine();
System.out.print("Pet Name: ");
String petName = input.nextLine();
System.out.print("Pet Age: ");
String petAge = input.nextLine();
System.out.print("Owner Name: ");
String ownerName = input.nextLine();
System.out.print("Address: ");
String address = input.nextLine();
System.out.print("Contact Number: ");
String contact = input.nextLine();
pets.add(new Pet(petID, petName, petAge, ownerName, address, contact));
System.out.println("Pet Record Added Successfully!");
// ===== MANAGE RECORDS =====
} else if (menuChoice == 2) {
System.out.println("\n--- Manage Records ---");
System.out.println("1. View Records");
System.out.println("2. Update Record");
System.out.println("3. Delete Record");
System.out.println("4. Back");
System.out.print("Enter choice: ");
int subChoice = input.nextInt();input.nextLine();
if (subChoice == 1) {
if (pets.isEmpty()) {
System.out.println("No records found.");
} else {
for (Pet p : pets) {
System.out.println("\nPet ID: " + p.id);
System.out.println("Pet Name: " + p.name);
System.out.println("Pet Age: " + p.age);
System.out.println("Owner: " + p.owner);
System.out.println("Address: " + p.address);
System.out.println("Contact: " + p.contact);

}
}
} else if (subChoice == 2) {
System.out.print("Enter Pet ID to update: ");
String id = input.nextLine();
boolean found = false;
for (Pet p : pets) {
if (p.id.equals(id)) {
System.out.print("New Name: ");
p.name = input.nextLine();
System.out.print("New Age: ");
p.age = input.nextLine();
System.out.print("New Owner: ");
p.owner = input.nextLine();
System.out.print("New Address: ");
p.address = input.nextLine();
System.out.print("New Contact: ");
p.contact = input.nextLine();
found = true;
System.out.println("Record Updated!");
break;
}
}
if (!found) {
System.out.println("Pet not found.");
}
} else if (subChoice == 3) {
System.out.print("Enter Pet ID to delete: ");
String id = input.nextLine();
boolean removed = pets.removeIf(p -> p.id.equals(id));
if (removed) {System.out.println("Record Deleted!");
} else {
System.out.println("Pet not found.");
}
}
// ===== ADD APPOINTMENT =====
} else if (menuChoice == 3) {
System.out.println("\nSelect Service Type:");
System.out.println("1. Vaccine");
System.out.println("2. Grooming");
System.out.println("3. Surgery");
System.out.println("4. Back");
System.out.print("Choice: ");
int serviceChoice = input.nextInt();
input.nextLine();
if (serviceChoice == 4) {
continue;
}
String serviceType = "", serviceName = "";
double price = 0;
if (serviceChoice == 1) {
serviceType = "Vaccine";
System.out.println("1. Anti Rabies (P722)");
System.out.println("2. Parvovirus (P600)");
System.out.println("3. DHPP (P900)");
System.out.println("4. Bordetella (P800)");
System.out.println("5. Leptospirosis (P550)");
System.out.print("Enter choice: ");
int v = input.nextInt();
input.nextLine();
switch (v) {
case 1:
serviceName = "Anti Rabies";
price = 722;
break;
case 2:
serviceName = "Parvovirus";
price = 600;
break;
case 3:
serviceName = "DHPP";price = 900;
break;
case 4:
serviceName = "Bordetella";
price = 800;
break;
case 5:
serviceName = "Leptospirosis";
price = 550;
break;
}
} else if (serviceChoice == 2) {
serviceType = "Grooming";
System.out.println("1. Nail Trim (₱75)");
System.out.println("2. Facial Trimming (₱150)");
System.out.println("3. Paw Shaving (₱150)");
System.out.println("4. Eye Wash (₱75)");
System.out.println("5. Ear Cleaning (₱150)");
System.out.print("Enter choice: ");
int g = input.nextInt();
input.nextLine();
switch (g) {
case 1:
serviceName = "Nail Trim";
price = 75;
break;
case 2:
serviceName = "Facial Trimming";
price = 150;
break;
case 3:
serviceName = "Paw Shaving";
price = 150;
break;
case 4:
serviceName = "Eye Wash";
price = 75;
break;
case 5:
serviceName = "Ear Cleaning";
price = 150;
break;
}
} else if (serviceChoice == 3) {serviceType = "Surgery";
System.out.println("1. Cystotomy (₱10000)");
System.out.println("2. Eye Enucleation (₱8000)");
System.out.println("3. Neuter (₱8000)");
System.out.println("4. GI Surgery (₱15000)");
System.out.print("Enter choice: ");
int s = input.nextInt();
input.nextLine();
switch (s) {
case 1:
serviceName = "Cystotomy";
price = 10000;
break;
case 2:
serviceName = "Eye Enucleation";
price = 8000;
break;
case 3:
serviceName = "Neuter";
price = 8000;
break;
case 4:
serviceName = "GI Surgery";
price = 15000;
break;
}
}
System.out.print("Appointment ID: ");
String appID = input.nextLine();
System.out.print("Pet ID: ");
String petID = input.nextLine();
String petName = "Unknown";
for (Pet p : pets) {
if (p.id.equals(petID)) {
petName = p.name;
break;
}
}
System.out.print("Date (DD-MM-YYYY): ");
String date = input.nextLine();
System.out.print("Time: ");String time = input.nextLine();
appointments.add(new Appointment(appID, petID, petName, serviceType,
serviceName, price, date, time));
System.out.println("Appointment Added Successfully!");
// ===== MANAGE APPOINTMENTS =====
} else if (menuChoice == 4) {
System.out.println("\n--- Manage Appointments ---");

System.out.println("1. View Status");
System.out.println("2. Update Appointment");
System.out.println("3. Cancel Appointment");
System.out.println("4. Mark as Complete");
System.out.println("5. View Appointments by Date");
System.out.println("6. Back");
System.out.print("Choice: ");
int appChoice = input.nextInt();
input.nextLine();
// VIEW STATUS
if (appChoice == 1) {
if (appointments.isEmpty()) {
System.out.println("No appointments found.");
} else {
for (Appointment a : appointments) {
System.out.println("\nPET ID: " + a.petID);
System.out.println("SERVICE TYPE: " + a.serviceType);
System.out.println("SERVICE NAME: " + a.serviceName);
System.out.println("PRICE: ₱" + a.price);
System.out.println("DATE & TIME: " + a.date + " " + a.time);
System.out.println("STATUS: " + (a.completed ? "Completed" :
"Pending"));
}
}
// UPDATE APPOINTMENT
} else if (appChoice == 2) {
System.out.print("Enter Appointment ID to update: ");
String id = input.nextLine();
boolean found = false;
for (Appointment a : appointments) {
if (a.appID.equals(id)) {
System.out.print("Update Pet ID: ");
a.petID = input.nextLine();System.out.print("Update Service Type: ");
a.serviceType = input.nextLine();
System.out.print("Update Service Name: ");
a.serviceName = input.nextLine();
System.out.print("Update Price: ");
a.price = input.nextDouble();
input.nextLine();
System.out.print("Update Date: ");
a.date = input.nextLine();
System.out.print("Update Time: ");
a.time = input.nextLine();
found = true;
System.out.println("Appointment Updated!");
break;
}
}
if (!found) {
System.out.println("Appointment not found.");
}
// CANCEL APPOINTMENT
} else if (appChoice == 3) {
System.out.print("Enter Appointment ID to cancel: ");
String id = input.nextLine();
Appointment apptToCancel = null;
for (Appointment a : appointments) {
if (a.appID.equals(id)) {
apptToCancel = a;
break;
}
}
if (apptToCancel != null) {
System.out.println("\nCANCEL APPOINTMENT?");
System.out.println("1. YES");
System.out.println("2. NO");
System.out.print("Choice: ");
int cancelChoice = input.nextInt();
input.nextLine();
if (cancelChoice == 1) {
appointments.remove(apptToCancel);
System.out.println("Appointment Cancelled!");
} else {
System.out.println("Cancelled operation.");
}} else {
System.out.println("Appointment not found.");
}
// MARK COMPLETE
} else if (appChoice == 4) {
System.out.print("Enter Appointment ID to mark complete: ");
String id = input.nextLine();
Appointment appt = null;
for (Appointment a : appointments) {
if (a.appID.equals(id)) {
appt = a;
break;
}
}
if (appt != null) {
System.out.println("\nAPPOINTMENT DETAILS");
System.out.println("PET NAME: " + appt.petName);
System.out.println("SERVICE: " + appt.serviceName);
System.out.println("PRICE: ₱" + appt.price);
System.out.println("DATE: " + appt.date);
System.out.println("\nIS THE APPOINTMENT COMPLETED?");
System.out.println("1. COMPLETED");
System.out.println("2. PENDING");
System.out.print("Choice: ");
int completeChoice = input.nextInt();
input.nextLine();
if (completeChoice == 1) {
appt.completed = true;
System.out.println("Appointment Completed!");
} else {
System.out.println("Back to menu.");
}
} else {
System.out.println("Appointment not found.");
}
// VIEW APPOINTMENTS BY DATE
} else if (appChoice == 5) {
System.out.print("Enter Date (DD-MM-YYYY): ");
String searchDate = input.nextLine();
boolean found = false;
for (Appointment a : appointments) {
if (a.date.equals(searchDate)) {System.out.println("\nAPPOINTMENT ID: " + a.appID);
System.out.println("Pet Name: " + a.petName + " - " + a.serviceName);
System.out.println("Time: " + a.time);
System.out.println("Status: " + (a.completed ? "Completed" : "Pending"));
found = true;
}
}
if (!found) {
System.out.println("NO APPOINTMENTS FOUND.");
}
}
// ===== LOGOUT =====
} else if (menuChoice == 5) {
System.out.println("Logging out...");
loggedIn = false;
} else {
System.out.println("Invalid choice.");
}
} // end while (loggedIn)
} else if (choice == 2) {
System.out.println("Exiting program...");
break;
}
} // end while (true)
input.close();
}
}
