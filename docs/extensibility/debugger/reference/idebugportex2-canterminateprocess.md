---
title: IDebugPortEx2::CanTerminateProcess | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bbc5c5128c1235c7ee46300a1cd45f92b53d243d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725159"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
Określa, czy proces można zakończyć.

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
[w] Obiekt [IDebugProcess2 reprezentujący](../../../extensibility/debugger/reference/idebugprocess2.md) proces, który ma zostać zakończony.

## <a name="return-value"></a>Wartość zwracana
 Zwraca, `S_OK` jeśli proces może zostać zakończony; w przeciwnym `S_FALSE`razie zwraca plik .

## <a name="see-also"></a>Zobacz też
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
