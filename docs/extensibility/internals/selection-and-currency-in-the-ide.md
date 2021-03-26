---
title: Wybór i waluta w środowisku IDE | Microsoft Docs
description: Dowiedz się, jak pakietów VSPackage wziąć udział w śledzeniu walut. Środowisko IDE programu Visual Studio zachowuje informacje o aktualnie wybranych obiektach przy użyciu kontekstu wyboru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0fb65a63b99f625f8d32af8436db753a0f17322e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080908"
---
# <a name="selection-and-currency-in-the-ide"></a>Wybór i aktualność w środowisku IDE
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Zintegrowane środowisko programistyczne (IDE) obsługuje informacje o aktualnie wybranych obiektach użytkowników przy użyciu *kontekstu* wyboru. W przypadku kontekstu wyboru pakietów VSPackage może wziąć udział w śledzeniu walut na dwa sposoby:

- Propagowanie informacji o walucie pakietów VSPackage do IDE.

- Monitorując aktualnie aktywne wybory użytkowników w środowisku IDE.

## <a name="selection-context"></a>Kontekst zaznaczenia
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE globalnie śledzi walutę IDE w swoim własnym globalnym obiekcie kontekstu wyboru. W poniższej tabeli przedstawiono elementy wchodzące w skład kontekstu wyboru.

|Element|Opis|
|-------------|-----------------|
|Bieżąca hierarchia|Zwykle bieżący projekt; Bieżąca hierarchia o wartości NULL wskazuje, że rozwiązanie jako całość jest aktualne.|
|Bieżący identyfikator elementu|Wybrany element w bieżącej hierarchii; Jeśli w oknie projektu istnieje wiele opcji, może istnieć wiele bieżących elementów.|
|Obecne `SelectionContainer`|Zawiera jeden lub więcej obiektów, dla których okno Właściwości powinny wyświetlać właściwości.|

 Ponadto środowisko utrzymuje dwie listy globalne:

- Lista identyfikatorów poleceń interfejsu użytkownika

- Lista obecnie aktywnych typów elementów.

### <a name="window-types-and-selection"></a>Typy okien i wybór
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE organizuje system Windows w postaci dwóch typów ogólnych:

- Hierarchia typu w systemie Windows

- Okna ramowe, takie jak okna narzędzi i dokumentów

  IDE śledzi walutę inaczej dla każdego z tych typów okien.

  Najbardziej typowym oknem typu projektu jest Eksplorator rozwiązań, który kontroluje IDE. Okno typu projektu śledzi hierarchię globalną oraz identyfikator elementu globalnego kontekstu wyboru, a okno opiera się na wyborze użytkownika w celu określenia bieżącej hierarchii. W przypadku okien typu projektowego środowisko zapewnia globalną usługę <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> , za pomocą której pakietów VSPackage może monitorować bieżące wartości dla otwartych elementów. Przeglądanie właściwości w środowisku jest sterowane przez tę usługę globalną.

  Okna ramowe, z drugiej strony, użyj DocObject w oknie ramki, aby wypchnąć wartość kontekst wyboru (Hierarchy/ItemID/SelectionContainer trójka). . Okna ramowe używają usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> do tego celu. DocObject może wypchnąć tylko wartości dla kontenera wyboru, pozostawiając wartości lokalne dla hierarchii i identyfikatora elementu, jak zwykle w przypadku dokumentów podrzędnych MDI.

### <a name="events-and-currency"></a>Zdarzenia i waluta
 Mogą wystąpić dwa typy zdarzeń, które wpływają na pojęcie walutowe środowiska:

- Zdarzenia, które są propagowane do poziomu globalnego i zmieniają kontekst zaznaczenia ramki okna. Przykłady tego rodzaju zdarzenia obejmują otwierające się okno podrzędne MDI, otwiera okno narzędzia globalnego lub otwiera okno narzędzia typu projektu.

- Zdarzenia, które zmieniają elementy śledzone w kontekście wyboru ramki okna. Przykłady obejmują zmianę wyboru w DocObject lub zmianę zaznaczenia w oknie Typ projektu.

## <a name="see-also"></a>Zobacz też
- [Obiekty kontekstu wyboru](../../extensibility/internals/selection-context-objects.md)
- [Opinia dla użytkownika](../../extensibility/internals/feedback-to-the-user.md)
