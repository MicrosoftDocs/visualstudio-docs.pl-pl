---
title: BPRESI_FIELDS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 837bb7d25ab8dea2b146a98cc65d320b58162685
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737719"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Określa informacje, które mają być pobierane o pomyślnym rozwiązaniu punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Pola
`BPRESI_BPRESLOCATION`\
Inicjowanie/używanie pola `bpResLocation` (lokalizacja rozpoznawania punktów przerwania) BP_RESOLUTION_INFO struktury. [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)

`BPRESI_PROGRAM`\
Inicjuj/użyj `pProgram` `BP_RESOLUTION_INFO` pola konstrukcji.

`BPRESI_THREAD`\
Inicjuj/użyj `pThread` `BP_RESOLUTION_INFO` pola konstrukcji.

`BPRESI_ALLFIELDS`\
Określa wszystkie pola.

## <a name="remarks"></a>Uwagi
Przekazany do [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) metody, aby wskazać, które pola [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struktury mają być inicjowane.

Flagi te są również używane do `BP_RESOLUTION_INFO` wskazania, które pola struktury są używane i prawidłowe, gdy ta struktura jest zwracana.

Wartości te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
