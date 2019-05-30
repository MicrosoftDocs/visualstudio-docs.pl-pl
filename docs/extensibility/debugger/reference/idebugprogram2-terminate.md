---
title: IDebugProgram2::Terminate | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16a6d60173090642bda7d8fd940ecf0699e1d7ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331498"
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
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli to możliwe program zostanie zakończony i zwolnione z procesu; w przeciwnym razie aparat debugowania (DE) będzie wykonać wszelkie niezbędne czyszczenia.

 Ta metoda lub [Zakończ](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) metoda jest wywoływana przez środowisko IDE, zwykle w odpowiedzi na użytkownika zatrzymywanie debugowania wszystkie. Implementacja tej metody w idealnym przypadku należy zakończyć program w ramach procesu. Jeśli nie jest to możliwe, DE powinien uniemożliwienie program dalszych w ramach tego procesu (i wykonaj wszelkie niezbędne czyszczenia). Jeśli `IDebugProcess2::Terminate` wywołano metodę IDE, cały proces zostanie zakończony jakiś czas po `IDebugProgram2::Terminate` metoda jest wywoływana.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)