---
title: IDebugDocumentContext2::GetDocument | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetDocument
helpviewer_keywords:
- IDebugDocumentContext2::GetDocument
ms.assetid: c6d46c5d-ade8-4dc8-9862-8fc7876658c4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ce07bd2274bc2a4881acd98fb73266fc90c7bd8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341274"
---
# <a name="idebugdocumentcontext2getdocument"></a>IDebugDocumentContext2::GetDocument
Pobiera dokument, który zawiera ten kontekst dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDocument( 
   IDebugDocument2** ppDocument
);
```

```csharp
int GetDocument( 
   out IDebugDocument2 ppDocument
);
```

## <a name="parameters"></a>Parametry
`ppDocument`\
[out] Zwraca [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) obiekt, który reprezentuje dokument, który zawiera ten kontekst dokumentu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda służy do tych aparaty debugowania, zapewniających dokumentów bezpośrednio do środowiska IDE. W przeciwnym razie ta metoda powinna zwracać `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz także
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)