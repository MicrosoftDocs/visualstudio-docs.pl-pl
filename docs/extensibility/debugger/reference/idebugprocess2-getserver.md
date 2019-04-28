---
title: IDebugProcess2::GetServer | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetServer
helpviewer_keywords:
- IDebugProcess2::GetServer
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33f9b513bcf336cac68af7d915880af0652b0954
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917768"
---
# <a name="idebugprocess2getserver"></a>IDebugProcess2::GetServer
Pobiera serwera, na którym uruchomiono ten proces.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetServer( 
   IDebugCoreServer2** ppServer
);
```

```csharp
int GetServer( 
   out IDebugCoreServer2 ppServer
);
```

#### <a name="parameters"></a>Parametry
 `ppServer`

 [out] Zwraca [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) obiekt, który reprezentuje serwer, na którym działa ten proces.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Więcej niż jeden serwer może działać na jednym komputerze.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)