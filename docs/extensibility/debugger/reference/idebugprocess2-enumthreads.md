---
title: IDebugProcess2::EnumThreads | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 664f4264fd12106fef0650a31a888470e09a3154
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353168"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Pobiera listę wszystkich wątków, uruchomiony w procesie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[out] Zwraca [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) obiektu, który zawiera listę wszystkich wątków we wszystkich programach w procesie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda wylicza wątki uruchomione w każdym programie i łączy je w widoku proces wątków. Pojedynczy wątek może działać w wielu programach; Ta metoda wylicza wątek tylko raz.

 Ta metoda Wyświetla listę wątków procesu bez duplikatów. W przeciwnym razie można wyliczyć wątki uruchomione w szczególności program, należy użyć [enumthreads —](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)