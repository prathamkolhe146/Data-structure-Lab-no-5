# Data-structure-Lab-no-5
Hospital patient registration system 
#include <stdio.h>
#include <string.h>
#define MAX 5
struct Patient
  {
      int patientID;
      char arrivalTime[20];
  };
  struct Patient queue[MAX];
  int front = -1;
  int rear = -1;
  void addPatient()
  {
      struct Patient p;
      if (rear == MAX - 1)
      {
          printf("\nQueue Overflow\n");
          return;
      }
      printf("\nEnter Patient ID: ");
      scanf("%d", &p.patientID);
      printf("Enter Arrival Time: ");
      scanf("%s", p.arrivalTime);

      if (front == -1)
      {
          front = 0;
      }
      rear++;
      queue[rear] = p;
      printf("Patient added successfully.\n");
  }
  void attendPatient()
  {
      if (front == -1)
      {
          printf("\nQueue Underflow\n");
          return;
      }
      printf("\nAttending Patient:\n");
      printf("Patient ID: %d\n", queue[front].patientID);
      printf("Arrival Time: %s\n", queue[front].arrivalTime);

      if (front == rear)
      {
          front = -1;
          rear = -1;
      }
      else
      {
          front++;
      }
      printf("Patient attended successfully\n");
  }

  void viewPatients()
  {
      int i;
      if (front == -1)
      {
          printf("\nNo patients are waiting\n");
          return;
      }
      printf("\nPatients currently waiting:\n");
      printf("--------------------------------\n");
      printf("Patient ID\tArrival Time\n");
      printf("--------------------------------\n");

      for (i = front; i <= rear; i++)
      {
          printf("%d\t\t%s\n",
                 queue[i].patientID,
                 queue[i].arrivalTime);
      }
      printf("--------------------------------\n");
  }

  void isQueueEmpty()
  {
      if (front == -1)
      {
          printf("\nQueue is empty");
      }
      else
      {
          printf("\nQueue is not empty");
      }
  }

  int main()
  {
      int choice;
      do
      {
          printf("\n====== HOSPITAL PATIENT REGISTRATION SYSTEM ======\n");
          printf("1.Add Patient\n");
          printf("2.Attend Patient\n");
          printf("3.View Patients\n");
          printf("4.Check Queue Empty\n");
          printf("5.Exit\n");
          printf("==========================================================\n");
          printf("Enter your choice: ");
          scanf("%d", &choice);

          switch (choice)
          {
          case 1:
              addPatient();
              break;

          case 2:
              attendPatient();
              break;

          case 3:
              viewPatients();
              break;

          case 4:
              isQueueEmpty();
              break;

          case 5:
              printf("\nExit");
              break;

          default:
              printf("\nInvalid choice");
          }

      } while (choice != 5);

      return 0;
  }
