---
title: IDebugStackFrame3::InterceptCurrentException | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719479"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Wywoływane przez debugera w bieżącej ramce stosu, gdy chce przechwycić bieżący wyjątek.

## <a name="syntax"></a>Składnia

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Parametry
`dwFlags`\
[w] Określa różne akcje. Obecnie obsługiwana [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) jest tylko wartość `IEA_INTERCEPT` INTERCEPT_EXCEPTION_ACTION i musi być określona.

`pqwCookie`\
[na zewnątrz] Unikatowa wartość identyfikujący określony wyjątek.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

 Poniżej przedstawiono najczęstsze zwraca błąd.

|Błąd|Opis|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Bieżący wyjątek nie może zostać przechwycony.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Bieżąca ramka wykonywania nie została jeszcze przeszukana w poszukiwaniu programu obsługi.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Ta metoda nie jest obsługiwana dla tej ramki.|

## <a name="remarks"></a>Uwagi
 Gdy wyjątek, debuger zyskuje kontrolę od czasu wykonywania w kluczowych punktach podczas procesu obsługi wyjątków. Podczas tych kluczowych momentów debuger może zapytać bieżącą ramkę stosu, jeśli ramka chce przechwycić wyjątek. W ten sposób przechwycony wyjątek jest zasadniczo w locie obsługi wyjątków dla ramki stosu, nawet jeśli ramka stosu nie ma obsługi wyjątków (na przykład try/catch bloku w kodzie programu).

 Gdy debuger chce wiedzieć, czy wyjątek powinien zostać przechwycony, wywołuje tę metodę na bieżącym obiekcie ramki stosu. Ta metoda jest odpowiedzialna za obsługę wszystkich szczegółów wyjątku. Jeśli interfejs [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) nie jest `InterceptStackException` zaimplementowany lub metoda zwraca dowolny błąd, debuger kontynuuje przetwarzanie wyjątku normalnie.

> [!NOTE]
> Wyjątki mogą być przechwytywane tylko w kodzie zarządzanym, czyli gdy program debugowany jest uruchomiony w czasie wykonywania .NET. Oczywiście realizatorzy języków innych firm `InterceptStackException` mogą implementować we własnych aparatach debugowania, jeśli tak zdecydują.

 Po zakończeniu przechwytywania [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) jest sygnalizowany.

## <a name="see-also"></a>Zobacz też
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
