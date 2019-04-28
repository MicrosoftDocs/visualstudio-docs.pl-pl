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
ms.openlocfilehash: 891a0c200b02f8768ef68d1d87649bfd35cf59d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917541"
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

## <a name="see-also"></a>Zobacz też
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)