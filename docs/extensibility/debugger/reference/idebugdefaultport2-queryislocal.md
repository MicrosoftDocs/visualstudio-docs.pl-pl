---
title: IDebugDefaultPort2::QueryIsLocal | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e9ca74b007c3da5ac3674813ff37c718cdd801e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685537"
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

## <a name="see-also"></a>Zobacz też
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)