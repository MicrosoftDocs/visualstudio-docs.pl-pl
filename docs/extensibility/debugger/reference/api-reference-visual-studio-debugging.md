---
title: Dokumentacja interfejsu API (debugowanie w programie Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d415644897d7dd481f47c93a3b951db23fda843
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686356"
---
# <a name="api-reference-visual-studio-debugging"></a>Dokumentacja interfejsu API (Debugowanie w programie Visual Studio)
Ta część zawiera omówienie interfejsu API, przewodnik, który pokazuje składni i użycia dla wszystkich elementów interfejsu API i gamę przykłady kodu. Wszystkie odwołania są wymieniane alfabetycznie według kategorii.

 W poniższej tabeli przedstawiono typowe `HRESULT` wartości zwracane przez metody.

|Nazwa|Opis|Wartość|
|----------|-----------------|-----------|
|S_OK|Powodzenie.|0x00000000|
|E_UNEXPECTED|Nieoczekiwany błąd.|0x8000FFFF|
|E_NOTIMPL|Nie zaimplementowano.|0x80004001|
|E_OUTOFMEMORY|Nie ma wystarczającej ilości pamięci do ukończenia tej operacji.|0x8007000E|
|E_INVALIDARG|Jeden lub więcej argumentów są nieprawidłowe.|0x80070057|
|E_NOINTERFACE|Taki interfejs nie jest obsługiwane.|0x80004002|
|E_POINTER|Nieprawidłowy wskaźnik.|0x80004003|
|E_HANDLE|Nieprawidłowe dojście.|0x80070006|
|E_ABORT|Operacja została przerwana.|0x80004004|
|E_FAIL|Nieoczekiwany błąd.|0x80004005|
|E_ACCESSDENIED|Ogólny błąd odmowy dostępu.|0x80070005|

> [!NOTE]
>  Gdy [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugowania metoda zwraca `S_OK`, zakłada się, że wszystkie out parametru wskaźniki są prawidłowe, oznacza to, że nie nastąpi sprawdzanie poprawności jest przeprowadzane na się wskaźniki parametru podczas `S_OK` jest zwracana.
>
> [!NOTE]
>  Nieprawidłowy lub `NULL` [parametry out] może spowodować, że środowisko IDE ulega awarii.

## <a name="see-also"></a>Zobacz też
- [Interfejsy](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)