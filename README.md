# C_Class_190823
Parity bit


#include <stdio.h>
void main()
{
	int d, m, n, c = 0, dd, p, x = 10000000;
	// 8bit는 8자리이므로 x = 1000,0000 8자리수로 나누어준다.
	scanf_s("%d", &d);
	dd = d; //입력 초기값은 임의로 dd에 넣어둔다. (d의 값이 바뀔 수 있기 때문에?)
	do
	{
		m = d / x; // m 은 8비트숫자(10101100) 에서 x로 나눈 몫
		n = d % x; // n 은 8비트숫자(10101100) 에서 x로 나눈 나머지 
		if (m == 1)c++; // 맨 앞자리가 1이면 증가, 0이면 그대로
		d = n; // d에 나머지 값인 n 을 넣어둔다.
		x /= 10; /* 8자리수의 맨 앞자리를 알기 위해서는 x=1000,0000 를 나누어 알고
				 그 다음 8자리수의 맨 앞자리를 알기 위해 x=100,0000를 나누어 알고
				 그 다음 7자리수의 맨 앞자리를 알기 위해 x=10,0000를 나누어 알고
				 계속 반복해서
				 1의 자리수를 알기 까지 x/10 의 값으로 계속 나누어 준다.
				 */
	} while (n != 0); // 나눌것이 없어지면 반복 종료
	p = dd * 10; // parity 값은 9자리수 이므로 dd에서 10을 곱해서 마지막 자리수를 0으로 만들어 준다.
	if (c % 2 == 0) p += 1; // c = 1의 자리 수, 짝수면 p는 1 증가 (parity 값이 1이 된다.)
	printf("\nsource : %d \nparity bit : %d \n", &dd, &p);
}
