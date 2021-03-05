---
description: Określa rodzaj kroku do taktowania.
title: STEPKIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9cb230eac9e8851437614a590615ad2402923f6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225295"
---
# <a name="stepkind"></a>STEPKIND
Określa rodzaj kroku do taktowania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
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
 Kroki dotyczące funkcji.

 `STEP_OUT`\
 Kroki z funkcji.

 `STEP_BACKWARDS`\
 Kroki do tyłu w funkcji.

## <a name="remarks"></a>Uwagi
 Przekazanie jako argument do metody [kroku](../../../extensibility/debugger/reference/idebugprocess3-step.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)
