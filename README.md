# MiniProjectBrowser
A Github Repository for Data Structure Mini Project Browser

## Description
This project simulates a simple browser navigation system using Stack (Queue & Dequeue).

It allows users to:
- Visit new pages
- Go back to previous pages
- Go forward to next pages
- View browsing history

## Concepts used
- Stack (Queue)
- Stack (Dequeue)

## How It Works
When visiting a new page:
  - Current page is pushed into back stack
  - Forward stack is cleared
When going back:
  - Current page moves to forward stack
  - Previous page is popped from back stack
When going forward:
  - Currwnt page moves to back stack
  - Page is popped from forward stack

## How to Run
1. Put code inside any C code compiler.
2. Compile & Run.
3. Input 1, 2, 3, or 4 to navigate through the browser, input 5 to exit.
4. Enjoy.
