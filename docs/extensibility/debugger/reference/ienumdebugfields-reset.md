---
description: Ta metoda resetuje Wyliczenie pól do pierwszego elementu.
title: 'IEnumDebugFields:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2edf4751151779297d6ff8ed9ffa930cc7bf3868
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086545"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
Ta metoda resetuje Wyliczenie do pierwszego elementu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Po wywołaniu tej metody następne wywołanie [Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md) zwraca pierwszy element wyliczenia.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
