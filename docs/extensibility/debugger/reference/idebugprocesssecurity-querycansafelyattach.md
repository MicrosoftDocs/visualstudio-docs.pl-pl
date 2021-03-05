---
description: Ta metoda umożliwia dostawcom portu wyświetlanie ostrzeżenia przed dołączeniem użytkownika do niebezpiecznego procesu.
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e6a586983d64e8be27b15a0514234d1a321e943
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166167"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Ta metoda umożliwia dostawcom portu wyświetlanie ostrzeżenia przed dołączeniem użytkownika do niebezpiecznego procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Wartość zwracana
 Zwracane wartości są następujące:

- `S_OK`: Dołączanie do procesu jest bezpieczne i nie jest wyświetlane okno dialogowe ostrzeżenia.

- `S_FALSE`: Dołączanie może stanowić problem z zabezpieczeniami i wyświetlane jest okno dialogowe z ostrzeżeniem.

- `FAILURE`: Dołączanie do procesu nie powiodło się.

## <a name="see-also"></a>Zobacz też
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
