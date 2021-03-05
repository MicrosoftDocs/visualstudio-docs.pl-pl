---
description: Określa, czy proces może być zakończony.
title: 'IDebugPortEx2:: CanTerminateProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11a850f844a77c0e137a7a6603ac14b31e7dc326
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169460"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
Określa, czy proces może być zakończony.

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
podczas Obiekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) reprezentujący proces, który ma zostać zakończony.

## <a name="return-value"></a>Wartość zwracana
 Zwraca `S_OK` Czy proces może być zakończony; w przeciwnym razie zwraca `S_FALSE` .

## <a name="see-also"></a>Zobacz też
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
