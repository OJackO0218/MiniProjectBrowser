```c
#include <stdio.h>
#include <string.h>


#define MAX 100
#define URL_LEN 100

typedef struct {
    char data[MAX][URL_LEN];
    int top;
} Stack;


void init(Stack *s) {
    s->top = -1;
}

int isEmpty(Stack *s) {
    return s->top == -1;
}

void push(Stack *s, char url[]) {
    if (s->top < MAX - 1) {
        s->top++;
        strcpy(s->data[s->top], url);
    }
}

void pop(Stack *s, char result[]) {
    if (!isEmpty(s)) {
        strcpy(result, s->data[s->top]);
        s->top--;
    }
}

void clear(Stack *s) {
    s->top = -1;
}

void display(Stack *s) {
    for (int i = s->top; i >= 0; i--) {
        printf("%s ", s->data[i]);
    }
    printf("\n");
}

int main() {
    Stack backStack, forwardStack;
    char current[URL_LEN] = "Home";
    char temp[URL_LEN];
    int choice;

    init(&backStack);
    init(&forwardStack);

    while (1) {
        printf("\n=== Browser History ===\n");
        printf("Current Page: %s\n", current);
        printf("1. Visit Page\n");
        printf("2. Back\n");
        printf("3. Forward\n");
        printf("4. Show History\n");
        printf("5. Exit\n");
        printf("Choose: ");
        scanf("%d", &choice);

        if (choice == 1) {
            printf("Enter URL: ");
            scanf("%s", temp);

            push(&backStack, current);
            strcpy(current, temp);
            clear(&forwardStack);

            printf("Visited: %s\n", current);
        }
        else if (choice == 2) {
            if (isEmpty(&backStack)) {
                printf("No page to go back to\n");
            } else {
                push(&forwardStack, current);
                pop(&backStack, current);
                printf("Back to: %s\n", current);
            }
        }
        else if (choice == 3) {
            if (isEmpty(&forwardStack)) {
                printf("No page to go forward to\n");
            } else {
                push(&backStack, current);
                pop(&forwardStack, current);
                printf("Forward to: %s\n", current);
            }
        }
        else if (choice == 4) {
            printf("Current: %s\n", current);

            printf("Back Stack: ");
            display(&backStack);

            printf("Forward Stack: ");
            display(&forwardStack);
        }
        else if (choice == 5) {
            break;
        }
        else {
            printf("Invalid choice\n");
        }
    }

    return 0;
}

```
