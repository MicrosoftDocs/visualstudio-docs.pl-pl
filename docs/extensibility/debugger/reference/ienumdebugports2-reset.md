---
title: 'IEnumDebugPorts2:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Reset
helpviewer_keywords:
- IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6247e48af98f5c21a0afc40577e18d38bba06506
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716186"
---
# <a name="ienumdebugports2reset"></a>IEnumDebugPorts2::Reset
Resetuje Wyliczenie do pierwszego elementu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Po wywołaniu tej metody następne wywołanie do [następnej](../../../extensibility/debugger/reference/ienumdebugports2-next.md) metody zwraca pierwszy element wyliczenia.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
