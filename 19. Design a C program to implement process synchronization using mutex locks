#include <pthread.h>
#include <stdio.h>
pthread_mutex_t lock;
void* func1(void* arg) {
    pthread_mutex_lock(&lock);
    printf("Thread 1: Locked\n");
    sleep(5);
    printf("Thread 1: Unlocked\n");
    pthread_mutex_unlock(&lock);
    return NULL;
}
void* func2(void* arg) {
    pthread_mutex_lock(&lock);
    printf("Thread 2: Locked\n");
    sleep(5);
    printf("Thread 2: Unlocked\n");
    pthread_mutex_unlock(&lock);
    return NULL;
}
int main() {
    pthread_t thread1, thread2;
    pthread_mutex_init(&lock, NULL);
    pthread_create(&thread1, NULL, func1, NULL);
    pthread_create(&thread2, NULL, func2, NULL);
    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);
    pthread_mutex_destroy(&lock);
    return 0;
}
