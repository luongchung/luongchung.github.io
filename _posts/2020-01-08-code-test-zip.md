---
layout: post
title:  "ZIP JAVA"
date:   2020-01-07 22:50:29
categories: laptrinhphantan
---

    #include <iostream>
    using namespace std;
    #define N 10
    int A[N]={1,2,3,4,5,1,2,3,4,5};
    int B[4];
    int C[N];
    void nen(){
        int index = 0;
        for (int j = 0; j < 4; ++j) B[j]=0;
        for (int i = 0; i < 4; ++i) {
            if(i%2==0){
                B[i]= B[i] | A[index]<<20;
                index++;
                B[i]= B[i] | A[index]<<8;
                index++;
                B[i]= B[i] | (A[index]>>6)<<2;
            } else{
                B[i]= B[i] | (A[index]<<26)>>2;
                index++;
                B[i]= B[i] | (A[index]<<12);
                index++;
                B[i]= B[i] | A[index];
                index++;
            }
        }
    
    }
    void giai_nen(){
        int index=0;
        for (int i = 0; i < 4; ++i) {
            if(i%2==0){
                C[index]=B[i]>>20;
                index++;
                C[index]=(B[i]<<12)>>20;
                index++;
                C[index]=((B[i]<<24)>>26)<<6;
            } else{
                C[index]= C[index] | (B[i]<<2)>>26;
                index++;
                C[index]=(B[i]<<8)>>20;
                index++;
                C[index]=(B[i]<<20)>>20;
                index++;
            }
        }
    }
    int main() {
    nen();
    giai_nen();

    for (int i = 0; i < N; ++i) {
        cout<<C[i]<<" ";
    }
    cout<<endl;
    return 0;
    }
    

