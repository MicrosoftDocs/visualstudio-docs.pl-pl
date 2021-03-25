---
description: Pobiera rangę lub liczbę wymiarów tablicy.
title: 'IDebugArrayField:: getranga | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ac945e23090b649ffb5ad2f452ec9245aac81ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058979"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Pobiera rangę lub liczbę wymiarów tablicy.

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
określoną Zwraca rangę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ranga tablicy odpowiada liczbie wymiarów. W językach C++ i C# tablice wielowymiarowe są naprawdę tablicami tablic i dlatego można je traktować tylko jako tablicę jednowymiarową (a `GetRank` Metoda zawsze zwraca 1). Z [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] drugiej strony, wielowymiarowe tablice są obsługiwane inaczej, a ranga tablicy odzwierciedla liczbę wymiarów (a `GetRank` Metoda zawsze zwraca liczbę wymiarów).

## <a name="see-also"></a>Zobacz też
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
