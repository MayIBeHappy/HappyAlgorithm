
# ✏️ 문제 제목 (문제 번호)
- [동물원](https://www.acmicpc.net/problem/1309)

## 💡 풀이한 코드
```java
	public static void main(String[] args) throws IOException {
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	int n = Integer.parseInt(br.readLine());

	int[] dp = new int[100001];
	dp[0] = 1;
	dp[1] = 3;
	for (int i = 2; i <= n; i++) {
		dp[i] = (2*dp[i-1] + dp[i-2]) % 9901;
	}

	System.out.println(dp[n]%9901);
}
	
```
## 📖 풀이 내용
1. 새롭게 값이 추가되면, 사자가 들어오지 않는 경우+ 사자가 한쪽에 들어오는 케이스로 나눠서 풀이함
2. 사자가 한쪽에 들어오는 케이스를 보면 어쨌든 이전 결과 + 이전에 사자가 두쪽에 들어오지 않았떤 경우, 즉 여집합을 만들어서 문제를 풀이하려고 함
3. 사실 이거 생각하다가 문제가 쉬워서 점화식 만들어냄..
--- 

## 소감
이걸 스터디하면서 설명을 계속 못하고 감으로 푸니까 너무 열받았음.. <br>
그래도 이전 결과를 바탕으로 어떻게 다음을 해석해 나갈지 생각하기에 아주 좋은 dp 케이스였다.

