---
title: IDebugPortSupplier2::CanAddPort | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19eb4d11ab6e67384a119f11bf070a27159c1676
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696119"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Sprawdza, czy dostawca portu można dodawać nowych portów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Wartość zwracana
 Można dodać portu, funkcja zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` do wskazania żadnych portów mogą być dodawane do tego dostawcy portu.

## <a name="remarks"></a>Uwagi
 Wywołanie tej metody, przed wywołaniem [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) metody, ponieważ druga metoda tworzy portu, a także dodawanie, co może być czasochłonna operacja.

## <a name="see-also"></a>Zobacz też
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)