# Macroeconomics IS-LM Model

A Python implementation of the classical **IS–LM** model in a Jupyter notebook. Define your fiscal and monetary parameters, compute the equilibrium ($Y^*$, $i^*$), simulate policy shocks, and visualize results for:
- **Money market** (real money demand vs. supply)  
- **IS–LM diagram** with equilibrium point  
- **Aggregate supply–demand** (AS–AD)

All you need are `numpy` and `matplotlib`; simply run the notebook cells to get started.

## Usage

```python
import numpy as np
import matplotlib.pyplot as plt

# 1. Create model instance with your parameters
m = ISLMModel(
    ConsumoAutonomo=50,
    EfectosEficiencia=20,
    GastoPublico=30,
    parametro=10,
    PropoencionConsumir=0.8,
    TasaImpuestos=0.2,
    SensibilidadDineroIng=0.5,
    SensibilidadDineroi=0.3,
    OfertaDinero=100,
    precios=1.0
)

# 2. Solve equilibrium
Y_star, i_star = m.Equilibrio()
print(f"Equilibrium: Y*={Y_star}, i*={i_star}")

# 3. Plot baseline IS–LM
m.graficar()


### The shocks are interactive and simply by calling the class method you can simulate the shocks, no extra parameters are required.
# 4. Simulate a +15% fiscal shock
m.Shock() # Option 1 and enter 15 to simulate that shock

# 5. Simulate combined +20% monetary & +15% fiscal shock
m.Shock() # Option 3 and enteder 20 and 15 to simulate that shock
```

## API

| Method             | Description                                                                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CurvaIS(Y)`       | Computes the IS–curve interest rate for a given output level `Y`.                                                                                                                   |
| `CurvaLM(Y)`       | Computes the LM–curve interest rate for a given output level `Y`.                                                                                                                   |
| `MercadoDinero(m)` | Calculates real money demand given a nominal money supply parameter `m`.                                                                                                            |
| `CurvaDemanda(Y)`  | Computes aggregate demand at the output level `Y`.                                                                                                                                  |
| `Equilibrio()`     | Returns the equilibrium pair ($Y^*$, $i^*$) in the goods and money markets.                                                                                                        |
| `graficar()`       | Draws a 2×2 grid of plots: money market, IS–LM diagram, and AS–AD diagrams.                                                                                                          |
| `Shock()`          | Interactive policy-shock simulator:<br>• **Option 1**: fiscal shock (enter % increase or decrease in `GastoPublico`)<br>• **Option 2**: monetary shock (enter % increase or decrease in `OfertaDinero`)<br>• **Option 3**: combined shock (enter monetary %, then fiscal %) |




