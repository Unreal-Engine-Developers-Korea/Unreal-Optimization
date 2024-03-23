#### C++: TSoftClassPtr and regular Class Pointer (TSubclass, etc.)

#### Blueprint: 
<img width="170" alt="Screenshot 2024-03-24 at 2 14 05 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/aca02055-173a-413a-8722-1068cfa1983b">

# Want to spawn an actor

### Reference Viewer
<img width="471" alt="Screenshot 2024-03-24 at 2 03 02 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/53af834c-6417-4f61-897a-8b06b8f27b8b">

### 2 Blueprints referencing this: One is Soft Reference and the other Hard Reference
<img width="1728" alt="Screenshot 2024-03-24 at 2 04 09 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/03ecd8f7-badf-4165-8fdb-0dcbe8cb7d88">

### BP_Cliff Size Map

<img width="253" alt="Screenshot 2024-03-24 at 2 05 43 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/acfd934e-0d0b-4ec9-8e42-0ce82d07429c">

<img width="986" alt="Screenshot 2024-03-24 at 2 17 09 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/c869aa0a-d9b9-40ed-812d-00c735fa498f">

## Hard Reference

### Reference Viewer
<img width="589" alt="Screenshot 2024-03-24 at 2 05 07 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/3ac50ea2-b832-4e1e-ae8a-fe488f826a30">

### BP_HardReferenceActor Size Map
<img width="986" alt="Screenshot 2024-03-24 at 2 06 04 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/6be3fee0-782e-4fa2-8a18-fb27e496dd15">

### Load Time: 0.0 ms Spawn Time: 0.0(?) ms

https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/9bca650e-c324-4098-9bba-1b62586782c1

## Soft Reference

### Reference Viewer
<img width="875" alt="Screenshot 2024-03-24 at 2 07 44 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/2c2253e7-1a39-4686-890d-7e1da166dc41">

### BP_SoftReferenceActor Size Map
<img width="986" alt="Screenshot 2024-03-24 at 2 06 16 AM" src="https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/9f49b675-52f3-4d5b-a701-874c743a2a29">

### Load Time: 0.0 ms Spawn Time: 0.01 ms

https://github.com/Unreal-Engine-Developers-Korea/Unreal-Optimization/assets/57009810/5f85747d-de7b-41a8-8cab-81c5281418fb








