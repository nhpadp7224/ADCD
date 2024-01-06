#include <stdio.h>
#include <stdlib.h>
#include <conio.h>

#define RESET   "\x1B[0m"
#define RED     "\x1B[31m"
#define GREEN   "\x1B[32m"
#define YELLOW  "\x1B[33m"
#define BLUE    "\x1B[34m"
#define MAGENTA "\x1B[35m"
#define CYAN    "\x1B[36m"
#define WHITE   "\x1B[37m"

void clearScreen() {
    system("cls");
}

void changeMenuColor(int choice) {
    switch (choice % 6) {
        case 0:
            printf(RED);
            break;
        case 1:
            printf(GREEN);
            break;
        case 2:
            printf(YELLOW);
            break;
        case 3:
            printf(BLUE);
            break;
        case 4:
            printf(MAGENTA);
            break;
        case 5:
            printf(CYAN);
            break;
        default:
            break;
    }
}

void printIcon() {
    printf("      / \\ \n");
    printf("     / _ \\ \n");
    printf("    | / \\ | \n");
    printf("   | / _ \\ | \n");
    printf("  | | / \\ | | \n");
    printf(" | | / _ \\ | | \n");
    printf("|_|_|/_\\_|_|_| \n");
}

void menuFunction1() {
    clearScreen();
    changeMenuColor(1);
    printf("Chức năng 1\n");
    printIcon();
    printf("Nội dung chức năng 1\n");
    changeMenuColor(1);
}

// Thêm các chức năng khác tại đây

int main() {
    int choice = 1;
    int key;

    do {
        clearScreen();

        // Hiển thị menu lựa chọn
        printf("========== MENU ==========\n");
        for (int i = 1; i <= 10; ++i) {
            if (i == choice) {
                changeMenuColor(choice);
                printf("> ");
            }
            printf("%d. Chức năng %d\n", i, i);
            changeMenuColor(0);  // Reset màu
        }
        printf("11. Thoát\n");
        printf("===========================\n");

        // Đọc phím bấm từ người dùng
        key = getch();

        // Xử lý phím bấm
        switch (key) {
            case 72:  // Phím lên
                choice = (choice > 1) ? choice - 1 : 11;
                break;
            case 80:  // Phím xuống
                choice = (choice < 11) ? choice + 1 : 1;
                break;
            case 13:  // Phím Enter
                if (choice != 11) {
                    // Chỉ thực hiện chức năng khi không phải là thoát
                    switch (choice) {
                        case 1:
                            menuFunction1();
                            break;
                        // Thêm các chức năng khác tại đây
                        default:
                            break;
                    }
                    // Dừng chương trình để người dùng đọc thông báo
                    printf("\nNhấn Enter để tiếp tục...");
                    getchar();
                    getchar();
                }
                break;
            default:
                break;
        }

    } while (key != 27);  // 27 là mã ASCII cho phím Escape

    return 0;
}
