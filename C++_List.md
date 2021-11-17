```cpp
#include <iostream>
#include <string>
#include <iomanip>
#include <math.h>
#include <algorithm>

using namespace std;

class LNode
{
    public:
        LNode()
        {
            this->last=NULL;
            this->next=NULL;
        }

        int data; //element type can be changed
        LNode* next;
        LNode* last;

        int len();
        int get(int index); //element type can be changed
        void change(int index, int data); //element type can be changed
        void append(int data); //element type can be changed
        int pop(int index=-1); //element type can be changed
        int max(); //element type can be changed
        int min(); //element type can be changed
        void print();
};

int LNode::len()
{
    LNode* p = this;
    unsigned int count=0;
    while(p->next)
    {
        p=p->next;
        count++;
    }
    return count;
}

int LNode::get(int index)
{
    LNode* p = this;
    if(index >= 0)
    {
        if(index+1>this->len())
        {
            cout<<"error, index overflow"<<endl;
            return 0;
        }
        else
        {
            for(int i=0;i<index+1;i++)
                p=p->next;
            return p->data;
        }
    }
    else
    {
        if(-index>this->len())
        {
            cout<<"error, index overflow"<<endl;
            return 0;
        }
        else
        {
            for(int i=0;i<(this->len()+index+1);i++)
                p=p->next;
            return p->data;
        }
    }
}

void LNode::change(int index, int data) //element type can be changed
{
    LNode* p = this;
    if(index >= 0)
    {
        if(index+1>this->len())
            cout<<"error, index overflow"<<endl;
        else
        {
            for(int i=0;i<index+1;i++)
                p=p->next;
            p->data = data;
        }
    }
    else
    {
        if(-index>this->len())
            cout<<"error, index overflow"<<endl;
        else
        {
            for(int i=0;i<(this->len()+index+1);i++)
                p=p->next;
            p->data = data;
        }
    }
}

void LNode::append(int data) //element type can be changed
{
    LNode* p = this;
    LNode* node;
    node = new LNode;
    node->data = data;
    node->next = NULL;
    while(p->next)
        p=p->next;
    p->next = node;
    node->last = p;
}

int LNode::pop(int index) //element type can be changed
{
    LNode* p = this;
    int result=0; //element type can be changed
    if(index >= 0)
    {
        if(index+1>this->len())
            cout<<"error, index overflow"<<endl;
        else
        {
            for(int i=0;i<index+1;i++)
                p=p->next;
            if(p->next && p->last)
            {
                LNode* pNext = p->next;
                LNode* pLast = p->last;
                pLast->next = pNext;
                pNext->last = pLast;
                result = p->data;
                free(p);
            }
            else if(!p->next && p->last)
            {
                LNode* pLast = p->last;
                pLast->next = NULL;
                result = p->data;
                free(p);
            }
        }
    }
    else
    {
        if(-index>this->len())
            cout<<"error, index overflow"<<endl;
        else
        {
            for(int i=0;i<(this->len()+index+1);i++)
                p=p->next;
            if(p->next && p->last)
            {
                LNode* pNext = p->next;
                LNode* pLast = p->last;
                pLast->next = pNext;
                pNext->last = pLast;
                result = p->data;
                free(p);
            }
            else if(!p->next && p->last)
            {
                LNode* pLast = p->last;
                pLast->next = NULL;
                result = p->data;
                free(p);
            }
        }
    }
    return result;
}

int LNode::max() //element type can be changed
{
    LNode *p = this;
    int max;
    if(p->next)
    {
        p=p->next;
        max=p->data;
        while(p->next)
        {
            p=p->next;
            if(p->data>max)
                max=p->data;
        }
    }
    else
    {
        cout<<"error, index overflow";
        return 0;
    }
    
    return max;
}

int LNode::min() //element type can be changed
{
    LNode *p = this;
    int min;
    if(p->next)
    {
        p=p->next;
        min=p->data;
        while(p->next)
        {
            p=p->next;
            if(p->data<min)
                min=p->data;
        }
    }
    else
    {
        cout<<"error, index overflow";
        return 0;
    }
    
    return min;
}

void LNode::print()
{
    LNode* p = this;
    while(p->next)
    {
        p=p->next;
        cout<<p->data<<' ';
    }
    cout<<endl;
}
```
