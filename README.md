# Rotate-LL
Rotate a linked list by k places to the right with the best technique.
//Rotate a linked list by k places to right
#include<iostream>
using namespace std;

struct Node{
	int data;
	Node* next;
	Node(int d){
		data=d;
		next=NULL;
	}	
};

Node* rotateList(Node* head,int k){
	if(head==NULL || head->next==NULL){
		return head;
	}
	int count=1;
	Node* curr=head;
	while(curr->next!=NULL){
		count++;
		curr=curr->next;
	}
	curr->next=head;   //The list is made circular
	curr=head;
	for(int i=0;i<(count-(k%count)-1);i++){ //use the formula
		curr=curr->next;
	}
	head=curr->next;
	curr->next=NULL;
	return head;
}

void printList(Node* head)
{
	if(head==NULL){
		return;
	}
	Node* curr=head;
	while(curr!=NULL){
		cout<<curr->data<<" ";
		curr=curr->next;
	}
	
}
int main(){
	Node* head=new Node(1);
	head->next=new Node(2);
	head->next->next=new Node(3);
	head->next->next->next=new Node(4);
	head->next->next->next->next=new Node(5);
	int k=3;
	printList(head);
	cout<<endl;
	head=rotateList(head,k);
	printList(head);
}
