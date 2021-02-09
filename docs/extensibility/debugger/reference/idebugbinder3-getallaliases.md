---
title: 'IDebugBinder3:: GetAllAliases | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea8de97a82959b1135866988aeeeb14cf464e8b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925077"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Ta metoda pobiera listę aliasów z programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>Parametry
`uRequest`\
podczas Maksymalna liczba aliasów do zwrócenia (określa długość tablicy, do której została przeniesiona `ppAliases` ).

`ppAliases`\
[in. out] Tablica do wypełnienia przy użyciu aliasów (jeśli jest to wartość zerowa i `uRequest` wynosi 0, liczba aliasów, które mogą zostać zwrócone, będzie zwracana przez `puFetched` ).

`puFetched`\
określoną Zwraca liczbę uzyskanych aliasów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
