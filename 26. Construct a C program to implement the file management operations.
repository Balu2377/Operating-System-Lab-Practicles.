#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>

int main() {
    int fd = open("file.txt", O_CREAT | O_RDWR, 0644);
    if (fd == -1) {
        perror("Error creating file");
        exit(1);
    }
    const char* data = "Hello, World!";
    write(fd, data, sizeof(data));
    lseek(fd, 0, SEEK_SET);
    char buffer[100];
    read(fd, buffer, sizeof(buffer));
    printf("Data read from file: %s\n", buffer);
    if (rename("file.txt", "new_file.txt") == -1) {
        perror("Error renaming file");
    }
    if (remove("new_file.txt") == -1) {
        perror("Error deleting file");
    }
    close(fd);
    return 0;
}
