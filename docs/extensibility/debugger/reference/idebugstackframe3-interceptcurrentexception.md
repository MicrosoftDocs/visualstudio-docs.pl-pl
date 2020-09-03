---
title: 'IDebugStackFrame3:: InterceptCurrentException — | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719479"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Wywoływane przez debuger w bieżącej klatce stosu, gdy chce przechwycić bieżący wyjątek.

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
podczas Określa różne akcje. Obecnie tylko [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) wartość `IEA_INTERCEPT` jest obsługiwana i musi być określona.

`pqwCookie`\
określoną Unikatowa wartość identyfikująca konkretny wyjątek.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

 Poniżej przedstawiono najbardziej typowe błędy.

|Błąd|Opis|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Nie można przechwycić bieżącego wyjątku.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Bieżąca ramka wykonawcza nie wyszukano jeszcze procedury obsługi.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Ta metoda nie jest obsługiwana dla tej ramki.|

## <a name="remarks"></a>Uwagi
 Gdy wyjątek jest zgłaszany, debuger uzyskuje kontrolę nad czasem wykonywania w kluczowych punktach podczas procesu obsługi wyjątków. W tym kluczu debuger może poprosił o bieżącą ramkę stosu, jeśli ramka przechwytuje wyjątek. W ten sposób przechwycony wyjątek jest zasadniczo obsługiwanym przez program obsługi wyjątków dla ramki stosu, nawet jeśli ta ramka stosu nie ma procedury obsługi wyjątków (na przykład blok try/catch w kodzie programu).

 Gdy debuger chce dowiedzieć się, czy wyjątek powinien być przechwytywany, wywołuje tę metodę na bieżącym obiekcie ramki stosu. Ta metoda jest odpowiedzialna za obsługę wszystkich szczegółów wyjątku. Jeśli interfejs [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) nie jest zaimplementowany lub `InterceptStackException` Metoda zwraca jakikolwiek błąd, debuger kontynuuje przetwarzanie wyjątku w normalny sposób.

> [!NOTE]
> Wyjątki mogą być przechwytywane tylko w kodzie zarządzanym, czyli gdy debugowany program jest uruchomiony w czasie wykonywania programu .NET. Oczywiście implementacje języka innych firm mogą zostać wdrożone `InterceptStackException` we własnych aparatach debugowania, jeśli tak się stanie.

 Po zakończeniu przechwycenia jest sygnalizowane [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
