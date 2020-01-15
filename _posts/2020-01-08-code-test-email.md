---
layout: post
title:  "EMAIL JAVA"
date:   2017-09-17 13:50:29
categories: laptrinhphantan
---

    #include <iostream>
    using namespace std;
    #define N 80
    #define POOL_SIZE 1000
    
    struct Node{
        Node* chill[N];
        bool isEnd;
        int count;
    };
    
    Node POOL[POOL_SIZE];
    int id=0;
    Node* getNode(){
        Node* node = &POOL[id++];
        for (int i = 0; i < N; ++i) {
            node->chill[i]=0;
        }
        node->count=0;
        node->isEnd= false;
        return node;
    }
    Node* root;
    
    int find(const char* email){
        Node* tmp = root;
        while (email[0]!='\0'){
            int index = email[0] - '.';
            if (tmp->chill[index]==0 || tmp->chill[index]->count==0)
                return 0;
            tmp=tmp->chill[index];
            email++;
        }
        return tmp->count;
    }
    bool _find(const char* email){
        Node* tmp = root;
        while (email[0]!='\0'){
            int index = email[0] - '.';
            if (tmp->chill[index]==0 || tmp->chill[index]->count==0)
                return true;
            tmp=tmp->chill[index];
            email++;
        }
        return !tmp->isEnd;
    }
    void removes(const char* email1){
        const char* email=email1;
        Node* tmp = root;
        while (email[0]!='\0'){
            int index = email[0] - '.';
            if (tmp->chill[index]==0 || tmp->chill[index]->count==0)
                return;
            tmp=tmp->chill[index];
            email++;
        }
        if(tmp->count>0 && tmp->isEnd){
            //remove
            tmp->isEnd = false;
            email=email1;
            tmp=root;
            while (email[0]!='\0'){
                int index = email[0] - '.';
                tmp=tmp->chill[index];
                tmp->count--;
                email++;
            }
    
        }
    }
    void add(const char* email1){
        const char* email= email1;
        Node* tmp = root;
        if(!_find(email))return;
        email=email1;
        while (email[0]!='\0'){
            int index = email[0] - '.';
            if (tmp->chill[index]==0)
                tmp->chill[index] = getNode();
            tmp=tmp->chill[index];
            tmp->count++;
            email++;
        }
        tmp->isEnd= true;
    }
    void init(){
        id=0;
        root = getNode();
    }
    
    int main() {
        init();
        char a[4]="012";
        char b[4]="013";
        char c[4]="01";
        char d[5]="0125";
        add(a);
        add(d);
        add(b);
        int kq =find(c);
        removes(c);
        add(c);
    
        int kq1 =find(c);
        cout<<kq<<endl;
    
    
        return 0;
    }


