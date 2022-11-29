# MISRA Compliance

For now, FreeRTOS-Kernel only conforms [MISRA C:2012](https://www.misra.org.uk/MISRAHome/MISRAC2012/tabid/196/Default.aspx) guidelines in SMP part (configNUM_CORES > 1), 
with the deviations listed below. Compliance is checked with Coverity static analysis.

### Suppressed with Coverity Comments
To find the violation references in the source files run grep on the source code
with ( Assuming rule 11.4 violation; with justification in point 2 ):
```
grep 'MISRA Ref 4.6.1' . -rI
```
#### Directive 4.6

_Ref 4.6.1_

- MISRA C:2012 Directive 4.6: typedef that indicate size and signedness should be used in place of the basic numerical types.
        MISRA warns against the use of basic numerical types. FreeRTOS-Kerenl 
        uses BaseType_t/UBaseType_t to represent signed/unsigned variables no matter it's 16 or 32 bits.
        
#### Rule 17.3

_Ref 17.3.1_

- MISRA C:2012 Rule 17.3: A function shall not be declared implicitly.
        MISRA warns against the function declared implicitly. It's a false alarm that
        portCHECK_IF_IN_ISR() is declared in portmacro.h correctly.

_Ref 17.3.2_

- MISRA C:2012 Rule 17.3: A function shall not be declared implicitly.
        MISRA warns against the function declared implicitly. It's a false alarm that
        portGET_RUN_TIME_COUNTER_VALUE() is declared in portmacro.h correctly.
