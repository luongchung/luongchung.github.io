---
layout: post
title:  "TEST "
date:   2017-09-17 13:50:29
categories: laptrinhphantan
---


    #include <iostream>
    #define POOL_SIZE 1000000
    using namespace std;
    
    struct Node {
        int key;
        Node *left, *right;
    }POOL[POOL_SIZE];
    int index_p;
    Node* root = 0;
    Node* newNode(int value){
        Node* node = &POOL[index_p++];
        node->left = 0;
        node->right =0;
        node->key = value;
        return node;
    }
    
    
    // Insert a node
    void insertNode(int value) {
        Node* node = root;
        if (node == 0){
            root = newNode(value);
            return;
        }
        while (true){
            if(value == node->key)return;
            if (value < node->key){
                if(node->left==0){
                    node->left = newNode(value);
                    return;
                }
                node = node->left;
            }
            else {
                if(node->right==0) {
                    node->right = newNode(value);
                    return;
                }
                node = node->right;
            }
        }
    }
    
    // Deleting a node
    bool deleteNode(Node* n, int value){
        if (n == 0) return false;
        else if (n->key > value) return deleteNode(n->left, value);
        else if (n->key < value) return deleteNode(n->right, value);
        else
        {
            if (n->left == 0) n = n->right;    // Node chi co cay con phai
            else if (n->right == 0) n = n->left;   // Node chi co cay con trai
            else // Node co ca 2 con
            {
                Node *tmp = n->left;
                while (tmp->right != 0)
                {
                    tmp = tmp->right;
                }
                n->key = tmp->key;
                deleteNode(n->left, tmp->key);
            }
        }
        return true;
    }
    
    
    int abs1(int a){
        if(a<0)a*=-1;
        return a;
    }
    int diff = 10000000;
    int save = -1;
    void nhoGanNhat(Node* n,int value){
        if(n == 0)return;
        if(value > n->key && abs1(value-n->key)<diff){
            diff = abs1(value-n->key);
            save = n->key;
        }
        if(n->key > value)nhoGanNhat(n->left,value);
        else if(n->key < value)nhoGanNhat(n->right,value);
        else nhoGanNhat(n->left,value);
    }
    
    void lonGanNhat(Node* n,int value){
        if(n == 0)return;
        if(value < n->key && abs1(value-n->key)<diff){
            diff = abs1(value-n->key);
            save = n->key;
        }
        if(n->key > value)lonGanNhat(n->left,value);
        else if(n->key < value)lonGanNhat(n->right,value);
        else lonGanNhat(n->right,value);
    }
    
    int main()
    {
        insertNode(8);
        insertNode(10);
        insertNode(3);
        insertNode(1);
        insertNode(6);
        insertNode(14);
        insertNode(4);
        insertNode(7);
        insertNode(13);
    
        bool kt = deleteNode(root,14);
        diff = 10000000;
        save = -1;
        int a = 14;
        nhoGanNhat(root,a);
        cout<<"Nho gan nhat: "<<save<<endl;
        diff = 10000000;
        save = -1;
        lonGanNhat(root,a);
        cout<<"Lon gan nhat: "<<save<<endl;
    
    }
    

