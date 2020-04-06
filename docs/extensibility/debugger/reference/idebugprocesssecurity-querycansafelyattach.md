---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e03ccbb7761802401239768c54f4ea5b36ab86bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723200"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Ta metoda umożliwia dostawcy portu wyświetlanie ostrzeżenia, zanim użytkownik dołączy do niebezpiecznego procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Wartość zwracana
 Zwracane wartości są następujące:

- `S_OK`: Dołączanie do procesu jest bezpieczne i nie jest wyświetlane żadne okno dialogowe z ostrzeżeniem.

- `S_FALSE`: Dołączanie może być problemem bezpieczeństwa i wyświetlane jest okno dialogowe z ostrzeżeniem.

- `FAILURE`: Podłączenie do procesu kończy się niepowodzeniem.

## <a name="see-also"></a>Zobacz też
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
