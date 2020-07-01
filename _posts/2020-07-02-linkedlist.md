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
- removeFront : head 노드를 old 노드에 복사 -> 연결 끊기 -> delete
- front() : return head->elem;
- empty() : return head==NULL;
- showList : do traverse using cur pointer

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
