---
layout: post
title:  "ZIP JAVA"
date:   2017-09-17 13:50:29
categories: laptrinhphantan
---

    #include <iostream>
    #define SIZE_DB 50000
    #define CHAR_SIZE 20
    #define FIELD_SIZE 5
    #define HASH_SIZE 1000007
    #define POOL_SIZE 1000000
    using namespace std;
    
    typedef enum{
        NAME,
        NUMBER,
        BIRTHDAY,
        EMAIL,
        MEMO
    }FIELD;
    typedef struct{
        int count;
        char tr[20];
    }RESULT;
    
    void strCopy(char* d,char* n){
        int i=0;
        while (n[i]!='\0'){
            d[i] = n[i];
            i++;
        }
        d[i] = '\0';
    }
    bool strComp(char* a,char* b){
        while (*a==*b){
            if(*a=='\0')return true;
            a++;b++;
        }
        return false;
    }
    
    struct Contact{
        char A[FIELD_SIZE][CHAR_SIZE];
        bool isDelete;
    };
    int index_db=0;
    Contact DB[SIZE_DB];
    
    struct Item{
        int index;
        Item* next;
    };
    Item* TABLE[FIELD_SIZE][HASH_SIZE];
    
    int index_pool=0;
    Item POOL[POOL_SIZE];
    Item* getPool(){
        return &POOL[index_pool++];
    }
    
    int hashindex(char *str)
    {
        unsigned long hash = 5381;
        int c;
        while (c = *str++)
            hash = ((hash << 5) + hash) + c; /* hash * 33 + c */
    
        return hash%HASH_SIZE;
    }
    
    void initDB(){
        index_db=0;
        index_pool=0;
    }
    void AddTable(FIELD field,char* str){
        Item* newItem =getPool();
        if(TABLE[field][hashindex(str)]==0){
            newItem->index=index_db;
            TABLE[field][hashindex(str)] = newItem;
        } else{
            newItem->index=index_db;
            newItem->next = TABLE[field][hashindex(str)];
            TABLE[field][hashindex(str)] = newItem;
        }
    }
    void Add(char* name,char* number, char* birthday, char* email, char* memo){
        //add to BD
        strCopy(DB[index_db].A[NAME],name);
        strCopy(DB[index_db].A[NUMBER],number);
        strCopy(DB[index_db].A[BIRTHDAY],birthday);
        strCopy(DB[index_db].A[EMAIL],email);
        strCopy(DB[index_db].A[MEMO],memo);
        DB[index_db].isDelete = false;
    
        //Save to hashtable
        AddTable(NAME,name);
        AddTable(NUMBER,number);
        AddTable(BIRTHDAY,birthday);
        AddTable(EMAIL,email);
        AddTable(MEMO,memo);
    
        index_db++;
    }
    int Delete(FIELD field, char* str){
        Item* list = TABLE[field][hashindex(str)];
        while (list){
            if (strComp(DB[list->index].A[field],str)){
                DB[list->index].isDelete = true;
            }
            list=list->next;
        }
    }
    int Change(FIELD field, char* str,FIELD changefield, char* changestr){
        Item* list = TABLE[field][hashindex(str)];
        int result = 0;
        while (list){
            if (!DB[list->index].isDelete && strComp(DB[list->index].A[field],str)) {
                strCopy(DB[list->index].A[changefield], changestr);
                result++;
            }
            list=list->next;
        }
        return result;
    }
    RESULT Search(FIELD field, char* str, FIELD returnfield){
        RESULT *result =new RESULT ();
        Item* list = TABLE[field][hashindex(str)];
        result->count=0;
        result->tr[0]='\0';
        while (list){
            if (!DB[list->index].isDelete && strComp(DB[list->index].A[field],str)){
                strCopy(result->tr,DB[list->index].A[returnfield]);
                result->count++;
            }
            list=list->next;
        }
        if(result->count > 1)result->tr[0]='\0';
        return *result;
    }
    
    int main()
    {
        initDB();
        Add("chung","098","1311","chung.lv1","hello");
       // Add("chung","0980","1311","chung.lv11","hello");
        Change(NAME,"chung",EMAIL,"luongchung@");
        Delete(NAME,"chung");
        RESULT result = Search(NAME,"chung",EMAIL);
        cout << "Hello, Dcoder!";
    }
    

