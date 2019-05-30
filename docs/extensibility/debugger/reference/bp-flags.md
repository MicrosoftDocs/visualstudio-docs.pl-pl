---
title: BP_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31f5153c3a2d0b55829a7743840fe8a791f023d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319223"
---
# <a name="bpflags"></a>BP_FLAGS
Zawiera flagi opcjonalne, które mogą być używane do określania dodatkowych informacji, gdy ustawienie punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Pola
`BP_FLAG_NONE`\
Określa flagę nie punktu przerwania.

`BP_FLAG_MAP_DOCPOSITION`\
Określa, że aparat debugowania (DE) powinny być mapowane punkt przerwania przy użyciu położenie dokumentu. Dotyczy tylko punkty przerwania ustawione w plikach źródłowych zorientowane na skrypt takie jak Active Server Pages (ASP).

`BP_FLAG_DONT_STOP`\
Określa, że punkt przerwania mają być przetwarzane przez aparat debugowania, ale że aparat debugowania ostatecznie nie należy zatrzymywać istnieje (czyli [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) obiektu zdarzenia nie powinny być przesyłane). Ta flaga jest przeznaczony do służyć przede wszystkim z punktami śledzenia.

## <a name="remarks"></a>Uwagi
Używany do `dwFlags` członkiem [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.

Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
