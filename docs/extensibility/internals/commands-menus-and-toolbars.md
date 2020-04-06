---
title: Polecenia, menu i paski narzędzi | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2be2f719d0f123328d5c518c08e30df2185e2a19
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709504"
---
# <a name="commands-menus-and-toolbars"></a>Polecenia, menu i paski narzędzi
Menu i paski narzędzi są sposób, w jaki użytkownicy uzyskują dostęp do poleceń w programie VSPackage. Polecenia to funkcje, które realizują zadania, takie jak drukowanie dokumentu, odświeżanie widoku lub tworzenie nowego pliku. Menu i paski narzędzi są wygodnymi graficznymi sposobami prezentowania poleceń użytkownikom. Zazwyczaj powiązane polecenia są grupowane razem w tym samym menu lub na pasku narzędzi.

- Menu są zazwyczaj wyświetlane jako jednowyrazowe ciągi klastrowane w wierszu u góry zintegrowanego środowiska programistycznego (IDE) lub okna narzędzia. Menu mogą być również wyświetlane w wyniku zdarzenia kliknięcia prawym przyciskiem myszy i są określane jako menu skrótów w tym kontekście. Po kliknięciu menu rozwiń, aby wyświetlić jedno lub więcej poleceń. Polecenia, po kliknięciu, można wykonywać zadania lub uruchomić podmenu, które zawierają dodatkowe polecenia. Niektóre dobrze znane nazwy menu **to Plik,** **Edycja,** **Widok**i **Okno**. Aby uzyskać więcej informacji, zobacz [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

- Paski narzędzi są zazwyczaj wierszami przycisków i innych formantów, takich jak pola kombi, pola listy, pola tekstowe i kontrolery menu. Wszystkie kontrolki paska narzędzi są skojarzone z poleceniami. Po kliknięciu przycisku paska narzędzi aktywowane jest skojarzone z nim polecenie. Przyciski paska narzędzi zwykle mają ikony sugerujące podstawowe polecenia, takie jak drukarka polecenia Drukuj. W formancie listy rozwijanej każdy element na liście jest skojarzony z innym poleceniem. Kontroler menu jest hybrydą, w której jedna strona formantu jest przyciskiem paska narzędzi, a druga jest strzałką w dół, która wyświetla dodatkowe polecenia po kliknięciu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolera menu do paska narzędzi](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Podczas tworzenia polecenia, należy również utworzyć program obsługi zdarzeń dla niego. Program obsługi zdarzeń określa, kiedy polecenie jest widoczne lub włączone, umożliwia modyfikowanie jego tekstu i zapewnia, że polecenie reaguje odpowiednio ("trasy") po aktywacji. W większości przypadków IDE obsługuje polecenia za <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pomocą interfejsu. Polecenia w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] trasie w sposób hierarchiczny, począwszy od najbardziej wewnętrznego kontekstu polecenia, na podstawie zaznaczenia lokalnego i przechodząc do kontekstu zewnętrznego, na podstawie zaznaczenia globalnego. Polecenia dodane do menu głównego są natychmiast dostępne do skryptów. Aby uzyskać więcej informacji, zobacz [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015) i [Obiekty kontekstu zaznaczenia](../../extensibility/internals/selection-context-objects.md).

  Aby zdefiniować nowe menu i paski narzędzi, należy opisać je w pliku polecenia programu Visual Studio (*.vsct*). Szablon pakietu programu Visual Studio tworzy ten plik dla Ciebie, wraz z elementów niezbędnych do obsługi niezależnie od poleceń, pasków narzędzi i edytorów, które zostały wybrane w szablonie. Alternatywnie można napisać własny plik *vsct,* używając schematu XML opisanego tutaj: [odwołanie do schematu VSCT XML](../../extensibility/vsct-xml-schema-reference.md).

  Aby uzyskać więcej informacji na temat pracy z *plikami vsct,* zobacz [Pliki tabeli poleceń programu Visual Studio (vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

  Tematy w tej sekcji wyjaśniają, jak działają polecenia, menu i paski narzędzi w programie VSPackages.

## <a name="in-this-section"></a>W tej sekcji
- [Jak vspackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Szczegółowy opis specyfikacji formatu tabeli poleceń.

- [Pliki tabeli poleceń programu Visual Studio (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Opisuje składnię opartą na języku XML i kompilator dla tabel poleceń.

- [Domyślne rozmieszczenie polecenia, grupy i paska narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Opisuje wstępnie zdefiniowane polecenia, grupy, menu i paski narzędzi.

- [Polecenia, menu i grupy zdefiniowane przez IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Określa wstępnie zdefiniowane menu, polecenia i grupy poleceń dostępne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do użycia przez IDE.

- [Projekt polecenia](../../extensibility/internals/command-design.md)

 W tym artykule wyjaśniono, jak projektować polecenia.

- [Optymalizuj polecenia menu i paska narzędzi](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Zawiera wskazówki dotyczące poleceń.

- [Udostępnianie poleceń](../../extensibility/internals/making-commands-available.md)

 W tym artykule wyjaśniono, jak udostępnić polecenia programowi Visual Studio.

- [Polecenia i menu, które używają zestawów międzyoperacyjnych](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Wyjaśniono, jak zaimplementować polecenia, które używają zestawów interop.

## <a name="related-sections"></a>Powiązane sekcje
- [Routing poleceń w pakietach VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 W tym artykule wyjaśniono routing poleceń w programie VSPackages.
