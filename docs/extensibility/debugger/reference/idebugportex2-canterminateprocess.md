---
title: IDebugPortEx2::CanTerminateProcess | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db1a4fedac88208d54d146a6c5b74b847db21866
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311138"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
Określa, czy Proces może zostać zakończone.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanTerminateProcess( 
   IDebugProcess2* pPortProcess
);
```

```csharp
HRESULT CanTerminateProcess( 
   IDebugProcess2 pPortProcess
);
```

## <a name="parameters"></a>Parametry
`pPortProcess`\
[in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) obiekt reprezentujący procesu, który ma zostać zakończony.

## <a name="return-value"></a>Wartość zwracana
 Zwraca `S_OK` przypadku można zakończyć procesu; w przeciwnym razie zwraca `S_FALSE`.

## <a name="see-also"></a>Zobacz także
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)