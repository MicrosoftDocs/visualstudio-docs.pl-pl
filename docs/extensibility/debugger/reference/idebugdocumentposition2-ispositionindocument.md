---
title: IDebugDocumentPosition2::IsPositionInDocument | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab4792427a98f97fcd50d4b39c2bb332527a0942
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333413"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Określa, jeśli położenie dokumentu jest zawarty w danym dokumencie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsPositionInDocument( 
   IDebugDocument2* pDoc
);
```

```csharp
int IsPositionInDocument( 
   IDebugDocument2 pDoc
);
```

## <a name="parameters"></a>Parametry
`pDoc`\
[in] [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) obiekt, który reprezentuje zawierającego Release candidate dokumentu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest używana głównie w przypadku ustawiania punktów przerwania [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejsów. W miarę ładowania, by określić czy dokument zawiera ta pozycja nosi nazwę położenie punktu przerwania.

## <a name="see-also"></a>Zobacz także
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)