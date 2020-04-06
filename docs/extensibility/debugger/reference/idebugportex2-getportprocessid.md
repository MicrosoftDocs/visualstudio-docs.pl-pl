---
title: IDebugPortEx2::GetPortProcessId | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae974461e312c68e6fcc14150a08879ac7709950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725140"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Pobiera identyfikator procesu samego portu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>Parametry
`pdwProcessId`\
[na zewnątrz] Zwraca identyfikator procesu fizycznego samego portu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Na przykład w czasie wykonywania Win32 ta metoda zazwyczaj `GetCurrentProcessId` wywołuje funkcję Win32, aby uzyskać identyfikator procesu fizycznego.

## <a name="see-also"></a>Zobacz też
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
