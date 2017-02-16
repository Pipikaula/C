
/*
 * Author: Andy Omori
 *
 * Purpose: Store my checks
 *
 * Date Created: 2/15/2017
 */
 
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

struct Checks {  //Structure of check
   char date[50];
   char to[50];
   char desc[100];
   float amount;
   int chNum;
   struct Checks *next; //Point to next
};

//Function Declarations
void addCheck();    
void showCheckInfo(struct Checks *chk);
struct Checks* getCheckInfo(struct Checks *chk);
void showCheckList();
void deleteCheck(int id);
struct Checks *checkbook = NULL; // The list of checks
struct Checks *last = NULL; // Track the last check

int main(void) {
   
   int i;
   do {
       printf("1 to add check, 2 to delete check, 3 to show checkbook, 4 to quit: ");
       scanf("%d", &i);
       switch (i) {
            case 1:
                   addCheck(); //Add a check to checkbook
                   break;
            case 2:
            case 3:
                   printf("Checkbook\n"); //Show checkbook
                   showCheckList();
                   if (i == 2) { //Delete a check in checkbook
		                   int id;
		                   printf("Enter the check number to delete: ");
		                   scanf("%d", &id);
		                   deleteCheck(id);
		                   printf("Checkbook:\n");
		                   showCheckList();
		               }
                   break;       
       }
   } while (i != 4);
    
   return 0;
}

void addCheck() {  //Function that adds the check and ask for input from getCheckInfo()
    
   struct Checks *newNode = (struct Checks*)malloc(sizeof(struct Checks)); //Create, allocate memory
     
   if (last == NULL) { //Set check number to space 1
	     newNode -> chNum;
   }
   else { //Sets check to last space + 1
	     newNode -> chNum = last -> chNum + 1;
    }
    
   newNode = getCheckInfo(newNode); //Obtain my check information using a new node
   newNode -> next = NULL;
   printf("\nVector added to the list:\n");
   showCheckInfo(newNode);
    
   if (checkbook == NULL) {  //If empty then new node made
	     checkbook = newNode;
	     last = newNode;
   }
   else { //Points to tail of list
	     last -> next = newNode;
	     last = newNode;
   }
}

struct Checks* getCheckInfo(struct Checks *chk) { //Ask for user input

   printf("Enter the check number: ");
   scanf("%d", &chk->chNum);  
   printf("Enter the amount of the check: "); 
   scanf("%f", &chk->amount);
   printf("Enter the date of check: ");
   scanf("%s", &chk->date);
   printf("Who is the check to?: ");
   scanf("%s", &chk->to);
   printf("Description of check: ");
   scanf("%s", &chk->desc);
    
   return chk;
}

void showCheckInfo(struct Checks *chk) {  //Function to show a check
    
   printf("Check Number:%d\n", chk->chNum);
   printf("Check Amount:%.2f\n", chk->amount);  //Two decimal places
   printf("Check Date:%s\n", chk->date);
   printf("Check To:%s\n", chk->to);
   printf("Check Description:%s\n", chk->desc);
}

void showCheckList() { //Show checkbook
  
   struct Checks *current = checkbook;
   while (current != NULL) {
	        showCheckInfo(current);
	        current = current -> next;
   }
}
    
void deleteCheck(int id) {  //Delete check in checkbook and clear memory
	
   struct Checks *tmp = checkbook;
   struct Checks *del = NULL;

   if (tmp == NULL) { //If empty
	          printf("No check found in the checkbook.\n", id);
   }
   else if (tmp -> chNum == id) {
	          del = tmp;
	          checkbook = tmp -> next;
	          printf("Check number %d deleted.\n", id);
   }
   else {
	       while (tmp != NULL) {
	              if (tmp -> next == NULL) {
		                            printf("Check number %d not found in the checkbook.\n", id);
		                            break; 
	              }	
	              else if (tmp -> next -> chNum == id) {
	                              del = tmp -> next;
		                            tmp -> next = tmp -> next -> next;
		                            del -> next = NULL;
		                            free(del); //Clear space
	                              del = NULL;
		                            break;
	              }
	              else {
		                            tmp = tmp -> next;
	              }
	       }
   }
}
