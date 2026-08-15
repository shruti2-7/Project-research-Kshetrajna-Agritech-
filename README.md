2. Rule-Based Expert System (Inference Engine)
Rather than writing tangled, deeply nested if-else statements, this approach decouples the Rules (data) from the Inference Engine (execution logic).

How it works:
You store your operational criteria in a lookup table or array of structs. The code iterates through the rule set to evaluate true/false conditions:

struct Rule {
    float minMoisture;
    float maxTemp;
    bool pumpState;
    int runDurationSec;
};

// Rule Table
Rule irrigationRules[] = {
    { 0.0,  20.0, true,  600 }, // Dry & Cool -> Moderate water
    { 0.0,  40.0, true,  900 }, // Dry & Hot  -> High water
    { 40.0, 50.0, false, 0   }  // Moisture OK -> Do nothing
};

Why it’s useful: If your team wants to add or tune irrigation cases, you only update the array parameters without modifying or refactoring the core codebase.
