---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e718efddc90c45ced7e497a9c66c9ab3889c090
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311437"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Ta metoda umożliwia dostawcy portu wyświetlić ostrzeżenie, zanim użytkownik dołącza do procesu niebezpieczne.

## <a name="syntax"></a>Składnia

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Wartość zwracana
 Wartości zwracane są następujące:

- `S_OK`: Dołączanie do procesu jest bezpieczne, a okno dialogowe ostrzeżenia o nie jest wyświetlany.

- `S_FALSE`: Dołączanie może być problem z zabezpieczeniami i wyświetlane jest okno dialogowe z ostrzeżeniem.

- `FAILURE`: Dołączanie do procesu nie powiodło się.

## <a name="see-also"></a>Zobacz także
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)