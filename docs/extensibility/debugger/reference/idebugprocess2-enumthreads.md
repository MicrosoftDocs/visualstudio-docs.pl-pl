---
title: IDebugProcess2::WyliczeniaWy | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52383649fc45eae6bbac6831f9bb233b9c0a2fde
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724068"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Pobiera listę wszystkich wątków uruchomionych w procesie.

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
[na zewnątrz] Zwraca obiekt [IEnumDebugThreads2,](../../../extensibility/debugger/reference/ienumdebugthreads2.md) który zawiera listę wszystkich wątków we wszystkich programach w procesie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda wylicza wątki uruchomione w każdym programie, a następnie łączy je w widok procesu wątków. Pojedynczy wątek może działać w wielu programach; ta metoda wylicza ten wątek tylko raz.

 Ta metoda przedstawia listę wątków procesu bez duplikatów. W przeciwnym razie, aby wyliczyć wątki uruchomione w określonym programie, należy użyć [Metody Wyliczenia.](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)

## <a name="see-also"></a>Zobacz też
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
