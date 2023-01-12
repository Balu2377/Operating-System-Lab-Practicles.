#include <stdio.h>
#include <pthread.h>
#include <semaphore.h>

#define BUFFER_SIZE 10

sem_t full, empty;
int buffer[BUFFER_SIZE];
int in = 0, out = 0;

void *producer(void *arg) {
    while (1) {
        int item = (int) arg;
        sem_wait(&empty);
        buffer[in] = item;
        printf("Produced item: %d\n", item);
        in = (in + 1) % BUFFER_SIZE;
        sem_post(&full);
    }
    return NULL;
}

void *consumer(void *arg) {
    while (1) {
        sem_wait(&full);
        int item = buffer[out];
        printf("Consumed item: %d\n", item);
        out = (out + 1) % BUFFER_SIZE;
        sem_post(&empty);
    }
    return NULL;
}

int main() {
    sem_init(&full, 0, 0);
    sem_init(&empty, 0, BUFFER_SIZE);

    pthread_t p, c;
    pthread_create(&p, NULL, producer, (void *) 1);
    pthread_create(&c, NULL, consumer, NULL);

    pthread_join(p, NULL);
    pthread_join(c, NULL);

    sem_destroy(&full);
    sem_destroy(&empty);

    return 0;
}
