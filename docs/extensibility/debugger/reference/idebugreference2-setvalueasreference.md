---
title: IDebugReference2::SetValueAsReference | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 108061d4957b03d049897985da849ab86563ea47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339751"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Ustawia wartość odwołanie z innego odwołania. Zarezerwowane do użytku w przyszłości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parametry
`rgpArgs`\
[in] Tablica [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiekty używane do określania, jak można ustawić wartości odwołania.

`dwArgCount`\
[in] Liczba odwołań w tablicy.

`pValue`\
[in] [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiektu, z którego można ustawić wartości właściwości.

`dwTimeout`\
[in] Maksymalny czas (w milisekundach) oczekiwania przed zwróceniem z tej metody. Użyj `INFINITE` czekanie w nieskończoność.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz także
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)