---
title: IDebugArrayObject::GetRank | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0391030e77e5959fdc28c94f63e099e5c505d77
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683899"
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

#### <a name="parameters"></a>Parametry
 `pdwRank`

 [out] Zwraca rangę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Użyj [getdimensions —](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) metodę, aby pobrać rozmiar każdego wymiaru obiektu array.

## <a name="see-also"></a>Zobacz też
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)