---
description: Określa styl warunku punktu przerwania dla oczekujących i powiązanych punktów przerwania.
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c23549d1553902c00048f946d2711c497fbe2322
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144484"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Określa styl warunku punktu przerwania dla oczekujących i powiązanych punktów przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Pola
`BP_COND_NONE`\
Uruchamia punkt przerwania po osiągnięciu położenia punktu przerwania. Nie określono warunku punktu przerwania.

`BP_COND_WHEN_TRUE`\
Uruchamia punkt przerwania tylko wtedy, gdy wyrażenie warunkowe skojarzone z punktem przerwania szacuje się na `true` .

`BP_COND_WHEN_CHANGED`\
Uruchamia punkt przerwania tylko wtedy, gdy wartość wyrażenia warunkowego skojarzonego z punktem przerwania zmieniła się od poprzedniej wersji ewaluacyjnej.

## <a name="remarks"></a>Uwagi
Używane dla `styleCondition` elementu członkowskiego struktury [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
