#include <iostream>
using namespace std;
struct Node { int data; Node* next; };
 Node* findMiddle(Node* head) {
     Node* slow = head;
     Node* fast = head;
while (fast != NULL && fast->next != NULL) {
    slow = slow->next;
    fast = fast->next->next;
}

return slow;
}
 bool hasCycle(Node* head) {
     Node* slow = head;
     Node* fast = head;
while (fast != NULL && fast->next != NULL) {
    slow = slow->next;
    fast = fast->next->next;

    if (slow == fast)
        return true;
}

return false;
}
 Node* deleteDuplicates(Node* head) { 
     Node* current = head;
while (current != NULL && current->next != NULL) {

    if (current->data == current->next->data) {
        Node* temp = current->next;
        current->next = temp->next;
        delete temp;
    }
    else {
        current = current->next;
    }
}

return head;
}
int main() { 
    return 0; }
