# Assignment-no-3

No:1

#include <stdio.h> int checkPrimeNumber(int number) { int i, f = 1; for (i = 2; i <= number / 2; ++i) {

	if (number % i == 0) {
		f = 0;
		break;
	}
}

return f;
}

int main() {

int num1 = 2, num2 = 10, j, f;

printf("Prime numbers between %d and %d are: ", num1,
	num2);
for (j = num1; j < num2; ++j) 
{
	f = checkPrimeNumber(j);

	if (f == 1) 
	{
		printf("%d ", j);
	}
}

return 0;
}

N0:2

#include <stdio.h> int checkPrime(int n); int main() { int n, i, flag = 0; printf("Enter a positive integer: "); scanf("%d", &n);

for (i = 2; i <= n / 2; ++i) { if (checkPrime(i) == 1) { if (checkPrime(n - i) == 1) { printf("%d = %d + %d\n", n, i, n - i); flag = 1; } } }

if (flag == 0) printf("%d cannot be expressed as the sum of two prime numbers.", n);

return 0; }

int checkPrime(int n) { int i, isPrime = 1; if (n == 0 || n == 1) { isPrime = 0; } else { for(i = 2; i <= n/2; ++i) { if(n % i == 0) { isPrime = 0; break; } } }

return isPrime; }

No:3

#include <stdio.h> int findGCD(int num1, int num2) { if(num2 == 0) { return num1; } else { return findGCD(num2, num1 % num2); } } int main() { int num1, num2, gcd; printf("Enter two numbers: "); scanf("%d %d", &num1, &num2); gcd = findGCD(num1, num2); printf("The GCD of %d and %d is %d", num1, num2, gcd); return 0; }

No:4

#include <stdio.h>

int main() {

int n1, n2, max;

printf("Enter two positive integers: ");
scanf("%d %d", &n1, &n2);

max = (n1 > n2) ? n1 : n2;

while (1) {
    if ((max % n1 == 0) && (max % n2 == 0)) {
        printf("The LCM of %d and %d is %d.", n1, n2, max);
        break;
    }
    ++max;
}
return 0;
}

No:5

#include <stdio.h> #include <string.h>

char string1[100], visited[100]; int count[100] = {0}, flag = 0;

void main() { int i, j = 0, k = 0, l, max, index;

printf("Enter a string : ");
scanf("%[^\n]s", string1);

l = strlen(string1);

for (i = 0; i < l; i++)
{
    if (i == 0)
    {
        visited[j++] = string1[i];
        count[j - 1]++;
    }
    else
    {
        for (k = 0; k  < j; k++)
        {
            if (string1[i] == visited[k])
            {
                count[k]++;
                flag = 1;
            }
        }
        if (flag == 0)
        {
            visited[j++] = string1[i];
            count[j - 1]++;
        }
        flag = 0;
    }
}    

for (i = 0; i < j; i++)
{
    if ((i == 0) && (visited[i] != ' '))
    {
        max = count[i];
        continue;
    }
    if ((max < count[i]) && (visited[i] != ' '))
    {
        max = count[i];
        index = i;
    }
}

printf("\nMax repeated character in the string = %c ", visited[index]);
printf("\nIt occurs %d times", count[index]);
}

No:6

#include <stdio.h>

int find_anagram(char [], char []);

int main() { char array1[100], array2[100]; int flag;

printf("Enter the string\n");
gets(array1);
printf("Enter another string\n");
gets(array2);
flag = find_anagram(array1, array2);
if (flag == 1)
    printf("%s and %s are anagrams.\n", array1, array2);
else
    printf(" %s and %s are not anagrams.\n", array1, array2);
return 0;
}

int find_anagram(char array1[], char array2[]) { int num1[26] = {0}, num2[26] = {0}, i = 0;

while (array1[i] != '\0')
{
    num1[array1[i] - 'a']++;
    i++;
}
i = 0;
while (array2[i] != '\0')
{
    num2[array2[i] -'a']++;
    i++;
}
for (i = 0; i < 26; i++)
{
    if (num1[i] != num2[i])
        return 0;
}
return 1;
}

No:7

#include <stdio.h> #include <string.h>

void main() { int sum = 0, i, len; char string1[100];

printf("Enter the string : ");
scanf("%[^\n]s", string1);
    len = strlen(string1);
for (i = 0; i < len; i++)
{
    sum = sum + string1[i];
}
printf("\nSum of all characters : %d ",sum);
}

No:8

#include <stdio.h> #include <string.h>

void swap(char* x, char* y) { char temp; temp = *x; *x = *y; y = temp; } void permute(char a, int l, int r) { int i; if (l == r) printf("%s\n", a); else { for (i = l; i <= r; i++) { swap((a + l), (a + i)); permute(a, l + 1, r); swap((a + l), (a + i)); } } }

int main() { char str[] = "ABC"; int n = strlen(str); permute(str, 0, n - 1); return 0; }

No:9

#include <stdio.h>

#define MAX_SIZE 100

void printArray(int arr[], int size);

int main() { int source_arr[MAX_SIZE], dest_arr[MAX_SIZE]; int size, i;

int *source_ptr = source_arr;   
int *dest_ptr   = dest_arr;     

int *end_ptr;

printf("Enter size of array: ");
scanf("%d", &size);
printf("Enter elements in array: ");
for (i = 0; i < size; i++)
{
    scanf("%d", (source_ptr + i));
}

end_ptr = &source_arr[size - 1];

printf("\nSource array before copying: ");
printArray(source_arr, size);

printf("\nDestination array before copying: ");
printArray(dest_arr, size);



while(source_ptr <= end_ptr)
{
    *dest_ptr = *source_ptr;

    source_ptr++;
    dest_ptr++;
}

printf("\n\nSource array after copying: ");
printArray(source_arr, size);

printf("\nDestination array after copying: ");
printArray(dest_arr, size);


return 0;
}

void printArray(int *arr, int size) { int i;

for (i = 0; i < size; i++)
{
    printf("%d, ", *(arr + i));
}
}

No:10

#include <stdio.h> #include <string.h> void reverseString(char* str) { int l, i; char *begin_ptr, *end_ptr, ch; l = strlen(str); begin_ptr = str; end_ptr = str + l - 1; for (i = 0; i < (l - 1) / 2; i++) { ch = *end_ptr; *end_ptr = *begin_ptr; *begin_ptr = ch; begin_ptr++; end_ptr--; } }

int main() {

char str[100] = "GeeksForGeeks";
printf("Enter a string: %s\n", str);
reverseString(str);
printf("Reverse of the string: %s\n", str);

return 0;
}
