---
description: Pobiera kontekst dokumentu opisujący lokalizację tego zdarzenia.
title: 'IDebugCanStopEvent2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44e1f2aa918547d8b3b0b1bea1940072fe2d8f84
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085082"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
Pobiera kontekst dokumentu opisujący lokalizację tego zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocCxt
);
```

## <a name="parameters"></a>Parametry
`ppDocCxt`\
określoną Zwraca interfejs [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , który reprezentuje pozycję w dokumencie pliku źródłowego odpowiadającą bieżącej lokalizacji kodu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ogólnie rzecz biorąc, kontekst dokumentu może być uważany za pozycję w pliku źródłowym.

 Aby uzyskać kontekst kodu, który jest ukierunkowany na instrukcje kodu, wywołaj metodę [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
