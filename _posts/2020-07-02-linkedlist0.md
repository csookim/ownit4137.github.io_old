---
title: "Stack & Queue"
date: 2020-07-03
categories: "Algorithm" # 카테고리
excerpt: "Implementing Stack & Queue in C++"
published : true # 공개

author_profile: false
header:
    teaser: "assets/images/teaser/vs.png"  # 글 위의 이미지

toc: true #Table Of Contents 목차 보여줌
toc_label: " " # toc 이름 정의
toc_icon: " " #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
---



![](/assets/posts/al/aafb2884.png)
<span class="srclink">https://medium.com/x-organization/stack-and-queue-60f365963552</span>


## Stack


### class Stack(array)

- size 고정

{% highlight cpp %}

class Stack {
public:
	int arr[10000];
	int t = -1;

	int empty() {
		if (t == -1) return 1;
		return 0;
	}
	int top() {
		if (empty()) return -1;
		return arr[t];
	}
	void push(int x) {
		arr[++t] = x;
	}
	int pop() {
		if (empty()) return -1;
		return arr[t--];
	}
	int size() {
		return (t + 1);
	}
};

{% endhighlight %}

### class linkedStack(linkedlist)

- 만들어놓은 linkedlist ADT를 사용
- front(head)에서 push, pop이 일어남
- n은 스택의 원소 개수를 나타냄

{% highlight cpp %}

class linkedStack {
private:
	int n;
	SLinkedList* S;
public:
	linkedStack() {
		this->S = new SLinkedList();
		this->n = 0;
	}
	int size() { return n; }
	bool empty() {
		if (size()) return false;
		else return true;
	}
	int top() {
		if (empty()) { return -1; }
		else {
			return S->front();
		}
	}
	void push(int e) {
		S->addFront(e);
		n++;
	}
	int pop() {
		if (empty()) { return -1; }
		else {
			int elem = S->front();
			S->removeFront();
			n--;
			return elem;
		}
	}
};


{% endhighlight %}


## Queue

### class Queue

{% highlight cpp %}

a

{% endhighlight %}


### class Queue

{% highlight cpp %}

a

{% endhighlight %}


a
{: .notice}
