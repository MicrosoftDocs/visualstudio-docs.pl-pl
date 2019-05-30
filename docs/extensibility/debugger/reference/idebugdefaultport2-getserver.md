---
title: IDebugDefaultPort2::GetServer | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c959c84335023a3d187808d754b44b4a0d2b950
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351743"
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

## <a name="parameters"></a>Parametry
`ppServer`\
[out] Zwraca obiekt Implementowanie [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) interfejsu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) jest implementowany przez program Visual Studio i reprezentuje serwer, który port znajduje się na.

## <a name="see-also"></a>Zobacz także
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)