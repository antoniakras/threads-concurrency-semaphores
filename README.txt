# 📚 Study Room Synchronization with Threads and Semaphores

## 📖 About

This project simulates a **study room for students** using **POSIX threads (pthreads) and semaphores/mutexes** in C. It demonstrates **thread synchronization, critical section management, and FIFO ordering**. Each student is represented by a thread, and the system enforces rules:

- The study room accommodates **up to 8 students** at a time.
- Additional students must **wait in a waiting room** until the study room is empty.
- Students enter the study room in **FIFO order** to prevent starvation.
- Each student has a **random study duration** (5–15 seconds).

This project highlights skills in **concurrent programming, synchronization primitives, and resource management**.

---

## ✨ Features & Technical Highlights

- **Threaded Simulation**
  - Each student is a separate **pthread**.
  - Simulates realistic concurrent behavior.

- **Study Room & Waiting Room**
  - Study room: fixed-size array of 8 slots.
  - Waiting room: dynamically allocated array of pointers to integers, adjusts to number of students.

- **Synchronization**
  - **Mutex** for critical section protection.
  - **Condition variables** to manage student entry/exit.
  - Ensures **FIFO entry** and prevents **starvation**.

- **Random Study Duration**
  - Assigns each student a random study time between 5 and 15 seconds. 

- **Fairness & Concurrency**
  - Demonstrates proper management of **shared resources**.
  - Avoids race conditions and ensures correct order of thread execution.
  - Program ends when all students complete their study session.

---

## 🧩 Implementation Details

- **Critical Section:** Managed using a mutex (`pthread_mutex_t`) to ensure only one student thread modifies the study room at a time.

- **Waiting Room Logic:** When the study room is full, threads wait on a condition variable. Once the room is empty, waiting threads are signaled to enter in arrival order.

- **Randomized Behavior:** Sleep calls simulate study time, demonstrating concurrency handling under non-deterministic durations.

---

## 🛠️ Setup & Run

1. Clone the repository:
   ```bash
   git clone https://github.com/antoniakras/threads-concurrency-semaphores.git
   cd threads-concurrency-semaphores
   make
   ./thread
        Enter the number of students when prompted.
        The program will simulate students entering and leaving the study room according to the rules.
