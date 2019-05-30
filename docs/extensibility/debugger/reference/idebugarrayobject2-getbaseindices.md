---
title: IDebugArrayObject2::GetBaseIndices | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04252ed40cd0ac2c0e5f41bc1104104aeee302c4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317574"
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

## <a name="parameters"></a>Parametry
`dwRank`\
[in] Liczba wymiarów (ranga) w tablicy.

`dwIndices`\
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

## <a name="see-also"></a>Zobacz także
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)