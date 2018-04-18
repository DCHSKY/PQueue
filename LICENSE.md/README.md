# PQueue
#ifndef PQUEUE_H
#define PQUEUE_H
#include <string>
//#include<iostream>
class PQueue{
	struct Node{
		std::string name;
		int pri;
		Node *next;
	};
public:
	PQueue(){
		head = NULL;
	}
	~PQueue(){
		while (head != NULL){
			Node *temp = head;
			head = head->next;
			delete temp;
		}
	}
	int enqueue(std::string name, int pri){
		Node *newnode = new Node;
		newnode->name = name;
		newnode->pri = pri;
		newnode->next = NULL;
		if (head == NULL){
			head = newnode;
		}
		else{
			Node *curr = head;
			Node *last = NULL;
			while (curr != NULL){
				if (curr->pri <= newnode->pri){
					newnode->next = curr;
					if (last == NULL){
						head = newnode;
					}
					else
                    {
						last->next = newnode;
                    }
					break;
				}
				curr = curr->next;
			}
		}
		return 0;
	}
	int dequeue(){
		if (head == NULL){
			return -1;
		}
		Node *temp = head;
		head = head->next;
		delete temp;
		return 0;
	}
	//void print(){
	//	node *temp = head;
	//	while(temp != null){
	//		std::cout << "(" << temp->name << "," << temp->pri << ")" << std::endl;
	//		temp = temp->next;
	//	}
	//}
	int front(std::string &n){
		if (head == NULL){
			return -1;
		}
		n = head->name;
		return 0;
	}
private:
	Node *head;
};
#endif
