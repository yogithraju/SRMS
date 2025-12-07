#include <stdio.h>
#include <string.h>
#include <time.h>
#include "../include/auth.h"

int login() {
    char user[50], pass[50], role[50];

    printf("Username: ");
    scanf("%s", user);
    printf("Password: ");
    scanf("%s", pass);

    FILE *fp = fopen("data/credentials.txt", "r");
    if (!fp) return 0;

    char u[50], p[50], r[50];

    while (fscanf(fp, "%s %s %s", u, p, r) != EOF) {
        if (strcmp(user, u)==0 && strcmp(pass, p)==0) {
            logLoginHistory(user);
            fclose(fp);
            return 1;
        }
    }

    fclose(fp);
    return 0;
}

void logLoginHistory(char *user) {
    FILE *fp = fopen("data/login_history.txt", "a");

    time_t now = time(NULL);
    fprintf(fp, "%s logged in at %s", user, ctime(&now));

    fclose(fp);
}
