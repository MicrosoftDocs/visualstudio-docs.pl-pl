---
title: IDebugDefaultPort2::QueryIsLocal | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42a21419af9be56647a835ee1d8ddab62e20f842
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351755"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Ta metoda określa, czy ten port jest na komputerze lokalnym.

## <a name="syntax"></a>Składnia

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Wartość zwracana
 Zwraca `S_OK` czy ten port jest lokalny (na tym samym komputerze co obiekt wywołujący) lub `S_FALSE` Jeśli port znajduje się na innym komputerze.

## <a name="see-also"></a>Zobacz także
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)