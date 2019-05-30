---
title: IDebugDocumentTextEvents2::onUpdateTextAttributes | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateTextAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateTextAttributes
ms.assetid: eb68d69a-1ad9-4ce4-84e1-40979ef16634
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a1eb8d6d9f14fcad5358b4a358673e08f3395ff
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351366"
---
# <a name="idebugdocumenttextevents2onupdatetextattributes"></a>IDebugDocumentTextEvents2::onUpdateTextAttributes
Powiadamia pakietu debugowania, atrybuty zostały zaktualizowane w dokumencie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT onUpdateTextAttributes( 
   TEXT_POSITION pos,
   DWORD         dwNumToUpdate
);
```

```csharp
int onUpdateTextAttributes( 
   enum_TEXT_POSITION pos,
   uint               dwNumToUpdate
);
```

## <a name="parameters"></a>Parametry
`pos`\
[in] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) strukturę, która wskazuje, gdzie zostały zaktualizowane atrybutów tekstu.

`dwNumToUpdate`\
[in] Określa liczbę znaków tekstu, które zostały zaktualizowane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)