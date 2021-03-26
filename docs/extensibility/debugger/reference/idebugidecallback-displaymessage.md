---
description: Wysyła określony ciąg komunikatu do okna danych wyjściowych debugera.
title: IDebugIDECallback::D isplayMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6968c524559280756014bb6b26f55f688bc38ab3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091945"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
Wysyła określony ciąg komunikatu do okna danych wyjściowych debugera.

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
podczas Ciąg komunikatu do wyświetlenia w oknie danych wyjściowych debugera.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
