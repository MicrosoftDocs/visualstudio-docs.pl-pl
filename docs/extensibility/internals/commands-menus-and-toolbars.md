---
title: Polecenia, menu i paski narzędzi | Microsoft Docs
description: Uzyskaj informacje na temat poleceń, menu i pasków narzędzi w programie Visual Studio, w tym ich elementów i sposobu ich działania w pakietów VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2a1b4cdb95fa5b053bc75efb559ea77b84ae56dd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057159"
---
# <a name="commands-menus-and-toolbars"></a>Polecenia, menu i paski narzędzi
Menu i paski narzędzi to sposób, w jaki użytkownicy uzyskują dostęp do poleceń w pakietu VSPackage. Polecenia to funkcje wykonujące zadania, takie jak drukowanie dokumentu, odświeżanie widoku lub tworzenie nowego pliku. Menu i paski narzędzi są wygodnym sposobem na prezentowanie poleceń użytkownikom. Zazwyczaj powiązane polecenia są klastrowane w tym samym menu lub pasku narzędzi.

- Menu są zwykle wyświetlane jako ciągi jednowyrazowe klastrowane w wierszu w górnej części zintegrowanego środowiska programistycznego (IDE) lub okna narzędzi. Menu można także wyświetlać jako wynik zdarzenia prawym przyciskiem myszy i są nazywane menu skrótów w tym kontekście. Po kliknięciu menu rozwijane, aby wyświetlić jedno lub więcej poleceń. Polecenia po kliknięciu mogą wykonywać zadania i uruchamiać podmenu zawierające dodatkowe polecenia. Niektóre dobrze znane nazwy menu to **plik**, **Edycja**, **Widok** i **okno**. Aby uzyskać więcej informacji, zobacz sekcję [poszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

- Paski narzędzi zwykle są wierszami przycisków i innych kontrolek, takimi jak pola kombi, pola listy, pola tekstowe i kontrolery menu. Wszystkie kontrolki paska narzędzi są skojarzone z poleceniami. Po kliknięciu przycisku paska narzędzi jego skojarzone polecenie jest uaktywniane. Przyciski paska narzędzi mają zwykle ikony sugerujące podstawowe polecenia, takie jak drukarka dla polecenia Print. W kontrolce listy rozwijanej każdy element na liście jest skojarzony z innym poleceniem. Kontroler menu jest hybrydowy, w którym jedna strona kontrolki jest przyciskiem paska narzędzi, a druga strona jest strzałką w dół, która wyświetla dodatkowe polecenia po kliknięciu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolera menu do paska narzędzi](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Podczas tworzenia polecenia należy również utworzyć procedurę obsługi zdarzeń. Program obsługi zdarzeń określa, kiedy polecenie jest widoczne lub włączone, umożliwia zmodyfikowanie tekstu i gwarantuje, że polecenie będzie odpowiadać odpowiednio ("trasy") po aktywowaniu. W większości wystąpień IDE obsługuje polecenia przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Polecenia w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] trasie w sposób hierarchiczny, zaczynając od wewnętrznego kontekstu poleceń, na podstawie wyboru lokalnego i przechodząc do zewnętrznego kontekstu, oparte na globalnym wyborze. Polecenia dodane do menu głównego są natychmiast dostępne dla skryptów. Aby uzyskać więcej informacji, zobacz [MenuCommands a OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015) i [obiekty kontekstu wyboru](../../extensibility/internals/selection-context-objects.md).

  Aby zdefiniować nowe menu i paski narzędzi, należy je opisać w pliku tabeli poleceń programu Visual Studio (*. vsct*). Szablon pakietu programu Visual Studio tworzy ten plik wraz z niezbędnymi elementami do obsługi poleceń, pasków narzędzi i edytorów wybranych w szablonie. Alternatywnie można napisać własny plik *. vsct* , używając schematu XML opisanego tutaj: [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).

  Aby uzyskać więcej informacji na temat pracy z plikami *. vsct* , zobacz [pliki programu Visual Studio Command Table (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

  W tematach w tej sekcji wyjaśniono, jak polecenia, menu i paski narzędzi działają w pakietów VSPackage.

## <a name="in-this-section"></a>W tej sekcji
- [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Szczegółowy opis specyfikacji formatu tabeli poleceń.

- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Opisuje składnię i kompilator oparty na języku XML dla tabel poleceń.

- [Domyślne położenie poleceń, grup i pasków narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Opisuje wstępnie zdefiniowane polecenia, grupy, menu i paski narzędzi.

- [Polecenia, menu i grupy zdefiniowane w środowisku IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Określa wstępnie zdefiniowane menu, polecenia i grupy poleceń dostępne do użycia przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Projekt polecenia](../../extensibility/internals/command-design.md)

 Wyjaśnia, jak projektować polecenia.

- [Optymalizowanie poleceń menu i pasków narzędzi](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Zapewnia wytyczne dla poleceń.

- [Udostępnianie poleceń](../../extensibility/internals/making-commands-available.md)

 Wyjaśnia, jak udostępnić polecenia dla programu Visual Studio.

- [Polecenia i menu używające zestawów międzyoperacyjnych](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Wyjaśnia, jak zaimplementować polecenia korzystające z zestawów międzyoperacyjnych.

## <a name="related-sections"></a>Sekcje pokrewne
- [Routing poleceń w pakietów VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)

 Wyjaśnia routing poleceń w pakietów VSPackage.