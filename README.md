# linked-list-deletion
#include<stdio.h>
#include<stdlib.h>
struct node
{
    int data;
    struct node *next;
};
void linkedlisttraversal(struct node *ptr)
{
    while(ptr!=NULL){
        printf("Element:%d\n",ptr->data);
        ptr=ptr->next;
    }

}
// case 1:delete at the first position
struct node *deleteAtFirst(struct node *head)
{
    struct node *ptr=head;
    head=head->next;
    free(ptr);
    return head;
}
//case 2: delete at the given index
struct node *deleteAtIndex(struct node *head,int index)
{
    struct node *p=head;
    struct node *q=head->next;
    for(int i=0;i<index-1;i++)
    {
        p=p->next;
        q=q->next;
    }
    p->next=q->next;
    free(q);
    return head;

}
// case 3:delete the node at the end
struct node *deleteAtlast(struct node *head)
{
    struct node *p=head;
    struct node *q=head->next;
    while(q->next!=NULL)
    {
        p=p->next;
        q=q->next;
    }
    p->next=NULL;
    free(q);
    return head;

}
// delete node at a given value
struct node *deleteAtgiven(struct node *head,int value)
{
    struct node *p=head;
    struct node *q=head->next;
    while(q->data!=value && q->next!=NULL)
    {
        p=p->next;
        q=q->next;
    }
    if(q->data==value){
        p->next=q->next;
        free(q);
    }
    return head;

}



int main()
{
    struct node *head;
    struct node *second;
    struct node *third;
    struct node *fourth;
// allocates memory from heap
    head=(struct node *)malloc(sizeof(struct node));
    second=(struct node *)malloc(sizeof(struct node));
    third=(struct node *)malloc(sizeof(struct node));
    fourth=(struct node *)malloc(sizeof(struct node));

    head->data=4;
    head->next=second;

    second->data=3;
    second->next=third;

    third->data=8;
    third->next=fourth;

     fourth->data=1;
    fourth->next=NULL;
    printf("Linked list before deletion:\n");
    linkedlisttraversal(head);
    // head=deleteAtFirst(head);
    // head=deleteAtIndex(head,2);
    // head=deleteAtlast(head);
    head=deleteAtgiven(head,8);
    printf("Linked list after deletion:\n");
    linkedlisttraversal(head);

}
