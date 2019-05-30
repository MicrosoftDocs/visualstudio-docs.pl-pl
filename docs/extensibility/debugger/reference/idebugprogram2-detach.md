---
title: IDebugProgram2::Detach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Detach
helpviewer_keywords:
- IDebugProgram2::Detach
ms.assetid: 5e8d88b0-a8d4-4746-88c0-ad332ee73f33
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3259a2b9d0f9c617aaeebaebfae0713da5d3f9f5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326873"
---
# <a name="idebugprogram2detach"></a>IDebugProgram2::Detach
Odłącza aparatu debugowania programu.

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
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Odłączyć program będzie kontynuował działanie, ale nie jest już częścią sesji debugowania. Program debugowania zdarzenia nie są wysyłane po odłączeniu aparatu debugowania.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)