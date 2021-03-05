---
description: 'IDebugProgram2:: Execute kontynuuje działanie tego programu ze stanu zatrzymanego. Wszystkie poprzednie Stany wykonania (takie jak krok) są wyczyszczone, a program ponownie uruchamia wykonywanie.'
title: 'IDebugProgram2:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72b59066e8b7125216077dbf4f6ed83adfa0ad2c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146044"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Kontynuuje działanie tego programu ze stanu zatrzymanego. Wszystkie poprzednie Stany wykonania (takie jak krok) są wyczyszczone, a program ponownie uruchamia wykonywanie.

> [!NOTE]
> Ta metoda jest przestarzała. Zamiast tego użyj metody [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) .

## <a name="syntax"></a>Składnia

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy użytkownik uruchamia wykonywanie z stanu zatrzymanego w innym wątku programu, ta metoda jest wywoływana w tym programie. Ta metoda jest również wywoływana, gdy użytkownik wybierze polecenie **Uruchom** z menu **DEBUGUJ** w środowisku IDE. Implementacja tej metody może być prosta jako wywołanie metody [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) w bieżącym wątku w programie.

> [!WARNING]
> Nie wysyłaj zdarzenia zatrzymania ani bezpośredniego (synchronicznego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może przestać odpowiadać.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Wznawianie](../../../extensibility/debugger/reference/idebugthread2-resume.md)
