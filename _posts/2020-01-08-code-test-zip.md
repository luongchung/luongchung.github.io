---
layout: post
title:  "TEST "
date:   2017-09-17 13:50:29
categories: laptrinhphantan
---

    #include <iostream>
    using namespace std;
    #define SIZE 80
    #define SIZE_W 50
    #define SIZE_POOL 10000007
    
    void copy(char* n,char* d){
        while (*n != '\0'){
            *d++ = *n++;
        }
        *d='\0';
    }
    bool compare(char* a, char* b){
        while (a){
            if(*a!=*b)return false;
            a++;
            b++;
        }
        return *a==*b;
    }
    
    struct Node{
        Node* chill[SIZE];
        int count;
        bool isEnd;
        char world[SIZE_W];
    };
    
    int index_pool;
    Node POOL[SIZE_POOL];
    Node* getNode(){
        Node* node = &POOL[index_pool++];
        for (int i = 0; i < SIZE; ++i) {
            node->chill[i]=0;
        }
        node->count = 0;
        node->isEnd = false;
        node->world[0] = '\0';
        return node;
    }
    
    Node* rootTree;
    Node* rootCompany;
    
    void init(){
        index_pool = 0;
        rootTree =getNode();
        rootCompany = getNode();
    }
    
    char* nameCompany(char* email){
        char result[50];
        while (*email != '@')email++;
        email++;
        for (int i = 0; *email != '.' ; ++i) {
            result[i] = *email;
            email++;
        }
        return result;
    }
    void Add(char email[]){
        //kiểm tra có chưa
    
    
        //add email
        Node* tmp = rootTree;
        for (int i = 0; email[i] != '\0'; ++i) {
            int index = email[i] - '.';
            if(tmp->chill[index] == 0){
                tmp->chill[index] = getNode();
            }
            tmp = tmp -> chill[index];
            tmp->count++;
        }
        tmp->isEnd = true;
        copy(email,tmp->world);
    
        //add company
        Node* tmpCP = rootCompany;
        email = nameCompany(email);
        for (int i = 0; email[i] != '\0'; ++i) {
            int index = email[i] - '.';
            if(tmpCP->chill[index] == 0){
                tmpCP->chill[index] = getNode();
            }
            tmpCP = tmpCP -> chill[index];
        }
        tmpCP->count++;
    }
    void Delete(char email[]){
        //kiểm tra có chưa
    
    
        //delete email
        Node* tmp = rootTree;
        for (int i = 0; email[i] != '\0'; ++i) {
            int index = email[i] - '.';
            if(tmp->chill[index] == 0){
                tmp->chill[index] = getNode();
            }
            tmp = tmp -> chill[index];
            tmp->count--;
        }
        tmp->isEnd = false;
        tmp->world[0] = '\0';
    
        //delete company
        Node* tmpCP = rootCompany;
        email = nameCompany(email);
        for (int i = 0; email[i] != '\0'; ++i) {
            int index = email[i] - '.';
            if(tmpCP->chill[index] == 0){
                tmpCP->chill[index] = getNode();
            }
            tmpCP = tmpCP -> chill[index];
        }
        tmpCP->count--;
    
    }
    char save[50];
    int ma;
    void run(Node* s){
        if(s->isEnd && s->count > ma){
            copy(s->world,save);
            ma = s->count;
        }
        for (int i = 0; i < 80; ++i) {
            if(s->chill[i] != 0 && s->chill[i]->count > 0){
                run(s->chill[i]);
            }
        }
    
    }
    int Search(char* pre, char* result){
        Node* tmp = rootTree;
        for (; *pre != '\0'; pre++) {
            int index = *pre - '.';
            if(tmp->chill[index] == 0){
                tmp->chill[index] = getNode();
            }
            tmp = tmp -> chill[index];
        }
        ma=-1;
        save[0] = '\0';
        run(tmp);
        copy(save,result);
        return tmp->count;
    }
    
    int SearchbyCompany(char company[]){
        Node* tmpCP = rootCompany;
        for (int i = 0; company[i] != '\0'; ++i) {
            int index = company[i] - '.';
            if(tmpCP->chill[index] == 0){
                tmpCP->chill[index] = getNode();
            }
            tmpCP = tmpCP -> chill[index];
        }
        return tmpCP->count;
    }
    int main()
    {
        init();
        Add("chung11@aa.c");
        Add("chung1@aa.c");
        Add("chung2@aa.c");
        char kq[50];
        int i =Search("chu",kq);
        Delete("chung2@aa.c");
    
        int a = SearchbyCompany("aa");
        cout << "Hello, Dcoder!";
    }
    

