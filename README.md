```mermaid
flowchart LR

subgraph RAW
    R1[orders_raw]
    R2[stream_raw_orders]
end

subgraph STAGED
    S1[stg_orders]
    S2[stg_order_items]
end

subgraph CURATED
    D1[dim_customer]
    D2[dim_product]
    F1[fact_orders]
    F2[fact_order_items]
end

subgraph ORCHESTRATION
    T1[Task RAW_to_STAGED]
    T2[Task STAGED_to_CURATED]
    A[pipeline_audit]
end

R1 --> R2
R2 --> T1
T1 --> S1
T1 --> S2
T1 --> A

S1 --> T2
S2 --> T2
T2 --> D1
T2 --> D2
T2 --> F1
T2 --> F2
T2 --> A
```
