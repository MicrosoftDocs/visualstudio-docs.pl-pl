---
description: Ta metoda resetuje Wyliczenie do pierwszego elementu IDebugObject.
title: 'IEnumDebugObjects:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 193f0f2f793c1ca1ee1af208105be33754a1effa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083053"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Ta metoda resetuje Wyliczenie do pierwszego elementu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Parametry
 Brak

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Po wywołaniu tej metody następne wywołanie [Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) zwraca pierwszy element wyliczenia.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)
