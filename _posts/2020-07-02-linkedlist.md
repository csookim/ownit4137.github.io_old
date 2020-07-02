---
title: "Linked List"
date: 2020-07-02
categories: "Algorithm" # 카테고리
excerpt: "Implementing a Linked List in C++"
published : true # 공개

author_profile: false
header:
    teaser: "assets/images/teaser/vs.png"  # 글 위의 이미지

toc: true #Table Of Contents 목차 보여줌
toc_label: " " # toc 이름 정의
toc_icon: " " #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
---



![](/assets/posts/al/86223188.png)
<span class="srclink">https://www.faceprep.in/data-structures/linked-list-introduction/</span>


## Singly Linked List


### class Node

- Node(int e) : e값을 가지는 Node 생성


{% highlight cpp %}

class Node {
public:
	Node(int e) {
		elem = e;
		this->next = NULL;
	}
private:
	int elem;
	Node* next;

	friend class SLinkedList;  //friend
};

{% endhighlight %}

### class SLinkedList

- addFront(int x) : newNode 생성 -> 연결
- addBack(int x) : newNode 생성 -> 연결
- removeFront() : head 노드를 old 노드에 복사 -> 연결 끊기 -> delete
- front() : return head->elem;
- empty() : return head==NULL;
- showList() : do traverse using cur pointer

{% highlight cpp %}

class SLinkedList {
private:
	Node* head;
	Node* tail;
public:
	SLinkedList() :head{ NULL }, tail{ NULL } {}

	void addFront(int x) {
		Node* newNode = new Node(x);
		if (empty()) head = tail = newNode;
		else {
			newNode->next = head;
			head = newNode;
		}
	}
	void addBack(int x) {
		Node* newNode = new Node(x);
		if (empty()) head = tail = newNode;
		else {
			tail->next = newNode;
			tail = newNode;
		}
	}
	int removeFront() {
		if (empty()) return -1;
		Node* old = head;
		head = old->next;
		int oldelem = old->elem;
		delete old;
		return oldelem;
	}
	int front() {
		if (empty()) return -1;
		return head->elem;
	}
	int empty() { return head == NULL; }
	void showList() {
		if (empty()) { cout << -1; return; }
		for (Node* cur = head; cur != NULL; cur = cur->next) {
			cout << cur->elem << " ";
		}
	}
};

{% endhighlight %}

## Doubly Linked List

## Circular Linked List

### class Node

{% highlight cpp %}

class Node {
public:
	Node(int e) {
		elem = e;
		this->next = NULL;
	}
private:
	int elem;
	Node* next;

	friend class CLinkedList;
};

{% endhighlight %}


### class CLinkedList

- addFront() : newNode 생성 -> 연결
- addBack() : newNode 생성 -> 연결
- remove(int idx) : 삭제할 노드와 **그 전 노드** 를 가리킴 -> head/tail 갱신 -> 연결 -> 삭제
- showList() : do traverse, p가 tail이면 반복문 종료

{% highlight cpp %}

class CLinkedList {
public:
	CLinkedList() {
		head = NULL;
		tail = NULL;
	}
	void addFront(int x) {
		Node* newNode = new Node(x);
		if (empty()) {
			head = newNode;
			tail = newNode;
			newNode->next = head;
		}
		else {
			newNode->next = head;
			tail->next = newNode;
			head = newNode;
		}
	}
	void addBack(int x) {
		Node* newNode = new Node(x);
		if (empty()) {
			head = newNode;
			tail = newNode;
			newNode->next = head;
		}
		else {
			newNode->next = head;
			tail->next = newNode;
			tail = newNode;
		}
	}
	void remove(int idx) {
		Node* old = head;
		Node* prev = tail;
		for (int id = 0; id < idx; id++) {
			old = old->next;
			prev = prev->next;
		}
		if (old == head) head = old->next;
		if (old == tail) tail = prev;
		prev->next = old->next;
		delete old;
	}
	void showList() {
		for (Node* p = head;; p = p->next) {
			cout << p->elem << " ";
			if (p == tail) break;
		}
	}
	int empty() { return head == NULL; }
private:
	Node* head;
	Node* tail;
};

{% endhighlight %}



삽입을 구현할 때, 빈 리스트(head == NULL or tail == NULL)는 따로 처리
{: .notice}
