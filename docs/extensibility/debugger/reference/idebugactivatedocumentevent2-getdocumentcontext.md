---
description: Pobiera kontekst dokumentu opisujący położenie w dokumencie, który ma zostać uaktywniony przez pakiet debugowania.
title: 'IDebugActivateDocumentEvent2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocumentContext
helpviewer_keywords:
- GetDocumentContext method
- IDebugActivateDocumentEvent2::GetDocumentContext method
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79344833eb5f8e46b4725828980e334b4049c01e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078165"
---
# <a name="idebugactivatedocumentevent2getdocumentcontext"></a>IDebugActivateDocumentEvent2::GetDocumentContext
Pobiera kontekst dokumentu opisujący położenie w dokumencie, który ma zostać uaktywniony przez pakiet debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocContext
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parametry
`ppDocContext`\
określoną Zwraca obiekt [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , który reprezentuje pozycję w dokumencie pliku źródłowego.

## <a name="remarks"></a>Uwagi
 Ta pozycja może być używana do wyświetlania karetki, na przykład.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
