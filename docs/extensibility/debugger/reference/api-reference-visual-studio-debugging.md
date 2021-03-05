---
description: Sekcja Reference zawiera omówienie pojęć dotyczących interfejsu API, przewodnik, który pokazuje składnię i użycie dla wszystkich elementów interfejsu API oraz asortyment przykładów kodu.
title: Dokumentacja interfejsu API (debugowanie programu Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 47c6697945c6c588a8b4e57ab03d573d45c4d4cf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144640"
---
# <a name="api-reference-visual-studio-debugging"></a>Dokumentacja interfejsu API (Debugowanie w programie Visual Studio)
Sekcja Reference zawiera omówienie pojęć dotyczących interfejsu API, przewodnik, który pokazuje składnię i użycie dla wszystkich elementów interfejsu API oraz asortyment przykładów kodu. Wszystkie odwołania są wyświetlane alfabetycznie według kategorii.

 W poniższej tabeli przedstawiono typowe `HRESULT` wartości zwracane przez metody.

|Nazwa|Opis|Wartość|
|----------|-----------------|-----------|
|S_OK|Powodzenie.|0x00000000|
|E_UNEXPECTED|Nieoczekiwany błąd.|0x8000FFFF|
|E_NOTIMPL|Nie zaimplementowano.|0x80004001|
|E_OUTOFMEMORY|Za mało pamięci, aby ukończyć operację.|0x8007000E|
|E_INVALIDARG|Co najmniej jeden argument jest nieprawidłowy.|0x80070057|
|E_NOINTERFACE|Taki interfejs nie jest obsługiwany.|0x80004002|
|E_POINTER|Nieprawidłowy wskaźnik.|0x80004003|
|E_HANDLE|Nieprawidłowe dojście.|0x80070006|
|E_ABORT|Operacja została przerwana.|0x80004004|
|E_FAIL|Nieoczekiwany błąd.|0x80004005|
|E_ACCESSDENIED|Ogólny błąd odmowy dostępu.|0x80070005|

> [!NOTE]
> Gdy [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Metoda debugowania zwraca `S_OK` , zakłada się, że wszystkie wskaźniki parametru out są prawidłowe, co oznacza, żadna Walidacja nie jest przeprowadzana na wskaźnikach parametrów out, gdy `S_OK` jest zwracany.
>
> [!NOTE]
> Parametry nieprawidłowe lub `NULL` [out] mogą spowodować awarię środowiska IDE.

## <a name="see-also"></a>Zobacz też
- [Interfejsy](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
