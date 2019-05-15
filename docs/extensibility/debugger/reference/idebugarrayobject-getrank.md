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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aabaaed13de191e4e0ee8d8d0e8422d3df144210
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615212"
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