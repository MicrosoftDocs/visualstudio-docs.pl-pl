---
title: IDebugArrayObject2::GetBaseIndices | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5355e85007c04e523efa4030ca0603a01cf88c68
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704062"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Pobiera podstawowy indeksów (dolne granice) dla każdego indeksu, biorąc pod uwagę liczbę wymiarów w tablicy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetBaseIndices (
   DWORD  dwRank,
   DWORD* dwIndices
);
```

```csharp
int GetBaseIndices (
   uint       dwRank,
   out uint[] dwIndices
);
```

#### <a name="parameters"></a>Parametry
 `dwRank`

 [in] Liczba wymiarów (ranga) w tablicy.

 `dwIndices`

 [out] Wskaźniki podstawowej (dolne granice) dla tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Na przykład ta funkcja zwróci "5" dla tablicy, utworzone przez następujące C# kodu:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>Zobacz też
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)