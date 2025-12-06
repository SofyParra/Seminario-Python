# Codigo en Thonny, lectura potenciometro


[![Open in VS Code](https://github.com/SofyParra/Seminario-Python/blob/main/grafica.py)

## Vista rápida

![Codigo en Thonny](https://github.com/SofyParra/Seminario-Python/blob/main/Codigo%20en%20Thonny.png)

```
from machine import ADC, Pin
import time

# ---------- ADC configuration  ----------
pot = ADC(Pin(34))               
pot.atten(ADC.ATTN_11DB)         # Approx. 0–3.3 V input range
pot.width(ADC.WIDTH_12BIT)       # 12-bit resolution: 0–4095

# ---------- UART configuration ----------
def read_pot():
    raw = pot.read()                 # 0–4095
    voltage = raw * 3.3 / 4095       
    return raw, voltage

while True:
    raw, v = read_pot()
    print("V={:0.3f} V".format(v))
    time.sleep(0.1)
```
