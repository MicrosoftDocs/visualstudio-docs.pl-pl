---
title: IDebugCoreServer2::GetPort | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44e801318a2a997e7c1ab2f863b737c4d6693e14
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708007"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Pobiera określonego portu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

#### <a name="parameters"></a>Parametry
 `guidPort`

 [in] Identyfikator GUID portu do pobrania.

 `ppPort`

 [out] Zwraca [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) obiekt reprezentujący odpowiedni port.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_PORTSUPPLIER_NO_PORT` przypadku ma portu z danym identyfikatorem.

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)