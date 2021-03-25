---
description: Ta metoda umożliwia dostawcom portu wyświetlanie ostrzeżenia przed dołączeniem użytkownika do niebezpiecznego procesu.
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbbfcf11a35fcfc43ae9e903b13a7480a3cf9743
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076280"
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
