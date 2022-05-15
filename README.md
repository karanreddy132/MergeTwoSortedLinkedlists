/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
	ListNode *mergeTwoLists(ListNode *list1, ListNode *list2,ListNode *head = nullptr,ListNode *tmp = nullptr) {
		if(list1==nullptr && list2==nullptr){
            return head;
        }
        else if(list1==nullptr){
            if(head==nullptr){
                return list2;
            }
            else{
                tmp->next = list2;
                return head;
            }
        }
        else if(list2==nullptr){
            if(head==nullptr){
                return list1;
            }
            else{
                tmp->next = list1;
                return head;
            }
        }
        
        if(head==nullptr){
            if(list1->val < list2->val){
                head = new ListNode(list1->val);
                tmp = head;
                list1 = list1->next;
            }
            else if(list1->val > list2->val){
                head = new ListNode(list2->val);
                tmp = head;
                list2 = list2->next;
            }
            else{
                head = new ListNode(list1->val);
                tmp = head;
                tmp->next = new ListNode(list2->val);
                tmp = tmp->next;
                list1 = list1->next;
                list2 = list2->next;
            }
        }
        else{
            if(list1->val < list2->val){
                tmp->next = new ListNode(list1->val);
                tmp = tmp->next;
                list1 = list1->next;
            }
            else if(list1->val > list2->val){
                tmp->next = new ListNode(list2->val);
                tmp = tmp->next;
                list2 = list2->next;
            }
            else{
                tmp->next = new ListNode(list1->val);
                tmp = tmp->next;
                tmp->next = new ListNode(list2->val);
                tmp = tmp->next;
                list1 = list1->next;
                list2 = list2->next;
            }
        }
        return mergeTwoLists(list1,list2,head,tmp);
	}
};
