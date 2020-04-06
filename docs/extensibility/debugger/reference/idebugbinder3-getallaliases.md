---
title: IDebugBinder3::GetAllAliases | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d512fa6eb7529e11c766d7c173b318aa6f8f2f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735808"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Ta metoda pobiera listę aliasów z programu.

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

## <a name="parameters"></a>Parametry
`uRequest`\
[w] Maksymalna liczba aliasów do zwrócenia (określa długość tablicy przekazywanej do `ppAliases`).

`ppAliases`\
[w, na zewnątrz] Tablica do wypełnienia aliasami (jeśli jest `uRequest` to wartość null i wynosi 0, liczba aliasów, które mogą być zwracane, zostanie zwrócona przez `puFetched`).

`puFetched`\
[na zewnątrz] Zwraca liczbę uzyskanych aliasów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
