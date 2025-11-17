graph TD
    subgraph 信任域 (Trust Domain)
        A[Certifier 服务: simpleserver]
        B(机密运行时: runtime.exe)
    end
    
    C[模型提供者: model_provider.exe]
    D[设备/客户端: device.exe]
    
    % 信任建立 - 红色虚线
    B -- 1. Attestation Request (Measurement) --> A
    A -- 2. Attestation Response (Keys/Approval) --> B
    
    % 模型部署 - 蓝色实线
    C -- 3. Secure Model Transfer (MODEL) --> B
    
    % 数据交互 - 绿色虚线
    D -- 4. Data/Local Updates --> B
    B -- 5. Result/Global Model --> D
    
    style A fill:#f9f,stroke:#333
    style B fill:#ccf,stroke:#333
    style C fill:#aaf,stroke:#333
    style D fill:#faa,stroke:#333
