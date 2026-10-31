#include <iostream>
#include <forward_list> 
#include <iterator>
using namespace std;

 forward_list<int> createAndFillList(int N) { 
     forward_list<int> lst;
     
for (int i = 1; i <= N; i++) {
    lst.push_front(i);
}

return lst;
}
 bool insertAfterPosition(forward_list<int>& lst, int position, int value) { 
     auto it = lst.begin();
for (int i = 1; i < position && it != lst.end(); i++) {
    it++;
}

if (it == lst.end()) {
    return false;
}

lst.insert_after(it, value);
return true;
}
 int removeAllOccurrences(forward_list<int>& lst, int value) {
     int count = 0; 
     auto it = lst.before_begin();
     
while (next(it) != lst.end()) {
    if (*next(it) == value) {
        lst.erase_after(it);
        count++;
    } else {
        it++;
    }
}

return count;
}
 void mergeSortedLists(forward_list<int>& f1,
 forward_list<int>& f2) {
     f1.merge(f2); }
 int main() {

forward_list<int> lst = createAndFillList(5);


for (int x : lst) {
    cout << x << " ";
}
cout << endl;


forward_list<int> a = {1, 2, 3, 4};

insertAfterPosition(a, 1, 99);


for (int x : a) {
    cout << x << " ";
}
cout << endl;


forward_list<int> b = {1, 2, 3, 2, 4, 2};

int removed = removeAllOccurrences(b, 2);


for (int x : b) {
    cout << x << " ";
}
cout << endl;

cout << "Removed: " << removed << endl;


forward_list<int> c = {1, 3, 5};
forward_list<int> d = {2, 4, 6};

mergeSortedLists(c, d);


for (int x : c) {
    cout << x << " ";
}
cout << endl;

return 0;
}
