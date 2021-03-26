---
description: Pobiera opis portu, który został wcześniej użyty do utworzenia portu (jeśli jest dostępny).
title: 'IDebugPort2:: GetPortRequest | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77224f98d953b61529ffed083e7be4cee0ed662f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087486"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Pobiera opis portu, który został wcześniej użyty do utworzenia portu (jeśli jest dostępny).

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Parametry
`ppRequest`\
określoną Zwraca obiekt [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) reprezentujący żądanie, które zostało użyte do utworzenia portu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  Zwraca `E_PORT_NO_REQUEST` czy port nie został utworzony przy użyciu żądania portu [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
