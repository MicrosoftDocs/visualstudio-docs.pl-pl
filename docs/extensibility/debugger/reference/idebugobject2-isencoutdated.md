---
title: IDebugObject2::IsEncOutdated | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1707b8bc9444022f51a6edddc9d95ef363c409b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719161"
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

#### <a name="parameters"></a>Parametry
 `pfEncOutdated`

 [out] Wartość różną od zera (`TRUE`) Jeśli stan Edytuj i Kontynuuj jest nieaktualna, zero (`FALSE`) Jeśli nie jest.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
>  Ewaluator wyrażeń niestandardowych zawsze powinna zwrócić `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz też
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)