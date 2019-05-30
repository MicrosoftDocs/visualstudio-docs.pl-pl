---
title: BP_COND_STYLE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ded3d31f9be2d0a02a238ead4bc989cc21b4922a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351815"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Określa styl warunku punktu przerwania dla oczekujące i powiązane punkty przerwania.

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
Uruchamia punkt przerwania, po osiągnięciu punktu przerwania pozycji. Nie określono warunek punktu przerwania.

`BP_COND_WHEN_TRUE`\
Uruchamia punkt przerwania, tylko jeśli wyrażenie warunkowe skojarzony punkt przerwania daje w wyniku `true`.

`BP_COND_WHEN_CHANGED`\
Uruchamiany punkt przerwania tylko wtedy, gdy wartość wyrażenia warunkowego skojarzony punkt przerwania został zmieniony z jego poprzedniej oceny.

## <a name="remarks"></a>Uwagi
Używany do `styleCondition` członkiem [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struktury.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
