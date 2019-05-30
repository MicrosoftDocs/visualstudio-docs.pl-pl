---
title: IDebugCanStopEvent2::GetDocumentContext | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c3d409b0fa4438331d1a798e5fd6e21b2c10ca9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349545"
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