---
layout: post
title:  "EMAIL JAVA"
date:   2017-09-17 13:50:29
categories: laptrinhphantan
---

    
    #include <iostream>
    using namespace std;
    int _durable;
    int _deliveryTime[100];
    
    int sQ;
    struct Q{
    int timec;
    int used;
    }H[10002];
    void swQ(int i, int j){
    H[10001].timec = H[i].timec;
    H[10001].used = H[i].used;
    H[i].timec = H[j].timec;
    H[i].used = H[j].used;
    H[j].timec =  H[10001].timec;
    H[j].used =  H[10001].used;
    }
    void upQ(int index){
    while (index / 2 >= 1){
        if(H[index].timec < H[index/2].timec){
            swQ(index,index/2);
        }
        index  = index / 2;
    }
    }
    void downQ(){
    int index = 1;
    while (index*2 <= sQ) //có con
    {
    if(index * 2 + 1 <= sQ && H[index * 2 + 1].timec < H[index * 2].timec){
    if(H[index * 2 + 1].timec < H[index].timec){
    swQ(index * 2 + 1,index);
    } else break;
    } else{
    if(H[index * 2].timec < H[index].timec){
    swQ(index * 2,index);
    } else break;
    }
    }
    }
    
    ////
    int hs[100]; //heap size
    int HEAP[100][100001];
    void sw(int station, int i, int j){
    int temp = HEAP[station][i];
    HEAP[station][i] = HEAP[station][j];
    HEAP[station][j] =  temp;
    }
    void pushHeap(int station){
    int index = hs[station];
    while (index / 2 >= 1){
    if(HEAP[station][index] < HEAP[station][index/2]){
    sw(station,index,index/2);
    }
    index  = index / 2;
    }
    }
    int popHeap(int station){
    if(hs[station] <= 0) return -1;
    int result = HEAP[station][1];
    sw(station, 1, hs[station]);
    hs[station] --;
    //downHeap
    int index = 1;
    while (index*2 <= hs[station]) //có con
    {
    if(index * 2 + 1 <= hs[station] && HEAP[station][index * 2 + 1] < HEAP[station][index * 2]){
    if(HEAP[station][index * 2 + 1] < HEAP[station][index]){
    sw(station, index * 2 + 1,index);
    } else break;
    } else{
    if(HEAP[station][index * 2] < HEAP[station][index]){
    sw(station, index * 2,index);
    } else break;
    }
    }
    return result;
    }
    ////
    struct Node{
    int validTime;//hạn vé
    bool isRent;
    int timeBegin;
    int timeUsed;
    Node* chill[27];
    }POOL[1000000];
    int indexNode;
    Node* getNode(){
    Node* node = &POOL[indexNode++];
    node->isRent =  false;
    node->validTime =  0;
    for (int i = 0; i < 27; ++i) {
    node->chill[i] = 0;
    }
    return node;
    }
    Node* root;
    
    //N  1->N-1 max 100 station
    //durable - thời hạn xe for all 1-> 1.000.000
    //deliveryTime - thời gian giao hàng của từng trạm  1->1000.000.000
    void init(int N, int durable, int deliveryTime[]){
    indexNode = 0;
    root = getNode();
    _durable = durable;
    for (int i = 0; i < N; ++i) {
    hs[i] = 0;
    _deliveryTime[i] = deliveryTime[i];
    }
    }
    //bicycleNum - số lượng xe được add 1-> 10.000
    void addBicycle(int cTimestamp, int pID, int bicycleNum){
    for (int i = 0; i < bicycleNum; ++i) {
    hs[pID]++;
    HEAP[pID][hs[pID]] = 0;
    pushHeap(pID);
    }
    }
    //uName - tênn khách thuê
    //validTime - hạn vé  1-> 1.000.000
    void buyTicket(int cTimestamp, char uName[],int validTime){
    Node* tmp = root;
    for (int i = 0; uName[i] != '\0'; ++i) {
    int id = uName[i] - 'a';
    if(tmp->chill[id] == 0) tmp->chill[id] = getNode();
    tmp = tmp->chill[id];
    }
    if(tmp->validTime >= cTimestamp){ //vé vẫn còn hạn
    tmp->validTime += validTime;
    } else tmp->validTime = cTimestamp + validTime - 1;
    }
    //Khách thuê xe thời gian run là ngắn nhất
    //return thời gian lên xe xe, otherwire -1
    int rentBicycle(int cTimestamp, char uName[], int pID){
    int temp = popHeap(pID);
    if(temp == -1) return -1; //không có xe

    Node* tmp = root;
    for (int i = 0; uName[i] != '\0'; ++i) {
        int id = uName[i] - 'a';
        if(tmp->chill[id] == 0) return -1; //không có vé
        tmp = tmp->chill[id];
    }
    if(tmp->isRent) return -1; //đã thuê rồi
        if(cTimestamp > tmp->validTime) return -1; //vé hết hạn
        tmp->isRent = true;
        tmp->timeBegin = cTimestamp;
        tmp->timeUsed = temp;
        return temp;
    }
    
    void buyTemp(int time){
    while(sQ > 0 && H[1].timec >= time){
    int p = H[1].used;
    hs[p]++;
    HEAP[p][hs[p]] = 0;
    pushHeap(p);
    
            swQ(1,sQ);
            sQ--;
            downQ();
        }
    }
    //trả xe
    //return if khác k thuê  -> -1
    //if khác thuê và vé chưa hết hạn trả lại 0
    //if khác thuê và vé HẾT hạn trả lại thời gian quá hạn
    int returnBicycle(int cTimestamp,char uName[],int pID){
    Node* tmp = root;
    for (int i = 0; uName[i] != '\0'; ++i) {
    int id = uName[i] - 'a';
    if(tmp->chill[id] == 0) return -1; //không có vé
    tmp = tmp->chill[id];
    }
    if(!tmp->isRent) return -1; //không có thuê
    //trả kho
    int timeU = tmp->timeUsed + (cTimestamp - tmp->timeBegin + 1);
    if(timeU > _durable){
    //bỏ đi
    int timeGiao = cTimestamp + _deliveryTime[pID];
    sQ++;
    H[sQ].timec = timeGiao;
    H[sQ].used = pID;
    upQ(sQ);
    }else{
    hs[pID]++;
    HEAP[pID][hs[pID]] = timeU;
    pushHeap(pID);
    }
    if(cTimestamp <= tmp->validTime) return 0;
    if(cTimestamp > tmp->validTime) {
    return cTimestamp - tmp->validTime;
    }
    }
    
    int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
    }
    
    
    
