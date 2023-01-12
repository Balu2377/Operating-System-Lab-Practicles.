#include <stdio.h>
#include <dirent.h>

int main(int argc, char* argv[]) {
    // Open the directory
    char* dir_name = ".";
    if (argc == 2) {
        dir_name = argv[1];
    }
    DIR* dir = opendir(dir_name);
    if (dir == NULL) {
        perror("Error opening directory");
        return 1;
    }

    // Read the contents of the directory
    struct dirent* dir_entry;
    while ((dir_entry = readdir(dir)) != NULL) {
        printf("%s\n", dir_entry->d_name);
    }

    // Close the directory
    closedir(dir);
    return 0;
}
