---
description: Pobiera kontekst kodu opisujący lokalizację tego zdarzenia.
title: 'IDebugCanStopEvent2:: GetCodeContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29863a16d59528e86f7c5a3449e7c321b2dcaf9d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173540"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
Pobiera kontekst kodu opisujący lokalizację tego zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCodeContext( 
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parametry
`ppCodeContext`\
określoną Zwraca obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , który reprezentuje bieżącą lokalizację kodu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W przypadku większości architektur czasu wykonywania, kontekst kodu może być uważany za adres w strumieniu wykonywania programu, wskazując konkretną instrukcję.

 Aby uzyskać kontekst dokumentu, który jest ukierunkowany na wiersze kodu źródłowego, wywołaj metodę [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
