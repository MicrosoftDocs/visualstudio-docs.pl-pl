---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d03d942bbc052a7ac6bebc6a89c55ec21a1b4c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723122"
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
