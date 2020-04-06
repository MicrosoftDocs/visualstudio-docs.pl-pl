---
title: BPERESI_FIELDS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737765"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Określa informacje, które mają być pobierane o nieudanej rozdzielczości punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Pola
`PERESI_BPRESLOCATION`\
Inicjowanie/używanie pola `bpResLocation` (lokalizacja rozpoznawania punktów przerwania) BP_ERROR_RESOLUTION_INFO struktury. [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

`BPERESI_PROGRAM`\
Inicjuj/użyj `pProgram` `BP_ERROR_RESOLUTION_INFO` pola konstrukcji.

`BPERESI_THREAD`\
Inicjuj/użyj `pThread` `BP_ERROR_RESOLUTION_INFO` pola konstrukcji.

`BPERESI_MESSAGE`\
Inicjuj/użyj `bstrMessage` `BP_ERROR_RESOLUTION_INFO` pola konstrukcji.

`BPERESI_TYPE`\
Inicjowanie/używanie pola `dwType` `BP_ERROR_RESOLUTION_INFO` (typ punktu przerwania) struktury.

`BPERESI_ALLFIELDS`\
Inicjuj/użyj `BP_ERROR_RESOLUTION_INFO` wszystkich pól struktury.

## <a name="remarks"></a>Uwagi
Przekazany jako parametr do [Metody GetResolutionInfo,](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) aby wskazać, które pola [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury mają zostać zainicjowane.

Wartości te są również używane do `BP_ERROR_RESOLUTION_INFO` wskazania, które pola w strukturze są używane i prawidłowe, gdy ta struktura jest zwracana.

Wartości te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
