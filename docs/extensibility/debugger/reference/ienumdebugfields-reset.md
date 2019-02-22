---
title: IEnumDebugFields::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6bf669261a3ece31e452227b7c93d7ce8bf07c1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697718"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
Ta metoda powoduje zresetowanie wyliczenia do pierwszego elementu.

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
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Po ta metoda jest wywoływana, następnym wywołaniu [dalej](../../../extensibility/debugger/reference/ienumdebugfields-next.md) zwraca pierwszy element wyliczenia.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md)