---
title: Odwołanie do interfejsu API (debugowanie programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a2df6d82099a927664620e19096107f283afada
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738178"
---
# <a name="api-reference-visual-studio-debugging"></a>Dokumentacja interfejsu API (Debugowanie w programie Visual Studio)
Sekcja odwołania zawiera omówienie koncepcyjne interfejsu API, przewodnik, który pokazuje składnię i użycie dla wszystkich elementów interfejsu API oraz asortyment przykładów kodu. Wszystkie odwołania są wyświetlane alfabetycznie według kategorii.

 W poniższej tabeli przedstawiono wspólne `HRESULT` wartości zwracane metodami.

|Nazwa|Opis|Wartość|
|----------|-----------------|-----------|
|S_OK|Powodzenie.|0x00000000|
|E_unexpected|Nieoczekiwany błąd.|0x8000FFFF|
|E_notimpl|Nie zaimplementowano.|0x80004001|
|E_outofmemory|Za mało pamięci, aby zakończyć operację.|0x8007000E|
|E_invalidarg|Jeden lub więcej argumentów jest nieprawidłowych.|0x80070057|
|E_nointerface|Nie obsługiwany jest taki interfejs.|0x80004002|
|E_pointer|Nieprawidłowy wskaźnik.|0x80004003|
|E_HANDLE|Nieprawidłowy dojście.|0x80070006|
|E_ABORT|Operacja została przerwana.|0x80004004|
|E_fail|Nieoczekiwany błąd.|0x80004005|
|E_ACCESSDENIED|Błąd odmowy dostępu ogólnego.|0x80070005|

> [!NOTE]
> Gdy [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] metoda debugowania `S_OK`zwraca , zakłada się, że wszystkie wskaźniki out parametr są prawidłowe, oznacza `S_OK` to, że nie sprawdzanie poprawności jest przeprowadzane na out wskaźników parametrów po powrocie.
>
> [!NOTE]
> Nieprawidłowe `NULL` lub [out] parametry mogą spowodować awarię IDE.

## <a name="see-also"></a>Zobacz też
- [Interfejsy](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
