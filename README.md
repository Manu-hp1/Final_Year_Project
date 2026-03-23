# Final-Year-Project
Autonomous River Depth Plotting and Cleaning Robot

isr()
{
    GIE = 0;        // disables further interrupts
    int_flag = 0;   // prevents recursive function calls
}


---

## Interrupt Latency
> Time taken by the microcontroller to **execute the first instruction of ISR** from the time interrupt has been requested

- If interrupt is at i-th instruction → time taken to complete i-th instruction + enter ISR = **Interrupt Latency**

---

## Priority Scheme
- Controller decides which interrupt gets executed **first based on priority**
- ISR are of **2 types**: Low priority & High priority
  - S2 → Low priority
  - S1 → High priority
- When higher priority interrupt comes first → ISR of high priority executes & completes → then low priority gets executed

---

## Trigger Interrupts
**3 bits** which control interrupts:
- **Flag bit**
- **Enable bit**
- **Priority bit**

---

## External Interrupts
- Only **3 pins** (RB0, RB1, RB2) are meant for external interrupts
- Only **edge triggering**

### For RB0 pin:
- To decide whether **rising edge / falling edge** → **INTEDG0** bit is used
  - INTEDG0 **set** → Rising edge ↑
  - INTEDG0 **cleared** → Falling edge ↓

### Enable bit — INTOE:
- **INTOE = 1** → Enable interrupt
- **INTOE = 0** → Disable interrupt

### Flag bit — INTOF:
- If both bits set → flag bit **INTOF = 1**
- This is **set by hardware itself**
- We have to **clear it** to use that
- GIE will also be cleared by hardware

---

## Super Loop & Interrupt Flow
```
main()
{
    while(1)
    {
        ←——— interrupt occurs here
        ↓
        [ISR executes]
        ↓
        returns back
    }
}
