---
title: IDebugProcessEx2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62ca404442d6bf6080972f03c3e2fd0da2621e20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954894"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Ta metoda informuje proces, że sesja nie jest już debugowana w procesie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parametry
`pSession`\
podczas Wartość, która jednoznacznie identyfikuje sesję, z której ma zostać odłączony ten proces.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Przekazany Interfejs `pSession` ma być traktowany tylko jako plik cookie, czyli wartość, która jednoznacznie identyfikuje Menedżera debugowania sesji, który został pierwotnie dołączony do tego procesu; żadna z metod interfejsu nie jest funkcjonalna.

## <a name="see-also"></a>Zobacz też
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
