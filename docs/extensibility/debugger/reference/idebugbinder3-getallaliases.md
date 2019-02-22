---
title: IDebugBinder3::GetAllAliases | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed8545431dc0cb643ba18d415285447f8a66f66e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679934"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Ta metoda pobiera listę aliasów w ramach programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

#### <a name="parameters"></a>Parametry
 `uRequest`

 [in] Maksymalną liczbę aliasów do zwrócenia (określa długość tablicy przekazane do `ppAliases`).

 `ppAliases`

 [out w] Tablica do wypełnienia przy użyciu aliasów (jeśli jest to wartość null i `uRequest` wynosi 0, liczba aliasy, które mogą zostać zwrócone zostaną zwrócone przez `puFetched`).

 `puFetched`

 [out] Zwraca liczbę aliasów uzyskany.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)