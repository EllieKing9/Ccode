# Ccode

```
https://blockdmask.tistory.com/391
```

문자열 복사
```
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

// 파라미터로 주어지는 문자열은 const로 주어집니다. 변경하려면 문자열을 복사해서 사용하세요.
char* solution(const char* my_string, int n) {
    // return 값은 malloc 등 동적 할당을 사용해주세요. 할당 길이는 상황에 맞게 변경해주세요.

    char *answer;
    if(answer = (char *)malloc((sizeof(char) * n) + 1)) {
        memset(answer, 0x00, (sizeof(char) * n) + 1);
        strncpy(answer, my_string, n);
    }
    else {
        printf("size overflow");
    }
    
    return answer;
}
```
문자열 정렬하기 숫자(qsort)
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int compare(const void *a, const void *b) {
    // return *(int *)a - *(int *)b; //작은순서
    return *(int *)b - *(int *)a; //큰순서
}

int* solution(const char* my_string) {
    printf("%s\n", my_string);
    int totCnt = 0;
    int* temp = (int*)malloc(sizeof(int) * strlen(my_string));
    
    for(int i = 0; i < strlen(my_string); i++) {
        if(my_string[i] >= '0' && my_string[i] <= '9') {
            temp[totCnt] = my_string[i] - 48;
            totCnt = totCnt + 1;
        }
    }
    printf("totCnt: %d \n", totCnt);
    int *answer = (int *)malloc(sizeof(int) * totCnt);
    memcpy(answer, temp, sizeof(int) * totCnt);
    free(temp);
    
    for(int i = 0; i < totCnt; i++) {
        printf("%d", answer[i]);
    }
    printf("\n");

    qsort(answer, totCnt, sizeof(int), compare);
    
    // for(int i = 0; i < totCnt; i++) {
    //     for(int j = 0; j < totCnt; j++) {
    //         if(answer[i] < answer[j]) {
    //             int temp = answer[i];
    //             answer[i] = answer[j];
    //             answer[j] = temp;
    //         }
    //     }
    // }

    for(int i = 0; i < totCnt; i++) {
        printf("%d", answer[i]);
    }
    
    return answer;
}

int main() {
    char s1[7] = "hu12392";
  
    solution(s1);

    return 0;
}
```
문자열 정렬하기 숫자
```
int* solution(const char* my_string) {
    int totCnt = 0;
    int* answer = (int*)malloc(sizeof(int) * strlen(my_string));
    
    for(int i = 0, j = 0; i < strlen(my_string); i++) {
        if(my_string[i] >= '0' && my_string[i] <= '9') {
            answer[j] = my_string[i] - 48;
            totCnt = totCnt + 1;
            ++j;
        }
    }
    printf("totCnt: %d ", totCnt);
    // int* answer = (int*)malloc(sizeof(int) * totCnt);
    
    for(int i = 0; i < totCnt; i++) {
        for(int j = 0; j < totCnt; j++) {
            if(answer[i] < answer[j]) {
                int temp = answer[i];
                answer[i] = answer[j];
                answer[j] = temp;
            }
        }
    }
    // return 값은 malloc 등 동적 할당을 사용해주세요. 할당 길이는 상황에 맞게 변경해주세요.
    return answer;
}
```
대소문자 변환
```
#include <stdio.h>
#define LEN_INPUT 10

int main(void) {
    char s1[LEN_INPUT];
    scanf("%s", s1);

    for(int i = 0; i < strlen(s1); i++) {
        if(isupper(s1[i])) {
            // printf("%c ", s1[i]);
            s1[i] = tolower(s1[i]);
            // printf("%c", s1[i]);
        }
        else if(islower(s1[i])) {
            // printf("%c ", s1[i]);
            s1[i] = toupper(s1[i]);
            // printf("%c", s1[i]);
        }
        // printf("%d ", s1[i]); // +- 32
    }
    
    printf("%s", s1);
    return 0;
}
```
최빈값구하기
```
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

// array_len은 배열 array의 길이입니다.
int solution(int array[], size_t array_len) {
    int answer = 0;
    
    int bestItem = 0;
    int bestItemCnt = 0;
    
    int item = 0;
    int itemCnt = 0;
    
    for(int i = 0; i < array_len; i++) {
        if(item != array[i]) {
            itemCnt = 0;
            
            for(int j = 0; j < array_len; j++) {
                if(array[i] == array[j]) {
                    itemCnt = itemCnt + 1;
                }
            }
            
            if(itemCnt > bestItemCnt) {
                bestItemCnt = itemCnt;
                bestItem = item = array[i];
            }
            else if(itemCnt == bestItemCnt) {
                bestItem = -1;
            }
        }
    }
    
    answer = bestItem;
    return answer;
}
```
문자열 기본
```
#include <stdio.h>
#define LEN_INPUT 1000001

#include <stdlib.h>

int main(void) {
    char s1[LEN_INPUT];
    scanf("%s", s1);
    
    // printf("%s", ptr_s2);
    
    // char *ptr_s2 = (char *)malloc(strlen(s1));
    // memcpy(ptr_s2, s1, sizeof(s1));
    char *ptr_s2 = s1;
    // char *ptr_s2 = &s1;
    // strcpy(ptr_s2, s1);
    // printf("%s\n", ptr_s2);

    // printf("%d\n", strlen(s1));
    // printf("%d\n", strlen(ptr_s2));
    // printf("%d\n", sizeof(s1));
    // printf("%d\n", sizeof(ptr_s2));
    // printf("%x\n", &ptr_s2);
    // printf("%x\n", ptr_s2);
    // printf("%x\n", s1);
    // printf("%d\n", sizeof(char));
    // printf("%d\n", sizeof(int));
    
    for(int i = 0; i < strlen(ptr_s2); i++) {
        printf("%c", ptr_s2[i]);
    }
    
    // free(ptr_s2);
    return 0;
}
```
주식가격 스택
```
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

// prices_len은 배열 prices의 길이입니다.
int* solution(int prices[], size_t prices_len) {
    printf("%d\n", prices_len);
    
    int* answer = (int*)malloc(prices_len * sizeof(int));
    int* stack = (int*)malloc(prices_len * sizeof(int));
    int top = -1; // 스택의 top 인덱스
    
    for (int i = 0; i < prices_len; ++i) {
        while (top >= 0 && prices[stack[top]] > prices[i]) {
            // 가격이 떨어지는 시점 계산
            answer[stack[top]] = i - stack[top];
            top--; //(1, 3)
        }
        // 현재 인덱스 push
        top = top + 1;
        stack[top] = i; // (0, 0) (1, 1) (2, 2) - (2, 3)
    }
    
    // 스택에 남아있는 것들 처리 (가격이 떨어지지 않은 기간을 계산할 수 없는 경우)
    while (top >= 0) {
        answer[stack[top]] = prices_len - stack[top] - 1;
        top--;
    }
    
    free(stack);
    
    return answer;
}
```
괄호 스택
```
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

// 파라미터로 주어지는 문자열은 const로 주어집니다. 변경하려면 문자열을 복사해서 사용하세요.
bool solution(const char* s) {
    bool answer = true;
    int *stack = (int *)malloc(sizeof(char) * strlen(s));
    int top = -1;
    
    int len = strlen(s);
    // printf("%d\n", len);
    
    for(int i = 0; i < len; i++) {
        if(s[i] == '(') {
            top = top + 1;
            stack[top] = '(';
        }
        else if(s[i] == ')') {
            if(top == -1) {
                answer = false;
                return answer;
            }
            else {
                top = top - 1;
            }
        }
    }
    
    if(top >= 0) {
        answer = false;
    }
        
    return answer;
}
```
DFS
```
#include <stdlib.h>
#define MAX 4

int visited[MAX] = {0};
int graph[MAX][MAX] = {
    {0,1,1,0},
    {1,0,0,1},
    {1,0,0,0},
    {0,1,0,0}};

void dfs(int v) {
    visited[v] = 1;
    for(int i = 0; i < MAX; i++) {
        if(graph[v][i] == 1 && !visited[i]) {
            dfs(i);
        }
    }
}

int main(void) {
    dfs(0);
    return 0;
}
```
BFS
```
typedef int ELEMENT;
typedef struct {
    ELEMENT data[MAX];
    int front, rear;
}QUEUE;

void initQueue(QUEUE *q) {
    q->rear = q->front = 0;
}
int isFull(QUEUE *q) {
    return((q->rear + 1) % MAX_Q == q->front);
}
int isEmpty(QUEUE *q) {
    return(q->front == q->rear);
}
void enQueue(QUEUE *q, ELEMENT item) {
    if(isFull(q)) {
        return 0;
    }
    q->rear = (q->rear + 1) % MAX_Q;
    q->data[q->rear] = item;
}
ELEMENT dequeue(QUEUE *q) {
    if(isEmpty(q) {
        exit(1);
    }
    q->front = (q->front + 1) % MAX_Q;
    return q->data[q->front];
}

void bfs(GRAPH *g, int start) {
    QUEUE q;
    initQueue(&q);
    visited[start] = 1;
    GRAPH *m = (GRAPH *)malloc(sizeof(GRAPH));
    m = g;
    enQueue(&q, start);

    while(!isEmpty(&q)) {
        int v = deQueue(&q);
        for(int i = 0; i < MAX; i++) {
            if(m[v][i] && visited[i]) {
                visited[i] = 1;
                enQueue(&q, i);
            }
        }
    }
}
```
