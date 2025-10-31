# 📘 5주차 1차시 강의 요약

---

## 1️⃣ State Variable 시스템

State Variable 시스템은 **스프링, 질량, 감쇠기로 구성된 Spring–Mass–Damper 시스템**으로  
외력 `r(t)`이 작용할 때 질량의 변위 `y(t)`를 출력으로 보는 모델이다.  
운동방정식은 **뉴턴의 법칙**에 따라 다음과 같다.

$$
M\frac{d^2y(t)}{dt^2} + b\frac{dy(t)}{dt} + ky(t) = r(t)
$$

이 식은 **2차 미분방정식**이므로, 상태변수로 표현하기 위해  
$$x_1(t) = y(t), \quad x_2(t) = \dot{y}(t)$$  
로 정의하면 두 개의 1차 미분방정식으로 바꿀 수 있다.

$$
\begin{cases}
\dot{x}_1(t) = x_2(t) \\
\dot{x}_2(t) = -\frac{b}{M}x_2(t) - \frac{k}{M}x_1(t) + \frac{1}{M}r(t)
\end{cases}
$$

출력은 다음과 같다.

$$
y(t) = x_1(t)
$$

따라서 이 시스템은 **질량 M**, **감쇠계수 b**, **스프링상수 k**에 의해 동특성이 결정되며,  
외력 `r(t)`에 대한 변위응답 `y(t)`를 예측할 수 있는 **상태공간모델(state-space model)** 형태로 표현된다.

![spring-mass-damper](<img width="247" height="309" alt="image" src="https://github.com/user-attachments/assets/3a3b892f-2e12-49fa-a722-122ba2896abc" />
)

---

## 2️⃣ RLC 직렬회로의 상태변수 표현

입력 전압 `u(t)`이 인가된 RLC 직렬회로를 상태변수로 표현한다.  
커패시터 전압과 인덕터 전류를 각각 상태변수 `x₁`, `x₂`로 정의하면  
키르히호프의 법칙(KVL, KCL)을 이용해 시스템을 기술할 수 있다.

- **KCL:** 입력 전류는 커패시터 전류와 인덕터 전류의 합  
- **KVL:** 회로 내 전압 관계 이용

이를 통해 다음과 같은 상태방정식을 얻을 수 있다.

$$
\begin{cases}
\dot{x}_1(t) = \frac{1}{C}x_2(t) \\
\dot{x}_2(t) = -\frac{R}{L}x_2(t) - \frac{1}{L}x_1(t) + \frac{1}{L}u(t)
\end{cases}
$$

출력은 회로 양단의 전압으로 표현된다.

$$
y(t) = R x_2(t)
$$

결과적으로 이 RLC 회로는 입력 전류 `u(t)`에 대한 동작을  
두 개의 1차 미분방정식으로 나타내는 **상태공간 모델** 형태로 정리된다.

![rlc-circuit](<img width="247" height="309" alt="image" src="https://github.com/user-attachments/assets/2275ae21-8de8-4e93-8a93-fd9ca0197d7c" />
)

---

## 3️⃣ 1차 상태방정식의 해

$$
x(t) = e^{At}x(0) + \int_0^t e^{A(t - \tau)}B u(\tau)d\tau
$$

- 첫 번째 항: 초기 상태로부터의 변화 (**Transition from initial state**)  
- 두 번째 항: 입력신호가 상태에 미치는 영향 (**Effect of input**)

즉, 상태공간 표현을 사용하면 시스템의 응답을  
**초기 상태의 영향**과 **입력에 의한 반응**으로 명확히 구분하여 이해할 수 있다.

![state-solution](이미지경로3.png)

---

## 4️⃣ 상태공간 표현 (State Space Representation)

상태벡터 `x(t)`는 여러 상태변수들을 모은 벡터이며,  
시스템은 다음과 같이 표현된다.

$$
\begin{cases}
\dot{x}(t) = A x(t) + B u(t) \\
y(t) = C x(t) + D u(t)
\end{cases}
$$

즉, `A`, `B`, `C`, `D` 행렬을 이용하여 입력 `u(t)`, 상태 `x(t)`, 출력 `y(t)` 간의 관계를  
**행렬 형태**로 나타낸 것이다.

![state-space](이미지경로4.png)

---

## 5️⃣ 상태전이행렬 (State Transition Matrix)

상태방정식:

$$
\dot{x}(t) = A x(t) + B u(t)
$$

그 해는 다음과 같다.

$$
x(t) = \Phi(t)x(0) + \int_0^t \Phi(t - \tau) B u(\tau)d\tau
$$

여기서 `Φ(t)`는 **상태전이행렬(State Transition Matrix)**로,  
시간이 지남에 따라 초기 상태가 어떻게 변화하는지를 나타낸다.

→ 전체 해는 **초기 상태의 영향**과 **입력 신호의 영향**이 결합된 형태로 구성된다.

![state-transition](이미지경로5.png)

---

## 6️⃣ 2자유도 질량–스프링–감쇠기 시스템 예시

두 개의 질량이 스프링과 감쇠기로 연결된 **2자유도 시스템**의 상태공간 표현이다.

입력 `u(t)`가 첫 번째 질량 `M₁`에 작용할 때,  
두 질량의 위치와 속도를 상태변수로 정의한다.

$$
x(t) = [p, q, \dot{p}, \dot{q}]^T
$$

이를 통해 시스템은 다음과 같이 표현된다.

$$
\dot{x}(t) = A x(t) + B u(t)
$$

행렬 `A`는 각 질량, 스프링, 감쇠기의 상호작용을 포함한다.  
→ 복잡한 2자유도 운동방정식을 행렬 형태의 상태방정식으로 단순화한 예시이다.

![two-mass-system](이미지경로6.png)

---

## 7️⃣ MATLAB 시뮬레이션 (Example 3.1)

앞서의 2자유도 질량–스프링–감쇠기 시스템을 MATLAB으로 시뮬레이션하였다.

$$
\dot{x}(t) = A x(t) + B u(t)
$$

출력:

$$
y(t) = p(t)
$$

입력:

$$
u(t) = 0
$$

- MATLAB 코드에서는 질량, 스프링, 감쇠계수를 설정하고  
  행렬 `A, B, C, D`를 정의한 뒤, `initial()` 함수를 이용하여  
  **초기변위에 대한 자유진동(free vibration) 응답**을 계산하였다.  
- 결과 그래프는 **감쇠에 의해 점차 안정되는 진동 특성**을 보여준다.

![matlab-simulation](이미지경로7.png)

---

> ✍️ **작성자:** 김준호  
> 💡 **주제:** 상태공간모델 (State-Space Model)  
> 📅 **5주차 1차시 강의**
