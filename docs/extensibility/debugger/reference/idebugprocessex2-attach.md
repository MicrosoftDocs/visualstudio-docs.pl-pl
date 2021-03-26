---
description: Ta metoda informuje proces, że sesja jest teraz debugowana w procesie.
title: 'IDebugProcessEx2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: da538b5ba91a976e96f447ba63843f20ae0b6f62
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076371"
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
