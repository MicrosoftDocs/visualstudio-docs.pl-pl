---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44b125f44f3345e7bd28a9993a7a44be2e378b53
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701436"
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

-   `S_OK`: Dołączanie do procesu jest bezpieczne, a okno dialogowe ostrzeżenia o nie jest wyświetlany.

-   `S_FALSE`: Dołączanie może być problem z zabezpieczeniami i wyświetlane jest okno dialogowe z ostrzeżeniem.

-   `FAILURE`: Dołączanie do procesu nie powiodło się.

## <a name="see-also"></a>Zobacz też
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)