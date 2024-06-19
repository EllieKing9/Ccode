# Ccode
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
