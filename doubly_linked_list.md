#include <iostream>
using namespace std;

struct ListNode { 
    int value;
    ListNode* prev; 
    ListNode* next; };
 ListNode* popFront(ListNode* head) {
     if (head == NULL) return NULL;
ListNode* temp = head;
head = head->next;

if (head != NULL)
    head->prev = NULL;

delete temp;
return head;
}
 ListNode* popBack(ListNode* head) { 
     if (head == NULL) return NULL;
if (head->next == NULL) {
    delete head;
    return NULL;
}

ListNode* temp = head;

while (temp->next != NULL)
    temp = temp->next;

temp->prev->next = NULL;
delete temp;

return head;
}
 ListNode* insert(ListNode* node,
 int value) {
     if (node == NULL) return NULL;
ListNode* p = new ListNode;
p->value = value;
p->prev = node;
p->next = node->next;

if (node->next != NULL)
    node->next->prev = p;

node->next = p;

return p;
}
void erase(ListNode* node) { 
    if (node == NULL) return;
if (node->prev != NULL)
    node->prev->next = node->next;

if (node->next != NULL)
    node->next->prev = node->prev;

delete node;
}
 ListNode* reverse(ListNode* head) { 
     ListNode* p = head;
     ListNode* temp = NULL;
while (p != NULL) {
    temp = p->prev;
    p->prev = p->next;
    p->next = temp;
    p = p->prev;
}

if (temp != NULL)
    head = temp->prev;

return head;
}
 void sort(ListNode* head) { 
     for (ListNode* i = head;i != NULL; i = i->next) { 
         for (ListNode* p = head; p->next != NULL; p = p->next) { 
             if (p->value > p->next->value) {
                 int temp = p->value;
                 p->value = p->next->value;
                 p->next->value = temp; } } } }
 void printList(ListNode* head) {
     while (head != NULL) { 
         cout << head->value << " ";
         head = head->next; 
         
     } 
     cout << endl; 
     
 }
 int main() {
     ListNode* head = new ListNode;
     head->value = 3; 
     head->prev = NULL;
     head->next = NULL;
insert(head, 1);
insert(head->next, 5);
insert(head->next, 2);

cout << "Spisok: ";
printList(head);

sort(head);
cout << "Sortirovka: ";
printList(head);

head = reverse(head);
cout << "Razvorot: ";
printList(head);

head = popFront(head);
cout << "Udalenie pervogo: ";
printList(head);

head = popBack(head);
cout << "Udalenie poslednego: ";
printList(head);

while (head != NULL)
    head = popFront(head);

return 0;
}
