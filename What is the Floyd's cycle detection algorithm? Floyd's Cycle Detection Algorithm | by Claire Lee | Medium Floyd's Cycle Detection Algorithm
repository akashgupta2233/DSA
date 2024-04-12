#include<iostream>
using namespace std;

class Node{
    public:
    int data;
    Node* next;
    Node(int data){
       this->data = data;
       this->next = NULL;
    }
};

void print(Node* head){
    Node* temp = head;
    while(temp!=NULL){
        cout<<temp->data<<" ";
        temp=temp->next;
    }   cout<<endl;
}

Node* Cir(Node* &head , int n){            //  return the node at which Tail will point(to make cycle)
    Node* temp = head; 
    for(int i=0 ; i<n ;i++){
        temp=temp->next;
    }
    return temp;
}

Node* end(Node* head ){                // returns the tail of the list
    Node* temp=head;
    Node* prev=NULL;
    while(temp!=NULL){
        prev = temp;
        temp= temp->next;
    }
    return prev;
}

void InsertHead(Node* &head , int data){
    Node* temp = new Node(data);
    temp->next=head;
    head=temp;
}

void RemoveLoop(Node* &head , Node* a){
    Node* Slow = head;
    Node* Fast = a;

    while(Fast->next!=Slow->next){
        Fast=Fast->next;
        Slow=Slow->next;
    }
    Fast->next=NULL;
}

Node* FloydCycleDetection(Node* head) {
    if(head==NULL || head->next==NULL){
        return NULL;
    }
    
    Node* Slow=head;
    Node* Fast=head;

    while(Fast!=NULL && Fast->next!=NULL){
        Fast= Fast->next->next;
        Slow = Slow->next;

        if(Fast==Slow){
            return Fast;
        }
    }
    return NULL;
}


int main(){
    Node* node1 = new Node(80);
    Node* head = node1;

    InsertHead(head ,70);    
    InsertHead(head ,60);    
    InsertHead(head ,50);
    InsertHead(head ,40);
    InsertHead(head ,30);
    InsertHead(head ,20);
    InsertHead(head ,10);
    

    print(head);
    Node* pointConnect = Cir(head , 3);
    cout<<"Connection: "<< pointConnect->data<<endl;

    Node*  Tail = end(head);
    cout<<"Tail: "<< Tail->data<<endl;

    // Connecting point with tail
        Tail->next = pointConnect;
        //print(head);
    
     Node* a = FloydCycleDetection(head);
     
     if(a!=NULL){
        cout<<"Circular"<<endl;
     }else{
        cout<<"Not a Circular"<<endl;
     }
     cout<<a->data<<endl;
     //Node* Point = point(head);
     
     RemoveLoop(head , a);
     print(head);

    return 0;
}
