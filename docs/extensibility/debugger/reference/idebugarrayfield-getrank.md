---
title: IDebugArrayField::GetRank | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2097a2168b40129c66ae6c48e75fee385ea81a45
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615258"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Pobiera ranga lub liczba wymiarów tablicy.

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
 Ranga tablicy odpowiada liczbę wymiarów. W języku C++ i C# są naprawdę tablice tablic wielowymiarowych tablic, a w związku z tym można uznać za Jednowymiarowa tablica (i `GetRank` metoda zawsze zwraca 1). W [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], z drugiej strony, wielowymiarowe tablice są obsługiwane inaczej i rangę tablicy takich odzwierciedla liczbę wymiarów (i `GetRank` metoda zawsze zwraca liczbę wymiarów).

## <a name="see-also"></a>Zobacz także
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)