---
description: Pobiera kontekst dokumentu odnoszący się do tego kontekstu kodu.
title: 'IDebugCodeContext2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99b67e76c8cc8719c77c88c8b93ca667c3a025a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164165"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Pobiera kontekst dokumentu odnoszący się do tego kontekstu kodu. Kontekst dokumentu reprezentuje pozycję w pliku źródłowym, która odnosi się do kodu źródłowego, który wygenerował tę instrukcję.

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
określoną Zwraca obiekt [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , który odnosi się do kontekstu kodu. Jeśli `S_OK` jest zwracany, tego nie powinien być `null` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Aparat debugowania powinien zwrócić kod błędu, taki jak, `E_FAIL` gdy `out` parametr jest `null` taki jak, gdy kontekst kodu nie ma skojarzonej pozycji źródłowej.

## <a name="remarks"></a>Uwagi
 Ogólnie rzecz biorąc, kontekst dokumentu może być uważany za pozycję w pliku źródłowym, podczas gdy kontekst kodu jest pozycją instrukcji kodu w strumieniu wykonywania.

## <a name="see-also"></a>Zobacz też
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
