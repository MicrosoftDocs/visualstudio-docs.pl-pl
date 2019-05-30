---
title: IDebugProgram2::CanDetach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6bc8f7ac644a893049592420ad8435ac896a62b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311480"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Określa, jeśli aparat debugowania (DE) można odłączyć od program.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli można odłączyć zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_FALSE` Jeśli DE nie można odłączyć od program.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)