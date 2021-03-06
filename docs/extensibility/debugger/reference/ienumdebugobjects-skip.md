---
description: Ta metoda pomija określoną liczbę elementów IDebugObject.
title: 'IEnumDebugObjects:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 962083242b5b178ddf39e21328917d09dc0ed09a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224645"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
Ta metoda pomija określoną liczbę elementów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   [In] uint celt
);
```

## <a name="parameters"></a>Parametry
`celt`\
podczas Liczba elementów do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` wartość `celt` , jeśli jest większa niż liczba pozostałych elementów; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli `celt` wartość jest większa niż liczba pozostałych elementów, Wyliczenie zostanie ustawione na koniec i `S_FALSE` zostanie zwrócone.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
