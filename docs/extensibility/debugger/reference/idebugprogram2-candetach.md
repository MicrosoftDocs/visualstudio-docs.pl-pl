---
description: Określa, czy aparat debugowania (DE) może odłączać od programu.
title: 'IDebugProgram2:: Odłączanie | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69bd7950d5b0cb884b8f59ae309265a0273d0944
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166076"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Określa, czy aparat debugowania (DE) może odłączać od programu.

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
 Jeśli może odłączać, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `S_FALSE` czy nie można odłączyć z programu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
