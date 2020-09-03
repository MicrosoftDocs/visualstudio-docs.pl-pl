---
title: IDebugProcess2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9036ebc44835ab6c3ebd08b9fad4408d9cb97461
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724127"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Odłącza debuger od tego procesu, odłączając wszystkie programy w procesie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wszystkie programy i procesy nadal działają, ale nie są już częścią sesji debugowania. Po zakończeniu operacji odłączenia nie będą wysyłane żadne zdarzenia debugowania dla tego procesu (i jego programów).

## <a name="see-also"></a>Zobacz też
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
