---
description: Pobiera identyfikator procesu, który hostuje ten program.
title: 'IDebugProgramHost2:: GetHostId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostId
helpviewer_keywords:
- IDebugProgramHost2::GetHostId
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9784c8e54ee5c75ed33a0aaf513f71dd09f6191
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168130"
---
# <a name="idebugprogramhost2gethostid"></a>IDebugProgramHost2::GetHostId
Pobiera identyfikator procesu, który hostuje ten program.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetHostId( 
   AD_PROCESS_ID* pdwId
);
```

```csharp
int GetHostId( 
   AD_PROCESS_ID[] pdwId
);
```

## <a name="parameters"></a>Parametry
`pdwId`\
[in. out] Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , która jest wypełniana informacjami o identyfikatorze procesu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
