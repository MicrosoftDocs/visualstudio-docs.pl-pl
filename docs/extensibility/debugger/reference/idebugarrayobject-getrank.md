---
title: IDebugArrayObject::GetRank | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a733baf1be2e5a249c214547b31465bb2464ed6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351786"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Pobiera rangę tablicy, czyli liczbę wymiarów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parametry
`pdwRank`\
[out] Zwraca rangę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Użyj [getdimensions —](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) metodę, aby pobrać rozmiar każdego wymiaru obiektu array.

## <a name="see-also"></a>Zobacz także
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)