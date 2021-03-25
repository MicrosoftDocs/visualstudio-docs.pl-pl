---
description: Określa jednostkę kroku do taktowania.
title: STEPUNIT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e27aa1e26c9ac80356446c59f0f7775d35328517
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061488"
---
# <a name="stepunit"></a>STEPUNIT
Określa jednostkę kroku do taktowania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
typedef DWORD STEPUNIT;
```

```csharp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
```

## <a name="fields"></a>Pola
 `STEP_STATEMENT`\
 Kroki według instrukcji.

 `STEP_LINE`\
 Kroki według wiersza.

 `STEP_INSTRUCTION`\
 Kroki według instrukcji.

## <a name="remarks"></a>Uwagi
 Przekazanie jako argument do metody [kroku](../../../extensibility/debugger/reference/idebugprocess3-step.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)
