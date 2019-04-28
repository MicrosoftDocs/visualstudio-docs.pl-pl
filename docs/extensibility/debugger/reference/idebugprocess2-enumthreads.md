---
title: IDebugProcess2::EnumThreads | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1ca619fe00ca29fb8788a450fab1ec5237be984
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870917"
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

#### <a name="parameters"></a>Parametry
 `ppEnum`

 [out] Zwraca [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) obiektu, który zawiera listę wszystkich wątków we wszystkich programach w procesie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda wylicza wątki uruchomione w każdym programie i łączy je w widoku proces wątków. Pojedynczy wątek może działać w wielu programach; Ta metoda wylicza wątek tylko raz.

 Ta metoda Wyświetla listę wątków procesu bez duplikatów. W przeciwnym razie można wyliczyć wątki uruchomione w szczególności program, należy użyć [enumthreads —](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)