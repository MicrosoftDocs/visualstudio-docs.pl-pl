---
description: Ta metoda pobiera listę typów argumentów skojarzonych z tym obiektem.
title: 'IDebugBinder3:: GetTypeArguments — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74cbd6e67a82113e43226ded8640630be50ba086
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173900"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Ta metoda pobiera listę typów argumentów skojarzonych z tym obiektem.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

## <a name="parameters"></a>Parametry
`skip`\
podczas Liczba pól do pominięcia przed pobraniem typów argumentów.

`count`\
podczas Liczba pól argumentów do zwrócenia (określa również rozmiar `ppFields` tablicy).

`ppFields`\
[in. out] Tablica pól, które będą wypełniane po powrocie tej metody.

`pFetched`\
[out] \( Opcjonalnie) liczba pól typu argumentu faktycznie zwróconych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Liczbę typów argumentów można uzyskać wcześniej za pomocą [GetTypeArgumentCount —](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md).

## <a name="see-also"></a>Zobacz też
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)
