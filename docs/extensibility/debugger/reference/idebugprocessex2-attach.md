---
title: 'IDebugProcessEx2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d70da2530a1677367a22968436a17eba809fd24a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723380"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Ta metoda informuje proces, że sesja jest teraz debugowana w procesie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parametry
`pSession`\
podczas Wartość, która jednoznacznie identyfikuje sesję dołączenia do tego procesu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Przekazany Interfejs `pSession` ma być traktowany tylko jako plik cookie, wartość, która jednoznacznie identyfikuje Menedżera debugowania sesji dołączenia do tego procesu; żadna z metod w interfejsie nie jest funkcjonalna.

## <a name="see-also"></a>Zobacz też
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
