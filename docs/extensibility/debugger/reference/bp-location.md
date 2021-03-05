---
description: Określa typ struktury używany do opisywania lokalizacji punktu przerwania.
title: BP_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 472dc7b2e642608691ea2adb2ad1a7dce170729f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144185"
---
# <a name="bp_location"></a>BP_LOCATION
Określa typ struktury używany do opisywania lokalizacji punktu przerwania.

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
Wartość z wyliczenia [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) używanego do interpretacji `bpLocation` Unii lub `unionmemberX` członków.

`bpLocation`.`bplocCodeFileLine`\
[Tylko C++] Zawiera strukturę [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) , jeśli `bpLocationType`  =  `BPLT_CODE_FILE_LINE` .

`bpLocation.bplocCodeFuncOffset`\
[Tylko C++] Zawiera strukturę [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) , jeśli `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET` .

`bpLocation.bplocCodeContext`\
[Tylko C++] Zawiera strukturę [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) , jeśli `bpLocationType`  =  `BPLT_CODE_CONTEXT` .

`bpLocation.bplocCodeString`\
[Tylko C++] Zawiera strukturę [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) , jeśli `bpLocationType`  =  `BPLT_CODE_STRING` .

`bpLocation.bplocCodeAddress`\
[Tylko C++] Zawiera strukturę [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) , jeśli `bpLocationType`  =  `BPLT_CODE_ADDRESS` .

`bpLocation.bplocDataString`\
[Tylko C++] Zawiera strukturę [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) , jeśli `bpLocationType`  =  `BPLT_DATA_STRING` .

`bpLocation.bplocResolution`\
[Tylko C++] Zawiera strukturę [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) , jeśli `bpLocationType`  =  `BPLT_RESOLUTION` .

`unionmember1`\
[Tylko w C#] Zobacz uwagi dotyczące sposobu interpretacji.

`unionmember2`\
[Tylko w C#] Zobacz uwagi dotyczące sposobu interpretacji.

`unionmember3`\
[Tylko w C#] Zobacz uwagi dotyczące sposobu interpretacji.

`unionmember4`\
[Tylko w C#] Zobacz uwagi dotyczące sposobu interpretacji.

## <a name="remarks"></a>Uwagi
Ta struktura jest elementem członkowskim struktur [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

 [Tylko w C#] `unionmemberX` Elementy członkowskie są interpretowane zgodnie z poniższą tabelą. Wyszukaj w lewej kolumnie `bpLocationType` wartość, a następnie poszukaj innych kolumn, aby określić, co każdy `unionmemberX` element członkowski reprezentuje i `unionmemberX` odpowiednio zorganizować. Zobacz przykład, aby poznać sposób interpretacji części tej struktury w języku C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string` (kontekst)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string` (kontekst)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string` (kontekst)|`string` (wyrażenie warunkowe)|-|-|
|`BPLT_CODE_ADDRESS`|`string` (kontekst)|`string` (adres URL modułu)|`string` (nazwa funkcji)|`string` Ulica|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (kontekst)|`string` (wyrażenie danych)|`uint` (liczba elementów)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak interpretować `BP_LOCATION` strukturę w języku C# dla `BPLT_DATA_STRING` typu. Ten konkretny typ pokazuje, jak interpretować wszystkie cztery `unionmemberX` elementy członkowskie we wszystkich możliwych formatach (Object, String i Number).

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
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

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
