```cpp
#include <iostream>
#include <string>
#include <iomanip>
#include <math.h>
#include <algorithm>

using namespace std;

template<class T> class LNode
{
    // int len()
    // T get(int index)
    // void change(int index, T data)
    // void append(T data)
    // T pop(int index=-1)
    // void print()
    // void reverse()
    // void removeduplicate()
    // void clear()
    public:
        LNode()
        {
            this->next=NULL;
        }

        T data;
        LNode* next;

        int len() //FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION
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

        T get(int index) //FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION
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
        void change(int index, T data) //FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION
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
        void append(T data) //FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION
        {
            LNode* p = this;
            LNode* node;
            node = new LNode;
            node->data = data;
            node->next = NULL;
            while(p->next)
                p=p->next;
            p->next = node;
        }
        T pop(int index=-1)  //FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION
        {
            LNode* p = this;
            T result;
            if(index >= 0)
            {
                if(index+1>this->len())
                    cout<<"error, index overflow"<<endl;
                else
                {
                    for(int i=0;i<index;i++)
                        p=p->next;
                    LNode* pNext = p->next;
                    if(pNext->next)
                    {
                        LNode* pNextNext = pNext->next;
                        p->next = pNextNext;
                        result = pNext->data;
                        free(pNext);
                    }
                    else if(!pNext->next)
                    {
                        p->next = NULL;
                        result = pNext->data;
                        free(pNext);
                    }
                }
            }
            else
            {
                if(-index>this->len())
                    cout<<"error, index overflow"<<endl;
                else
                {
                    for(int i=0;i<(this->len()+index);i++)
                        p=p->next;
                    LNode* pNext = p->next;
                    if(pNext->next)
                    {
                        LNode* pNextNext = pNext->next;
                        p->next = pNextNext;
                        result = pNext->data;
                        free(pNext);
                    }
                    else if(!pNext->next)
                    {
                        p->next = NULL;
                        result = pNext->data;
                        free(pNext);
                    }
                }
            }
            return result;
        }
        void print() //FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION
        {
            LNode* p = this;
            while(p->next)
            {
                p=p->next;
                cout<<p->data<<' ';
            }
            cout<<endl;
        }
        void reverse() //FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION
        {
            LNode* p;
            LNode* q;
            LNode* ptr=this;
            if(ptr->next)
            {
                p=ptr->next;
                ptr->next=NULL;
                while(p)
                {
                    q=p;
                    p=p->next;
                    q->next=ptr->next;
                    ptr->next=q;
                }
            }
            else
            {
                cout<<"error, empty list";
            }
        }
        void removeduplicate() //FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION
        {
            LNode* p=this;
            if(p->next)
            {
                p=p->next;
                while(p)
                {
                    LNode* q=p;
                    while(q->next)
                    {
                            LNode* qNext = q->next;
                            if(qNext->data==p->data)
                            {
                                p->next=qNext->next;
                                free(qNext);
                            }
                            else
                                q=q->next;
                    }
                    p=p->next;
                }
            }
        }
        void clear() //FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION FUNCTION
        {
            LNode* p = this;
            LNode* del;
            LNode* head=p;
            if(p->next)
            {
                p=p->next;
                while(p!=NULL)
                {
                    del=p;
                    p=p->next;
                    free(del);
                }
                head->next=NULL;
                p=head;
            }
        }
};
```
