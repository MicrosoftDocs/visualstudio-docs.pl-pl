---
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82a286bea92c778ab150cacdc80d79f8ac283469
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350485"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
Określa informacje, które mają zostać pobrane informacje pomyślnego rozwiązania punktu przerwania.

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
Inicjowanie bądź użyj `bpResLocation` pola (lokalizacji punktu przerwania rozdzielczość) [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struktury.

`BPRESI_PROGRAM`\
Inicjowanie bądź użyj `pProgram` pole `BP_RESOLUTION_INFO` struktury.

`BPRESI_THREAD`\
Inicjowanie bądź użyj `pThread` pole `BP_RESOLUTION_INFO` struktury.

`BPRESI_ALLFIELDS`\
Określa wszystkie pola.

## <a name="remarks"></a>Uwagi
Przekazany do [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) metodę, aby wskazać, które pola [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struktury, które mają zostać zainicjowane.

Te flagi są również używane w celu wskazania, które pola `BP_RESOLUTION_INFO` struktury są używane i ważne, gdy tej struktury jest zwracany.

Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
