# Hard Reference와 Soft Reference란
- Hard Reference: 직접 참조 - 에셋 또는 UObject를 가리키는 포인터
- Soft Reference: 간접 참조 - 에셋 또는 UObject 폴더주소라고 볼 수 있음(? 팩트체크 필요)

## C++: 
Soft Reference = TSoftClassPtr

Hard Reference = 기본 클래스 포인터 (TSubclass, etc.)

## 블루프린트: 
<img width="170" alt="Screenshot 2024-03-24 at 2 14 05 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/aca02055-173a-413a-8722-1068cfa1983b">

# 시나리오: BP_Cliff을 스폰하고 싶음

- 언리얼에서 자동으로 메모리 관리하는 기능(Garbage Collection, 등)이 있지만 레벨에 있는 모든 에셋들을 잘 관리해야 히칭 현상 또는 랙을 피할 수 있다.
- 우선 꼭 알아야하는 포인트는 _**에셋을 참조하는 모든 UObject는 자동으로 메모리에 실린다**_.
- 따라서 **변화없이 레벨에 존재하는 에셋들은 Hard Reference로 참조**하고 **동적으로 레벨에 Spawn/Destroy하는 에셋들은 Soft Reference로 참조**해주자.   

### Reference Viewer - BP_Cliff과 종속성이 있는 에셋들을 볼 수 있음
<img width="471" alt="Screenshot 2024-03-24 at 2 03 02 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/53af834c-6417-4f61-897a-8b06b8f27b8b">

### 예) BP_Cliff 블루프린트를 참조하는 블루프린트가 2개 있음 : 하나는 Soft Reference and 하나는 Hard Reference
<img width="1728" alt="Screenshot 2024-03-24 at 2 04 09 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/03ecd8f7-badf-4165-8fdb-0dcbe8cb7d88">

### Size Map - 에셋이 스트리밍으로 불러올 때 메모리 크기

<img width="253" alt="Screenshot 2024-03-24 at 2 05 43 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/acfd934e-0d0b-4ec9-8e42-0ce82d07429c">

### 예) BP_Cliff 사이즈 맵: 총 742.8 MB

<img width="986" alt="Screenshot 2024-03-24 at 2 17 09 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/c869aa0a-d9b9-40ed-812d-00c735fa498f">

## Hard Reference하는 블루프린트

### BP_HardReferenceActor Reference Viewer
<img width="589" alt="Screenshot 2024-03-24 at 2 05 07 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/3ac50ea2-b832-4e1e-ae8a-fe488f826a30">

### BP_HardReferenceActor Size Map
<img width="986" alt="Screenshot 2024-03-24 at 2 06 04 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/6be3fee0-782e-4fa2-8a18-fb27e496dd15">

### BP_HardReferenceActor Spawn 코드
<img width="637" alt="Screenshot 2024-03-24 at 2 35 38 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/9bcd9bb7-18c3-4e0e-92d9-f588cde47ede">

### 로딩 시간: 0.0 ms 스폰 시간: 0.0(?) ms

https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/9bca650e-c324-4098-9bba-1b62586782c1

## Soft Reference하는 블루프린트

### BP_SoftReferenceActor Reference Viewer
<img width="875" alt="Screenshot 2024-03-24 at 2 07 44 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/2c2253e7-1a39-4686-890d-7e1da166dc41">

### BP_SoftReferenceActor Size Map
<img width="986" alt="Screenshot 2024-03-24 at 2 06 16 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/9f49b675-52f3-4d5b-a701-874c743a2a29">

### BP_SoftReferenceActor Spawn 코드

<img width="895" alt="Screenshot 2024-03-24 at 2 36 58 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/2d87f061-3606-4da1-bc17-572c040f0f51">

### 로딩 시간: 0.0 ms 스폰 시간: 0.01 ms

https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/5f85747d-de7b-41a8-8cab-81c5281418fb

### 쿠키: C++ 코드 
https://gist.github.com/yoponchik/7523836a0f2ab649f3814e5c27a28bb1







