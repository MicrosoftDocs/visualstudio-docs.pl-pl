---
title: IDebugEngine2::SetException | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 288e77ce539a26764a897656c79649720be2438e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698914"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Określa, jak aparat debugowania (DE) powinna obsługiwać dany wyjątek.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

#### <a name="parameters"></a>Parametry
 `pException`

 [in] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury, który opisuje wyjątek i jak go debugować.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 DE może być zobowiązany do zatrzymać program generuje wyjątek w pierwszej szansy, drugiej szansy, lub wcale.

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)