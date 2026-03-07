# flowchart LR
  A[시나리오/명령 생성\n(급정지, 강풍 외란)] --> B[상태 추정/구독\n(자세, 각속도, 속도 등)\nROS2]
  B --> C[Outer loop\n정지제어 로직 + PID\n(자세/정지 목표)]
  C --> D[Body-rate setpoint 생성\np*, q*, r*\n(클리핑/레이트리밋)]
  D --> E[PX4 Rate Controller\n(내부 각속도 추종)]
  E --> F[모터/믹싱]
  F --> G[쿼드로터 동역학\nGazebo Harmonic]
  G --> B

  subgraph H[본 과제의 핵심(주제 영역)]
    I[PPO / SAC\n정책(학습)]
    J[PID 적분(I) 게인\n온라인 튜닝(Ki 또는 ΔKi)]
    I --> J --> C
  end
