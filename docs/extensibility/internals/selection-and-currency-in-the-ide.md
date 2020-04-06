---
title: Wybór i waluta w IDE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f580b7c8e1651dcbcd053476ae756399a0ac3482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705570"
---
# <a name="selection-and-currency-in-the-ide"></a>Wybór i aktualność w środowisku IDE
Zintegrowane [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko programistyczne (IDE) przechowuje informacje o aktualnie zaznaczonych obiektach użytkowników przy użyciu *kontekstu*zaznaczenia. W kontekście wyboru VSPackages może brać udział w śledzeniu waluty na dwa sposoby:

- Propagując informacje walutowe o VSPackages do IDE.

- Poprzez monitorowanie aktualnie aktywnych wyborów użytkowników w ramach IDE.

## <a name="selection-context"></a>Kontekst wyboru
 IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] globalnie śledzi waluty IDE w swoim własnym obiekcie kontekstu zaznaczenia globalnego. W poniższej tabeli przedstawiono elementy, które składają się na kontekst wyboru.

|Element|Opis|
|-------------|-----------------|
|Bieżąca hierarchia|Zazwyczaj bieżący projekt; A NULL bieżącej hierarchii wskazuje, że rozwiązanie jako całość jest aktualne.|
|Bieżący identyfikator pozycji|Wybrany element w bieżącej hierarchii; gdy w oknie projektu znajduje się wiele opcji, może istnieć wiele bieżących elementów.|
|Bieżącego`SelectionContainer`|Przechowuje jeden lub więcej obiektów, dla których właściwości okna powinny być wyświetlane właściwości.|

 Ponadto środowisko utrzymuje dwie listy globalne:

- Lista aktywnych identyfikatorów poleceń interfejsu użytkownika

- Lista aktualnie aktywnych typów elementów.

### <a name="window-types-and-selection"></a>Typy okien i zaznaczenie
 IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] organizuje okna na dwa typy ogólne:

- Okna typu hierarchia

- Okna ramek, takie jak okna narzędzi i dokumentów

  IDE śledzi walutę inaczej dla każdego z tych typów okien.

  Najbardziej typowe okno typu projektu jest eksplorator rozwiązania, który kontroluje IDE. Okno typu projektu śledzi globalną hierarchię i ItemID kontekstu zaznaczenia globalnego, a okno opiera się na wyborze użytkownika w celu określenia bieżącej hierarchii. W przypadku okien typu projektu środowisko <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>udostępnia usługę globalną, za pośrednictwem której vspackages mogą monitorować bieżące wartości dla otwartych elementów. Przeglądanie właściwości w środowisku jest napędzany przez tę usługę globalną.

  Okna ramki, z drugiej strony, użyj DocObject w oknie ramki, aby wypchnąć SelectionContext wartość (hierarchia/ItemID/SelectionContainer trio). . Okna ramki <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> korzystają z usługi w tym celu. DocObject można wypychać tylko wartości dla kontenera zaznaczenia, pozostawiając wartości lokalne dla hierarchii i ItemID bez zmian, jak to jest typowe dla dokumentów podrzędnych MDI.

### <a name="events-and-currency"></a>Wydarzenia i waluta
 Mogą wystąpić dwa typy zdarzeń, które wpływają na środowisko pojęcie waluty:

- Zdarzenia, które są propagowane na poziomie globalnym i zmieniają kontekst wyboru ramki okna. Przykłady tego typu zdarzenia obejmują otwierane okno podrzędne MDI, otwierane globalne okno narzędzia lub otwierane okno narzędzia typu projektu.

- Zdarzenia, które zmieniają elementy śledzone w kontekście zaznaczenia ramki okna. Przykłady obejmują zmianę zaznaczenia w docObject lub zmiana zaznaczenia w oknie typu projektu.

## <a name="see-also"></a>Zobacz też
- [Obiekty kontekstu wyboru](../../extensibility/internals/selection-context-objects.md)
- [Opinia dla użytkownika](../../extensibility/internals/feedback-to-the-user.md)
