---
title: IDebugArrayField::GetRank | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f2f13d861d9688ba349fbc80cb1ca426582c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736308"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Pobiera rangi lub liczby wymiarów tablicy.

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
[na zewnątrz] Zwraca rangę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ranga tablicy odpowiada liczbie wymiarów. W językach C++ i C#tablice wielowymiarowe są naprawdę tablicami tablic i dlatego można `GetRank` je uznać za tylko tablicę jednowymiarową (a metoda zawsze zwraca wartość 1). Z [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]drugiej strony w tablicach wielowymiarowych są obsługiwane w różny sposób, a ranga `GetRank` takiej tablicy odzwierciedla liczbę wymiarów (a metoda zawsze zwraca liczbę wymiarów).

## <a name="see-also"></a>Zobacz też
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
