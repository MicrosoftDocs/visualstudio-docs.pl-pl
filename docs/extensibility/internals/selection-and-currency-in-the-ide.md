---
title: Wybór i waluta w środowisku IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edff400420ca5f0c93e1df85fb9118eee6302d02
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723962"
---
# <a name="selection-and-currency-in-the-ide"></a>Wybór i aktualność w środowisku IDE
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) zachowuje informacje o aktualnie wybranych obiektach użytkowników przy użyciu *kontekstu*wyboru. W przypadku kontekstu wyboru pakietów VSPackage może wziąć udział w śledzeniu walut na dwa sposoby:

- Propagowanie informacji o walucie pakietów VSPackage do IDE.

- Monitorując aktualnie aktywne wybory użytkowników w środowisku IDE.

## <a name="selection-context"></a>Kontekst zaznaczenia
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE globalnie śledzi walutę IDE w swoim własnym globalnym obiekcie kontekstu wyboru. W poniższej tabeli przedstawiono elementy wchodzące w skład kontekstu wyboru.

|Element|Opis|
|-------------|-----------------|
|Bieżąca hierarchia|Zwykle bieżący projekt; Bieżąca hierarchia o wartości NULL wskazuje, że rozwiązanie jako całość jest aktualne.|
|Bieżący identyfikator elementu|Wybrany element w bieżącej hierarchii; Jeśli w oknie projektu istnieje wiele opcji, może istnieć wiele bieżących elementów.|
|Bieżąca `SelectionContainer`|Zawiera jeden lub więcej obiektów, dla których okno Właściwości powinny wyświetlać właściwości.|

 Ponadto środowisko utrzymuje dwie listy globalne:

- Lista identyfikatorów poleceń interfejsu użytkownika

- Lista obecnie aktywnych typów elementów.

### <a name="window-types-and-selection"></a>Typy okien i wybór
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organizuje system Windows w postaci dwóch typów ogólnych:

- Hierarchia typu w systemie Windows

- Okna ramowe, takie jak okna narzędzi i dokumentów

  IDE śledzi walutę inaczej dla każdego z tych typów okien.

  Najbardziej typowym oknem typu projektu jest Eksplorator rozwiązań, który kontroluje IDE. Okno typu projektu śledzi hierarchię globalną oraz identyfikator elementu globalnego kontekstu wyboru, a okno opiera się na wyborze użytkownika w celu określenia bieżącej hierarchii. W przypadku okien typu projektowego środowisko zapewnia globalną <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>usługi, za pomocą którego pakietów VSPackage może monitorować bieżące wartości dla otwartych elementów. Przeglądanie właściwości w środowisku jest sterowane przez tę usługę globalną.

  Okna ramowe, z drugiej strony, użyj DocObject w oknie ramki, aby wypchnąć wartość kontekst wyboru (Hierarchy/ItemID/SelectionContainer trójka). . W tym celu okna ramowe używają <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi. DocObject może wypchnąć tylko wartości dla kontenera wyboru, pozostawiając wartości lokalne dla hierarchii i identyfikatora elementu, jak zwykle w przypadku dokumentów podrzędnych MDI.

### <a name="events-and-currency"></a>Zdarzenia i waluta
 Mogą wystąpić dwa typy zdarzeń, które wpływają na pojęcie walutowe środowiska:

- Zdarzenia, które są propagowane do poziomu globalnego i zmieniają kontekst zaznaczenia ramki okna. Przykłady tego rodzaju zdarzenia obejmują otwierające się okno podrzędne MDI, otwiera okno narzędzia globalnego lub otwiera okno narzędzia typu projektu.

- Zdarzenia, które zmieniają elementy śledzone w kontekście wyboru ramki okna. Przykłady obejmują zmianę wyboru w DocObject lub zmianę zaznaczenia w oknie Typ projektu.

## <a name="see-also"></a>Zobacz także
- [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)
- [Opinia dla użytkownika](../../extensibility/internals/feedback-to-the-user.md)