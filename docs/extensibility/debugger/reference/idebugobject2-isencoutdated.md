---
title: IDebugObject2::IsEncOutdated | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b2d26b49f3d2597e12e11a323a9281bd5c676fa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317416"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Ta metoda określa, czy stan Edytuj i Kontynuuj tego obiektu lub kontenera nadrzędnego jest nieaktualna. Ewaluator wyrażeń niestandardowych nie implementuje tę metodę i zawsze zwraca `E_NOTIMPL`.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Parametry
`pfEncOutdated`\
[out] Wartość różną od zera (`TRUE`) Jeśli stan Edytuj i Kontynuuj jest nieaktualna, zero (`FALSE`) Jeśli nie jest.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Ewaluator wyrażeń niestandardowych zawsze powinna zwrócić `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz także
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)