---
title: IDebugIDECallback::DisplayMessage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a80fbc6e621e4cf1619aa310e5f7cd8beba47d7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349065"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
Wysyła ciągu określony komunikat do okna danych wyjściowych debugera.

## <a name="syntax"></a>Składnia

```cpp
HRESULT DisplayMessage (
   LPCOLESTR szMessage
);
```

```csharp
int DisplayMessage (
   string szMessage
);
```

## <a name="parameters"></a>Parametry
`szMessage`\
[in] Ciąg komunikatu do wyświetlenia w oknie danych wyjściowych debugera.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)