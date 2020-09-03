---
title: 'IDebugObject2:: IsEncOutdated | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726102"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Ta metoda określa, czy stan edycji i kontynuowania tego obiektu lub kontenera nadrzędnego jest nieaktualny. Niestandardowa ewaluatora wyrażeń nie implementuje tej metody i zawsze zwraca wartość `E_NOTIMPL` .

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
określoną Różna od zera ( `TRUE` ), jeśli stan Edytuj i Kontynuuj jest nieaktualny, zero ( `FALSE` ), jeśli nie jest.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Niestandardowa ewaluatora wyrażeń powinna zawsze zwracać wartość `E_NOTIMPL` .

## <a name="see-also"></a>Zobacz też
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
