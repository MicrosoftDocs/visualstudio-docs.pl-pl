---
title: BP_COND_STYLE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca704ca186308ea9e44c4fa7edc6617cbac806eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738111"
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
Uruchamia punkt przerwania po osiągnięciu pozycji punktu przerwania. Nie określono warunku punktu przerwania.

`BP_COND_WHEN_TRUE`\
Uruchamia punkt przerwania tylko wtedy, gdy wyrażenie warunkowe `true`skojarzone z punktem przerwania jest obliczane na .

`BP_COND_WHEN_CHANGED`\
Uruchamia punkt przerwania tylko wtedy, gdy wartość wyrażenia warunkowego skojarzonego z punktem przerwania uległa zmianie w stosunku do poprzedniej oceny.

## <a name="remarks"></a>Uwagi
Używany dla `styleCondition` członka struktury [BP_CONDITION.](../../../extensibility/debugger/reference/bp-condition.md)

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
