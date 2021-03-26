---
description: Pobiera dokument zawierający.
title: 'IDebugDocumentPosition2:: GetDocument | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetDocument
helpviewer_keywords:
- IDebugDocumentPosition2::GetDocument
ms.assetid: eaa172c9-5748-4ce1-a0e2-33c2063f6752
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5252ff2b469bc307bc73dc0136064b3b18700a0e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066480"
---
# <a name="idebugdocumentposition2getdocument"></a>IDebugDocumentPosition2::GetDocument
Pobiera dokument zawierający.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDocument( 
   IDebugDocument2** ppDoc
);
```

```csharp
int GetDocument( 
   out IDebugDocument2 ppDoc
);
```

## <a name="parameters"></a>Parametry
`ppDoc`\
określoną Zwraca obiekt [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , który reprezentuje dokument zawierający tę pozycję.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
