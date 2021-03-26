---
description: Ta metoda resetuje Wyliczenie adresów do pierwszego elementu.
title: 'IEnumDebugAddresses:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 385e650e908947288eafa6f3f2812db45f9721a3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083144"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
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
 Po wywołaniu tej metody następne wywołanie [Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) zwraca pierwszy element wyliczenia.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
