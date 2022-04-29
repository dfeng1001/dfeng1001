- 👋 Hi, I’m @dfeng1001
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
dfeng1001/dfeng1001 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

//数据结构之线性表的数组存储方法
#include<stdio.h>
#include <stdlib.h>
typedef int Elemtype;
typedef struct Slist {
	Elemtype* a;
	int size;
	int capacity;

}sl;
void initsl(sl* ps) {
	
	
	ps->a = NULL;
	ps->capacity = 0;
	ps->size = 0;
	
}
void check(sl* ps) {
	if (ps->capacity == ps->size) {
		int tmp = ps->capacity == 0 ? 4 : ps->capacity * 2;
		Elemtype* m = (Elemtype*)realloc(ps->a,tmp*sizeof(Elemtype));
		ps->a = m;
		ps->capacity = tmp;
	}
	
}
void pushback(sl* ps,Elemtype x) {
	check(ps);
	ps->a[ps->size] = x;
	ps->size++;

}

void print(sl p) {
	for (int i = 0; i < p.size; i++) {
		printf("%d ", p.a[i]);

	}
	printf("\n"); 

}
void pushfront(sl* ps,Elemtype x) {
	check(ps);
	int end = ps->size;
	for (int i = end; i > 0; i--) {
		ps->a[i] = ps->a[i - 1];
	}
	ps->a[0] = x;
	ps->size++;

}
void popback(sl* ps) {
	if (ps != NULL) {
		ps->size--;
	}
}
void popfront(sl* ps) {
	for (int i = 0; i < ps->size; i++) {
		ps->a[i] = ps->a[i + 1];
	}
	ps->size--;
}
void insert(sl* ps, int pos, Elemtype x) {
	for (int i = ps->size; i >=pos; i--) {
		ps->a[i] = ps->a[i - 1];
	}
	ps->a[pos - 1] = x;
	ps->size++;
}
void erase(sl* ps, int pos) {
	for (int i = ps->size - 1; i >= pos; i--) {
		ps->a[i - 1] = ps->a[i];
	}
	ps->size--;
}
void delect(sl* ps) {
	free(ps);
	ps->a = NULL;
	ps->capacity = ps->size = 0;
}
Elemtype find(sl s, Elemtype x) {
	for (int i = 0; i < s.size; i++) {
		if (s.a[i] == x)
			return i;
	}
}
int main(){
	sl t;
	initsl(&t);
	pushback(&t,1);
	pushback(&t,2);
	pushback(&t,3);
	pushback(&t, 1);
	pushback(&t, 2);
	pushback(&t, 3);
	pushfront(&t, 100);
	Elemtype x=find(t, 3);
	print(t);
	printf("%d ", x);
	/*popback(&t);
	popback(&t);
	
	popfront(&t);
	print(t);
	insert(&t, 2, 300);
	print(t);
	erase(&t, 2);
	print(t);*/
	return 0;
}
