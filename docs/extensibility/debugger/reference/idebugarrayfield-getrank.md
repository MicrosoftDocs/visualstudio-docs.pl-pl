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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9e3d822bac6fa16314f5d2962d69adbf74d0bc3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143717"
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
