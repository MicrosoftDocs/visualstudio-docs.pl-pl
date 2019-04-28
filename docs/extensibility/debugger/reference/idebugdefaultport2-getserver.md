---
title: IDebugDefaultPort2::GetServer | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cbfc81495c1f2319117a236246f1e7c47f3e582
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875987"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Ta metoda pobiera interfejs do serwera, na którym znajduje się na tym porcie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

#### <a name="parameters"></a>Parametry
 `ppServer`

 [out] Zwraca obiekt Implementowanie [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) interfejsu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) jest implementowany przez program Visual Studio i reprezentuje serwer, który port znajduje się na.

## <a name="see-also"></a>Zobacz też
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)