# Incentive-Inference
Causal Inference Model: Sales-Incentive Analysis using DoubleML

```{mermaid}
flowchart TD
    %% Main Data Sections
    RawData([Raw Input Data]):::inputNode
    
    %% Data Breakdown
    RawData --> SalesData["Sales Data:<br/>- Revenue<br/>- Units Sold<br/>- Product Categories<br/>- Sales Channels"]:::dataNode
    RawData --> IncentiveData["Incentive Data:<br/>- Promotional Discounts<br/>- Rebates<br/>- Loyalty Programs<br/>- Special Offers"]:::dataNode
    RawData --> ConfoundersData["Confounding Variables:<br/>- Seasonality<br/>- Market Competition<br/>- Economic Indicators<br/>- Marketing Spend<br/>- Product Lifecycle"]:::dataNode
    RawData --> ContextualData["Contextual Data:<br/>- Geographic Information<br/>- Customer Demographics<br/>- Historical Trends<br/>- Industry Benchmarks"]:::dataNode
    
    %% Preprocessing Section
    Preprocessing["Data Preprocessing"]:::processNode
    
    SalesData --> Preprocessing
    IncentiveData --> Preprocessing
    ConfoundersData --> Preprocessing
    ContextualData --> Preprocessing
    
    Preprocessing --> FeatureEngineering["Feature Engineering:<br/>- Derived Metrics<br/>- Temporal Features<br/>- Interaction Terms"]:::prepNode
    Preprocessing --> MissingHandling["Missing Data Handling:<br/>- Imputation<br/>- Filtering"]:::prepNode
    Preprocessing --> Normalization["Data Normalization:<br/>- Scaling<br/>- Transformation"]:::prepNode
    
    FeatureEngineering --> ProcessedData["Processed Dataset"]:::resultNode
    MissingHandling --> ProcessedData
    Normalization --> ProcessedData
    
    %% Problem Formulation
    ProblemForm["Problem Formulation"]:::processNode
    
    ProcessedData --> ProblemForm
    
    ProblemForm --> TreatmentDef["Treatment Definition:<br/>Incentive Variables"]:::defNode
    ProblemForm --> OutcomeDef["Outcome Definition:<br/>Sales Metrics"]:::defNode
    ProblemForm --> ConfDef["Confounder Definition:<br/>Control Variables"]:::defNode
    ProblemForm --> InstrumentDef["Instrumental Variables<br/>(if available)"]:::defNode
    
    %% DoubleML Framework
    DoubleMLFramework["DoubleML Framework"]:::modelNode
    
    TreatmentDef --> DoubleMLFramework
    OutcomeDef --> DoubleMLFramework
    ConfDef --> DoubleMLFramework
    InstrumentDef --> DoubleMLFramework
    
    DoubleMLFramework --> FirstStageModel["First Stage Model:<br/>Treatment Prediction<br/>(ML1)"]:::mlNode
    DoubleMLFramework --> SecondStageModel["Second Stage Model:<br/>Outcome Prediction<br/>(ML2)"]:::mlNode
    
    FirstStageModel --> ModelSelection1["Model Selection:<br/>- Random Forest<br/>- Gradient Boosting<br/>- Lasso/Ridge<br/>- Neural Networks"]:::methodNode
    SecondStageModel --> ModelSelection2["Model Selection:<br/>- Random Forest<br/>- Gradient Boosting<br/>- Lasso/Ridge<br/>- Neural Networks"]:::methodNode
    
    ModelSelection1 --> CrossFitting["Cross-Fitting<br/>Procedure"]:::methodNode
    ModelSelection2 --> CrossFitting
    
    CrossFitting --> OrthoScore["Orthogonalized<br/>Score Functions"]:::methodNode
    
    %% Estimation Process
    OrthoScore --> CausalEstimation["Causal Parameter<br/>Estimation"]:::estimationNode
    
    CausalEstimation --> ATEEstimation["Average Treatment Effect<br/>(ATE) Estimation"]:::resultNode
    CausalEstimation --> CATEEstimation["Conditional Average<br/>Treatment Effect<br/>(CATE) Estimation"]:::resultNode
    CausalEstimation --> DoseResponse["Dose-Response<br/>Curve Estimation"]:::resultNode
    
    %% Inference & Validation
    ValidationSection["Inference & Validation"]:::processNode
    
    ATEEstimation --> ValidationSection
    CATEEstimation --> ValidationSection
    DoseResponse --> ValidationSection
    
    ValidationSection --> ConfidenceIntervals["Confidence Intervals<br/>Construction"]:::validationNode
    ValidationSection --> Sensitivity["Sensitivity Analysis:<br/>- Robustness Checks<br/>- Model Variants"]:::validationNode
    ValidationSection --> Diagnostics["Model Diagnostics:<br/>- Residual Analysis<br/>- Specification Tests"]:::validationNode
    ValidationSection --> PlaceboTests["Placebo Tests"]:::validationNode
    
    %% Results & Insights
    Results["Results & Business Insights"]:::outputNode
    
    ConfidenceIntervals --> Results
    Sensitivity --> Results
    Diagnostics --> Results
    PlaceboTests --> Results
    
    Results --> IncentiveEffect["Incentive Effectiveness:<br/>- Effect Size<br/>- Statistical Significance"]:::insightNode
    Results --> HeterogeneousEffects["Heterogeneous Effects:<br/>- By Segment<br/>- By Channel<br/>- By Product"]:::insightNode
    Results --> OptimalAllocation["Optimal Incentive<br/>Allocation Strategy"]:::insightNode
    Results --> ROICalc["ROI Calculation<br/>Framework"]:::insightNode
    
    %% Implementation
    Implementation["Implementation<br/>& Deployment"]:::deployNode
    
    IncentiveEffect --> Implementation
    HeterogeneousEffects --> Implementation
    OptimalAllocation --> Implementation
    ROICalc --> Implementation
    
    Implementation --> Dashboard["Interactive<br/>Dashboard"]:::appNode
    Implementation --> APIntegration["API Integration<br/>with Planning Systems"]:::appNode
    Implementation --> MonitoringSystem["Continuous Monitoring<br/>System"]:::appNode
    
    %% Feedback Loop
    MonitoringSystem --> RawData
    
    %% Styling
    classDef inputNode fill:#d4f1f9,stroke:#05a8e6,stroke-width:2px,color:black,font-weight:bold
    classDef dataNode fill:#e1f5fe,stroke:#0288d1,stroke-width:1px
    classDef processNode fill:#fffde7,stroke:#fbc02d,stroke-width:3px,color:black,font-weight:bold
    classDef prepNode fill:#e8f5e9,stroke:#43a047,stroke-width:1px
    classDef resultNode fill:#e8f5e9,stroke:#43a047,stroke-width:2px,font-weight:bold
    classDef defNode fill:#f3e5f5,stroke:#8e24aa,stroke-width:1px
    classDef modelNode fill:#e1d5e7,stroke:#9673a6,stroke-width:3px,color:black,font-weight:bold
    classDef mlNode fill:#d1c4e9,stroke:#5e35b1,stroke-width:2px,font-weight:bold
    classDef methodNode fill:#ede7f6,stroke:#673ab7,stroke-width:1px
    classDef estimationNode fill:#bbdefb,stroke:#1976d2,stroke-width:2px
    classDef validationNode fill:#e3f2fd,stroke:#2196f3,stroke-width:1px
    classDef outputNode fill:#ffebee,stroke:#c62828,stroke-width:3px,color:black,font-weight:bold
    classDef insightNode fill:#ffcdd2,stroke:#e53935,stroke-width:1px
    classDef deployNode fill:#ffe0b2,stroke:#ef6c00,stroke-width:2px,font-weight:bold
    classDef appNode fill:#fff3e0,stroke:#ff9800,stroke-width:1px
```
