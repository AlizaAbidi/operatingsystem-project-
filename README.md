# 📚 Library Management System (Thread-Synchronized)
A multithreaded Library Management System in C that simulates a *student-librarian interaction* where:
* Students (Readers) view the book catalog.
* Librarians (Writers) can add or remove books.
* Uses Pthreads, Semaphores, and Mutexes to ensure proper synchronization between readers and writers.
  
## 🛠 Features
* 👨‍🏫 Multiple student threads can view the book catalog.
* 👩‍🏫 Librarian threads can safely add/remove books without conflict.
* 🔐 Synchronization handled via pthread_mutex_t and sem_t.
* 📄 File-based storage for books and logs.
* 🤵 Simulation of concurrent access using POSIX threads.

## 🧰 Libraries Used
| Library         | Purpose                                       |
| --------------- | --------------------------------------------- |
| <pthread.h>   | POSIX threads to simulate students/librarians |
| <semaphore.h> | Semaphores to synchronize read/write access   |
| <stdio.h>     | File handling and I/O                         |
| <stdlib.h>    | Memory and exit handling                      |
| <string.h>    | String operations                             |

## 👥 How It Works

### 📖 Reader (Student Thread):
* Can view book catalog using viewBookCatalog().
* If a writer is waiting, the student will wait using sem_wait().

### ✍ Writer (Librarian Thread):
* Sets writer_waiting = 1 before modifying catalog.
* Uses addBook() and removeBook() to update books.txt.
* Releases lock after completion.

### ⚖ Synchronization:
* sem_t rw_mutex prevents simultaneous reads/writes.
* pthread_mutex_t mutex ensures mutual exclusion.
* Prevents race conditions and data inconsistency.
  
## 🚀 How to Run

### ✅ Requirements
* GCC compiler
* Linux OS (POSIX-compliant)
* Make utility

### 🔧 Build the Project

Use the Makefile to compile all components:
bash
make


This will generate an executable named library.

### ▶ Run the Executable
bash
./library


### 📋 Menu Options

Library Management System
--------------------------
1. View Book Catalog (Student)
2. Add Book (Librarian)
3. Remove Book (Librarian)
4. Exit

## 📝 Sample Files

### 📚 books.txt
The Great Gatsby
1984
Harry Potter and the Philosopher's Stone


### 📒 log.txt
Book Viewed: 1984
Book Added: Clean Code
Book Removed: The Great Gatsby

