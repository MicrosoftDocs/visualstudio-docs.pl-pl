---
title: IDebugPortSupplier2::CanAddPort | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37f4fd246c376d08ab3ca006c543b44c4db2d73d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340290"
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

## <a name="see-also"></a>Zobacz także
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)