# ✏️ 문제 제목 (문제 번호)
- [Fly Me To The Alpha Centauri](https://www.acmicpc.net/problem/1011)

## 💡 풀이한 코드
```java
public static void main(String[] args) throws IOException {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

	int t = Integer.parseInt(br.readLine());
	for (int i = 0; i < t; i++) {
		String[] inputs = br.readLine().split(" ");
		int start = Integer.parseInt(inputs[0]);
		int end = Integer.parseInt(inputs[1]) - start - 1;
		start = 0;
		if(end-start==1) {
			System.out.println(1);
			continue;
		}

		int[][] dp = new int[end+1][3];
		dp[0][0] = 0;
		dp[1][0] = 1;
		for (int j = 1; j < end; j++) {
			for (int k = 0; k < end; k++) {
				dp[j][k] += Math.min(Math.min(dp[j-1][],dp[j][]),dp[j+1][])+1;
			}

		}
		bw.write(dp[end]);
		bw.close();
		br.close();
	}
}
	0 0 0 0 0 0 0 0 0
		0->1  2->3
		1->2 칸수만 계산하면된다
	0->4 네칸짜리를 가는 경우의수를 계삲ㄴ다.
닷서칸 짜리르 가는 경우의수를 게산한.....

	0 1
	1 2 3
	2 3 4
	3 4 5
	4 5 6


```
## 📖 풀이 내용
• 사용한 알고리즘 유형: DP <br>
• 시간 복잡도: O(n) <br>
• 주요 풀이 과정: <br>
    1. 1부터 시작, 끝날 때도 => 숫자의 진행이 증가했다가 감소하는 형태를 띈다.  <br>
    2. 시작점과 끝점의 상대적인 위치는 상관 없다. 그저 절대적인 거리값이 중요 <br>
    3. 거리, 최대값, 진행 가능 경우의 수, 이동횟수 등을 표로 정리해서 규칙을 우선적으로 찾기 <br>
• 그림/표 (선택 사항)

| 거리 | 이동 횟수 | 진행 가능한 경우의 수 | 최대값 |
|----|-------|--------------|-----|
| 1  | 1     | 1            | 1   |
| 2  | 2     | 1 1          | 1   |
| 4  | 3     | 1 2 1        | 2   |
| 6  | 4     | 1 2 2 1      | 2   |
...

이런 식으로 값이 증가하면서
- max값이 1씩 증가하는 구간이 2번씩 반복
- 현재 거리 - 이전거리 = max 증가 값과 동일
- max 가 변하는 최대 거리는 max의 제곱

해당 규칙을 잘 풀어서 구현하면 됨..

## 오답 소감
음 감도못잡고 굉장히 복잡해지는 문제였음. DP라는 내용을 전제하게 되면서 문제에 대한 규칙과 점화식을 찾기 위한 노력만 거듭했음
앞으로는 dp유형 같은 경우는 최대한 많은 표와 그림을 통해서, 그리고 예외조건을 찾기 위한 폭넓은 시도로 답을 낸 후에 DP로 접근하는게 조금 더 옳은 방법이라는 생각이 들음
가장 어려운 문제 유형이었던 만큼 반복해서 풀어보기, (생각보다 규칙찾기, 그리고 구현과정이 간결해보이지만 많이 생각해야만 할 수 있는 것들이라는 거 명심하기)
