---
title: BP_LOCATION | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c98fde516a3e836302cd7eb2c73abd730d5cc8c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737930"
---
# <a name="bp_location"></a>BP_LOCATION
Określa typ struktury używanej do opisywania lokalizacji punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>Elementy członkowskie
`bpLocationType`\
Wartość z [wyliczenia BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) używane do interpretacji `bpLocation` unii `unionmemberX` lub członków.

`bpLocation`.`bplocCodeFileLine`\
[Tylko C++] Zawiera [strukturę BP_LOCATION_CODE_FILE_LINE,](../../../extensibility/debugger/reference/bp-location-code-file-line.md) `bpLocationType`  =  `BPLT_CODE_FILE_LINE`jeśli .

`bpLocation.bplocCodeFuncOffset`\
[Tylko C++] Zawiera [strukturę BP_LOCATION_CODE_FUNC_OFFSET,](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`jeśli .

`bpLocation.bplocCodeContext`\
[Tylko C++] Zawiera [strukturę BP_LOCATION_CODE_CONTEXT,](../../../extensibility/debugger/reference/bp-location-code-context.md) `bpLocationType`  =  `BPLT_CODE_CONTEXT`jeśli .

`bpLocation.bplocCodeString`\
[Tylko C++] Zawiera [strukturę BP_LOCATION_CODE_STRING,](../../../extensibility/debugger/reference/bp-location-code-string.md) `bpLocationType`  =  `BPLT_CODE_STRING`jeśli .

`bpLocation.bplocCodeAddress`\
[Tylko C++] Zawiera [strukturę BP_LOCATION_CODE_ADDRESS,](../../../extensibility/debugger/reference/bp-location-code-address.md) `bpLocationType`  =  `BPLT_CODE_ADDRESS`jeśli .

`bpLocation.bplocDataString`\
[Tylko C++] Zawiera [strukturę BP_LOCATION_DATA_STRING,](../../../extensibility/debugger/reference/bp-location-data-string.md) `bpLocationType`  =  `BPLT_DATA_STRING`jeśli .

`bpLocation.bplocResolution`\
[Tylko C++] Zawiera [strukturę BP_LOCATION_RESOLUTION,](../../../extensibility/debugger/reference/bp-location-resolution.md) jeśli `bpLocationType`  =  `BPLT_RESOLUTION`.

`unionmember1`\
[Tylko C#] Zobacz Uwagi dotyczące interpretacji.

`unionmember2`\
[Tylko C#] Zobacz Uwagi dotyczące interpretacji.

`unionmember3`\
[Tylko C#] Zobacz Uwagi dotyczące interpretacji.

`unionmember4`\
[Tylko C#] Zobacz Uwagi dotyczące interpretacji.

## <a name="remarks"></a>Uwagi
Struktura ta jest członkiem [struktur BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

 [Tylko C#] Elementy `unionmemberX` członkowskie są interpretowane zgodnie z poniższą tabelą. Spójrz w dół lewej `bpLocationType` kolumny dla wartości, a następnie `unionmemberX` spojrzeć na `unionmemberX` inne kolumny, aby określić, co każdy element członkowski reprezentuje i marshal odpowiednio. Zobacz przykład, aby dokonywać interpretacji części tej struktury w języku C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string`(kontekst)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string`(kontekst)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string`(kontekst)|`string`(wyrażenie warunkowe)|-|-|
|`BPLT_CODE_ADDRESS`|`string`(kontekst)|`string`(adres URL modułu)|`string`(nazwa funkcji)|`string`(adres)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(kontekst)|`string`(wyrażenie danych)|`uint`(liczba elementów)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Przykład
W tym przykładzie `BP_LOCATION` pokazano, jak interpretować strukturę w języku C# dla `BPLT_DATA_STRING` typu. Ten konkretny typ pokazuje, `unionmemberX` jak interpretować wszystkie cztery elementy członkowskie we wszystkich możliwych formatach (obiekt, ciąg i liczba).

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
            }
        }
    }
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
