---
title: STEPKIND | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa9c1805c7eaba480cd46ebc6e73ee370e3cbb22
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460775"
---
# <a name="stepkind"></a>STEPKIND
Określa rodzaj kroku przechodzenie krok po kroku.

## <a name="syntax"></a>Składnia

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>Pola
 `STEP_INTO`\
 Kroki do funkcji.

 `STEP_OVER`\
 Pomija funkcji.

 `STEP_OUT`\
 Kroki z funkcji.

 `STEP_BACKWARDS`\
 Kroki wstecz do funkcji.

## <a name="remarks"></a>Uwagi
 Przekazywany jako argument do [kroku](../../../extensibility/debugger/reference/idebugprocess3-step.md) metody.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)