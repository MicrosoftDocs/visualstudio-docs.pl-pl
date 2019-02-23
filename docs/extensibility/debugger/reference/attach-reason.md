---
title: ATTACH_REASON | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11fba0944ca1b23c22caae6f0d6a4d9455099946
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688267"
---
# <a name="attachreason"></a>ATTACH_REASON
Określa przyczyny aparat debugowania (DE) można dołączyć do węzła programu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="members"></a>Elementy członkowskie
ATTACH_REASON_AUTO dołączyć, ponieważ proces jest obecnie w trybie debugowania.

ATTACH_REASON_LAUNCH dołączyć, ponieważ proces został uruchomiony.

Dołącz ATTACH_REASON_USER ze względu na żądanie użytkownika.

## <a name="remarks"></a>Uwagi
Wartości te są używane jako parametr do [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) i [Dołącz](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
