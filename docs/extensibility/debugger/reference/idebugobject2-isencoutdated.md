---
title: IDebugObject2::IsEnc Przestarzałe | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a90ff97b87ec2abaab87dfece5b2a2ac1cabb28c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726102"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Ta metoda określa, czy stan Edytuj i Kontynuuj tego obiektu lub kontenera nadrzędnego jest nieaktualny. Oceniający wyrażenie niestandardowe nie implementuje `E_NOTIMPL`tej metody i zawsze zwraca .

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
[na zewnątrz] Nonzero`TRUE`( ), jeśli stan Edytuj i Kontynuuj`FALSE`jest nieaktualny, zero ( ), jeśli nie jest.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Ewaluator wyrażeń `E_NOTIMPL`niestandardowych powinien zawsze zwracać .

## <a name="see-also"></a>Zobacz też
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
