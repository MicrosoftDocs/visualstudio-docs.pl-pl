---
description: Wylicza prawidłowe wartości reprezentujące rodzaje informacji, które mają być wykonywane z obiektu IDebugField i wyświetlane użytkownikowi.
title: DisplayKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8c474c9295ceedbdffd286e99975c375ea69fc4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096034"
---
# <a name="displaykind"></a>DisplayKind
Wylicza prawidłowe wartości reprezentujące rodzaje informacji, które mają być wykonywane z obiektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i wyświetlane użytkownikowi.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
typedef DWORD DisplayKind;
```

```csharp
public enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
```

## <a name="fields"></a>Pola
`DisplayKind_Value`\
Wartość pola.

`DisplayKind_Name`\
Nazwa pola.

`DisplayKind_Type`\
Typ pola.

## <a name="requirements"></a>Wymagania
Nagłówek: EE. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)
