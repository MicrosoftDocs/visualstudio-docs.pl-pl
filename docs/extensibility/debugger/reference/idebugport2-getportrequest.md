---
title: IDebugPort2::GetPortRequest | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8a103316a292c444a35b8c819968d98cda777b6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678127"
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

#### <a name="parameters"></a>Parametry
 `ppRequest`

 [out] Zwraca [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) obiekt reprezentujący żądanie, które zostało użyte do utworzenia portu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  Zwraca `E_PORT_NO_REQUEST` Jeśli port nie został utworzony przy użyciu [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) port żądania.

## <a name="see-also"></a>Zobacz też
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)