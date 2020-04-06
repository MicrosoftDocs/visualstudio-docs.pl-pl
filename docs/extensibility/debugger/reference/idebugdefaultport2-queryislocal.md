---
title: IDebugDefaultPort2::QueryIsLocal | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c06230f7bbd1825fe73a22f9b1fdc35aea35c499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732327"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Ta metoda określa, czy ten port znajduje się na komputerze lokalnym.

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
 Zwraca `S_OK` wartość, jeśli ten port jest lokalny (na `S_FALSE` tym samym komputerze co obiekt wywołujący) lub jeśli port znajduje się na innym komputerze.

## <a name="see-also"></a>Zobacz też
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
