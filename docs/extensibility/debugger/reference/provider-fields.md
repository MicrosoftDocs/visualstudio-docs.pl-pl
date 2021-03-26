---
description: Określa właściwości skojarzone z dostawcą programu.
title: PROVIDER_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1ab410d9780078cd786b75f14d0321498eca8fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079543"
---
# <a name="provider_fields"></a>PROVIDER_FIELDS
Określa właściwości skojarzone z dostawcą programu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
typedef DWORD PROVIDER_FIELDS;
```

```csharp
public enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
```

## <a name="fields"></a>Pola
 `PFIELD_PROGRAM_NODES`\
 `ProgramNodes`Pole jest prawidłowe.

 `PFIELD_IS_DEBUGGER_PRESENT`\
 `fIsDebuggerPresent`Pole jest prawidłowe.

## <a name="remarks"></a>Uwagi
 Te wartości są zwracane w `Fields` składowej struktury [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) , aby wskazać, które pola struktury zostały jawnie wypełnione.

 Te wartości mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
