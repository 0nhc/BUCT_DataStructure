# singly linked list
```cpp
#include <iostream>
#include <string>
#include <iomanip>
#include <math.h>
#include <algorithm>

using namespace std;

struct Node{
    int data;
    Node* next;
};

typedef Node* List;

bool InitList(List &ptr_in)
{
    ptr_in = new Node;
    ptr_in->next=NULL;
    return true;
}

bool AddNode(List &ptr_in, int data)
{
    List p = ptr_in;
    List add;
    add = new Node;
    add->data=data;
    add->next=NULL;
    while(p->next!=NULL)
    {
        p=p->next;
    }
    p->next=add;
    return true;
}

void PrintList(List &ptr_in)
{
    List p = ptr_in;
    p=p->next;
    while(p)
    {
        if(p->data)
        {
            cout<<p->data<<' ';
        }
        p=p->next;
    }
    cout<<endl;
}

int DestroyList(List &ptr_in)
{
    List p = ptr_in;
    List del;
    while(p!=NULL)
    {
        del=p;
        p=p->next;
        free(del);
    }
    return 0;
}

int ClearList(List &ptr_in)
{
    List p = ptr_in;
    List del;
    p=p->next;
    while(p!=NULL)
    {
        del=p;
        p=p->next;
        free(del);
    }
    ptr_in->next=NULL;
    return 0;
}

void InsertList(List &ptr_in, int after_which_index, int data)
{
    List p = ptr_in;
    List insert;
    insert = new Node;
    insert->data = data;
    int current_node_index = 0;
    while(current_node_index < after_which_index)
    {
        p=p->next;
    }
    insert->next = p->next;
    p->next = insert;
}

void ReverseList(List &ptr_in)
{
    List p,q;
    p=ptr_in->next;
    ptr_in->next=NULL;
    while(p)
    {
        q=p;
        p=p->next;
        q->next=ptr_in->next;
        ptr_in->next=q;
    }
}

void RemoveDuplicate(List &ptr_in)
{
    List p = ptr_in;
    p=p->next;
    while(p)
    {
        List q=p;
        while(q->next)
        {
                List qNext = q->next;
                if(qNext->data==p->data)
                {
                    p->next=qNext->next;
                    free(qNext);
                }
                else
                {
                    q=q->next;
                }
        }
        p=p->next;
    }
}
```
