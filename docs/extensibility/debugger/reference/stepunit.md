---
title: STEPUNIT | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a87c86647407d90c9f4292b1307fd5623e85d13b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713522"
---
# <a name="stepunit"></a>STEPUNIT
Określa jednostkę kroku dla kroków krokowych.

## <a name="syntax"></a>Składnia

```cpp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
typedef DWORD STEPUNIT;
```

```csharp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
```

## <a name="fields"></a>Pola
 `STEP_STATEMENT`\
 Kroki według instrukcji.

 `STEP_LINE`\
 Kroki po wierszu.

 `STEP_INSTRUCTION`\
 Kroki według instrukcji.

## <a name="remarks"></a>Uwagi
 Przekazany jako argument do [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) metody.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)
