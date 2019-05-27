---
title: IDebugCanStopEvent2::GetDocumentContext | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1a1c323a20d38738976cd868f5b392214f9000fb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203148"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
Pobiera kontekst dokumentu, opisująca lokalizację tego zdarzenia.

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
[out] Zwraca [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejs, który reprezentuje pozycji w dokumencie pliku źródłowym odpowiadającą bieżącej lokalizacji kodu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ogólnie rzecz biorąc kontekstu dokumentu mogą być uważane za pozycji w pliku źródłowym.

 Aby uzyskać kontekst kodu, który jest zorientowany na instrukcje kodu, należy wywołać [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)