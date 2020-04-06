---
title: IDebugCodeContext2::GetDocumentContext | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734343"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Pobiera kontekst dokumentu, który odpowiada temu kontekstowi kodu. Kontekst dokumentu reprezentuje pozycję w pliku źródłowym, która odpowiada kodowi źródłowemu, który wygenerował tę instrukcję.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Parametry
`ppSrcCxt`\
[na zewnątrz] Zwraca [obiekt IDebugDocumentContext2,](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) który odpowiada kontekstowi kodu. Jeśli `S_OK` jest zwracany, ths`null`powinny być non- .

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Aparat debugowania powinien zwracać `E_FAIL` kod `out` błędu, `null` na przykład gdy parametr jest taki jak wtedy, gdy kontekst kodu nie ma skojarzonej pozycji źródłowej.

## <a name="remarks"></a>Uwagi
 Ogólnie rzecz biorąc kontekst dokumentu można traktować jako pozycję w pliku źródłowym, podczas gdy kontekst kodu jest pozycją instrukcji kodu w strumieniu wykonania.

## <a name="see-also"></a>Zobacz też
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
