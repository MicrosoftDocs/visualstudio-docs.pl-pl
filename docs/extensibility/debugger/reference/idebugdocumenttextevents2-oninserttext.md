---
title: IDebugDocumentTextEvents2::onInsertText | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnInsertText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onInsertText
ms.assetid: 6040181f-7288-4a42-953c-d23f74200431
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a9c10449d324b33d601840ed24d5f8db9a4b1ae
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199146"
---
# <a name="idebugdocumenttextevents2oninserttext"></a>IDebugDocumentTextEvents2::onInsertText
Powiadamia pakietu debugowania, że włożono tekstu do dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT onInsert( 
   TEXT_POSITION pos,
   DWORD         dwNumToInsert
);
```

```csharp
int onInsert( 
   enum_TEXT_POSITION pos,
   uint               dwNumToInsert
);
```

## <a name="parameters"></a>Parametry
`pos`\
[in] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) strukturę, która wskazuje, gdzie został wstawiony tekst.

`dwNumToInsert`\
[in] Określa liczbę znaków tekstu, które zostały wprowadzone.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)