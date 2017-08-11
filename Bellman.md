강화학습
Bellman Equation 
http://www.phrgcm.com/blog/2016/08/05/bellman-eqation/
Bellman Equation

저번에는 Policy와 Value Function에 대해 알아보았다. 이번에는 Bellman Equation을 알아볼 것이다.

Bellan Equation을 알기 위해 먼저 저번에 보았던 Value Function을 보도록 하자.

Vπ(S)=E[Gt|St=s]  (Gt=Rt+1+γRt+2+⋯)Vπ(S)=E[Gt|St=s]  (Gt=Rt+1+γRt+2+⋯)

Value는 결국 GtGt를 나타낸다. GtGt를 다시 한번 써보면 아래와 같이 쓸 수 있다.

Gt=Rt+1+γRt+2+γ2Rt+3+⋯Gt=Rt+1+γRt+2+γ2Rt+3+⋯ 
     =Rt+1+γ(Rt+2+γRt+3+⋯)  =Rt+1+γ(Rt+2+γRt+3+⋯)
     =Rt+1+γGt+1  =Rt+1+γGt+1
GtGt를 위와 같이 나타내면 Value또한 위의 식을 이용해 아래와 같이 나타낼 수 있다.

Vπ(S)=E[Gt|St=s]=Eπ[Rt+1+γVπ(S+1)|St=s]Vπ(S)=E[Gt|St=s]=Eπ[Rt+1+γVπ(S+1)|St=s]
위의 수식을 표현하자면 이전에는 Goal을 계산하기 위해 모든 Reward를 더하려 했지만 그럴 필요 없이 Goal을 계산하기 위해서 다음 state에서의 Value만 알면 현재 state를 계산할 수 있다는 것이다. 그리고 그렇게 구하려면 Equation형태로 구해야 하는데, 이를 바로 Bellman Equation이라고 한다.
사실 그냥 이렇게 봐서는 도저히 이해가 안간다. 예를 들어 한번 생각해보자.
Example

Example1
위의 예제를 생각해 보자. 위에서 화살표 방향의 action들은 모두 0.5의 확률을 같는다. π(a|s)=0.5π(a|s)=0.5라는 표현이 바로 그말이다. 모든 action들은 0.5의 확률을 같는다. 그리고 편의상 discount factor는 1로 하겠다. 그리고 쉬운 설명을 위해 문제를 조금 단순화 했는데 각 action이나 각 state마다 Reward가 존재한다. 위의 예제는 terminal state를 제외하고는 Reward가 0인 경우이다. 이제 위의 문제를 풀어서 각 state에서의 Value를 구할 것이다.
가장 먼저 PC방에서의 Value를 구하겠다. PC방에서의 Value를 V(PC방)이라고 하면 다음과 같은 Equation을 만들 수 있다.

V(PC방)=0.5×[0+V(PC방)]+0.5×(−10)V(PC방)=0.5×[0+V(PC방)]+0.5×(−10)
0.5의 확률로 PC방을 가면 다음 state의 Value는 V(PC방)이다. 그리고 0.5의 확률로는 terminal state로 가서 Reward를 -10을 받는다. 그것을 위의 수식으로 표현한 것이다. 굳이 0을 더해준 이유는 Reward가 0임을 나타낸 것이다. 위의 Equation으르 풀면 V(PC방)은 -10이 된다는 것을 쉽게 알 수 있다.
위와 똑같은 방식으로 모든 식을 세우면 아래와 같이 나온다. 그리고 그 Equation들을 모두 풀면 아래 그림과 같은 Value들을 얻을 수 있다.

V(start)=0.5×[0+V(PC방)]+0.5×[0+V(수업)]V(start)=0.5×[0+V(PC방)]+0.5×[0+V(수업)]
V(수업)=0.5×[0+V(PC방)]+0.5×[0+V(독서실)]V(수업)=0.5×[0+V(PC방)]+0.5×[0+V(독서실)]
V(독서실)=0.5×[0+V(PC방)]+0.5×10V(독서실)=0.5×[0+V(PC방)]+0.5×10
Example2

결론

이렇게 Bellan Equation에 대해 알아보았다. 우리가 위에서 구한 것은 어떤 Policy에서의 Value Function을 Bellman Equation을 이용해서 구한 것이다. 그런데 우리가 실제로 구해야 하는 것은 Optimal Policy에서의 Optimal Value Function을 구해야 한다. 이 문제를 푸는 것을 Bellman Optimality Equation이라고 부르는데, Value Iteration, Policy Iteration, Q-Learning, Sarsa같은 방법들을 이용해서 구하게 될 것이다.
