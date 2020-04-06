---
title: BP_RESOLUTION_LOCATION | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b11d80e90daec19a14ca509e5a4b9bdb2d1ced4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737811"
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
Wartość z [wyliczenia BP_TYPE,](../../../extensibility/debugger/reference/bp-type.md) która określa sposób interpretowania `bpResLocation` `unionmemberX` unii lub członków.

`bpResLocation.bpresCode`\
[Tylko C++] Zawiera [strukturę BP_RESOLUTION_CODE,](../../../extensibility/debugger/reference/bp-resolution-code.md) jeśli `bpType`  =  `BPT_CODE`.

`bpResLocation.bpresData`\
[Tylko C++] Zawiera [strukturę BP_RESOLUTION_DATA,](../../../extensibility/debugger/reference/bp-resolution-data.md) `bpType`  =  `BPT_DATA`jeśli .

`bpResLocation.unused`\
[Tylko C++] Symbol zastępczy.

`unionmember1`\
[Tylko C#] Zobacz Uwagi dotyczące interpretacji.

`unionmember2`\
[Tylko C#] Zobacz Uwagi dotyczące interpretacji.

`unionmember3`\
[Tylko C#] Zobacz Uwagi dotyczące interpretacji.

`unionmember4`\
[Tylko C#] Zobacz Uwagi dotyczące interpretacji.

## <a name="remarks"></a>Uwagi
Struktura ta jest członkiem [struktur BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) i [BP_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-resolution-info.md)

 [Tylko C#] Elementy `unionmemberX` członkowskie są interpretowane zgodnie z poniższą tabelą. Spójrz w dół lewej `bpType` kolumny dla wartości `unionmemberX` następnie w poprzek, aby określić, co każdy element członkowski reprezentuje i marshal `unionmemberX` odpowiednio. Zobacz przykład, aby uzyskać sposób interpretowania tej struktury w języku C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string`(wyrażenie danych)|`string`(nazwa funkcji)|`string`(nazwa obrazu)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Przykład
W tym przykładzie `BP_RESOLUTION_LOCATION` pokazano, jak interpretować strukturę w języku C#.

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
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
