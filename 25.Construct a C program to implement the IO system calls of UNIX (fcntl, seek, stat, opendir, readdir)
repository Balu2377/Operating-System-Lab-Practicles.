#include <fcntl.h>
#include <sys/stat.h>
#include <unistd.h>
#include <dirent.h>
#include <stdio.h>

int main() {
    // Use fcntl to set file descriptor to non-blocking mode
    int fd = open("file.txt", O_RDONLY);
    int flags = fcntl(fd, F_GETFL, 0);
    fcntl(fd, F_SETFL, flags | O_NONBLOCK);

    // Use lseek to move the file pointer to a specific position
    off_t offset = lseek(fd, 10, SEEK_SET);

    // Use fstat to get information about a file
    struct stat file_stat;
    fstat(fd, &file_stat);
    printf("File size: %lld bytes\n", file_stat.st_size);

    // Use opendir and readdir to list files in a directory
    DIR* dir = opendir(".");
    struct dirent* dir_entry;
    while ((dir_entry = readdir(dir)) != NULL) {
        printf("%s\n", dir_entry->d_name);
    }
    closedir(dir);

    close(fd);
    return 0;
}
