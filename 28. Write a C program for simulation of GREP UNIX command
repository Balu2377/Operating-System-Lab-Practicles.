#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[]) {
    if (argc != 3) {
        printf("Usage: %s pattern file\n", argv[0]);
        return 1;
    }

    char *pattern = argv[1];
    char *file_name = argv[2];

    FILE *file = fopen(file_name, "r");
    if (file == NULL) {
        printf("Error: Could not open file %s\n", file_name);
        return 1;
    }

    char line[1024];
    while (fgets(line, sizeof(line), file)) {
        if (strstr(line, pattern) != NULL) {
            printf("%s", line);
        }
    }

    fclose(file);
    return 0;
}
