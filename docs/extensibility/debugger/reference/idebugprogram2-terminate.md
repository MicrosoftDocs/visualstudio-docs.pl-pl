---
title: IDebugProgram2::Zakończ | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722747"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Kończy program.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli to możliwe, program zostanie zakończony i wyładowany z procesu; w przeciwnym razie aparat debugowania (DE) wykona wszelkie niezbędne oczyszczanie.

 Ta metoda lub [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) metoda jest wywoływana przez IDE, zazwyczaj w odpowiedzi na użytkownika zatrzymanie wszystkich debugowania. Implementacja tej metody powinna, najlepiej, zakończyć program w ramach procesu. Jeśli nie jest to możliwe, DE powinien uniemożliwić programowi uruchomienie więcej w tym procesie (i zrobić wszelkie niezbędne oczyszczanie). Jeśli `IDebugProcess2::Terminate` metoda została wywołana przez IDE, cały proces zostanie `IDebugProgram2::Terminate` zakończony po wywołaniu metody.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
