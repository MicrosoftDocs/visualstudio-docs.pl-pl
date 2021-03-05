---
description: Określa strukturę lokalizacji rozpoznawania punktów przerwania.
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87fef44d02911e84952f6eb8ab09dd9a1360dea6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162566"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Określa strukturę lokalizacji rozpoznawania punktów przerwania.

## <a name="syntax"></a>Składnia

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Elementy członkowskie
`bpType`\
Wartość z wyliczenia [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) , która określa sposób interpretacji `bpResLocation` Unii lub `unionmemberX` członków.

`bpResLocation.bpresCode`\
[Tylko C++] Zawiera strukturę [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) , jeśli `bpType`  =  `BPT_CODE` .

`bpResLocation.bpresData`\
[Tylko C++] Zawiera strukturę [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) , jeśli `bpType`  =  `BPT_DATA` .

`bpResLocation.unused`\
[Tylko C++] Symbol zastępczy.

`unionmember1`\
[Tylko w C#] Zobacz uwagi dotyczące sposobu interpretacji.

`unionmember2`\
[Tylko w C#] Zobacz uwagi dotyczące sposobu interpretacji.

`unionmember3`\
[Tylko w C#] Zobacz uwagi dotyczące sposobu interpretacji.

`unionmember4`\
[Tylko w C#] Zobacz uwagi dotyczące sposobu interpretacji.

## <a name="remarks"></a>Uwagi
Ta struktura jest elementem członkowskim struktur [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) i [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .

 [Tylko w C#] `unionmemberX` Elementy członkowskie są interpretowane zgodnie z poniższą tabelą. Poszukaj w lewej kolumnie wartości, `bpType` a następnie określ, co każdy `unionmemberX` element członkowski reprezentuje i odpowiednio zorganizować `unionmemberX` . Zobacz przykład sposobu interpretacji struktury w języku C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` (wyrażenie danych)|`string` (nazwa funkcji)|`string` (nazwa obrazu)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak interpretować `BP_RESOLUTION_LOCATION` strukturę w języku C#.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
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
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
