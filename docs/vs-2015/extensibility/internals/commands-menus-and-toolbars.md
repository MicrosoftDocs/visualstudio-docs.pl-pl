---
title: Polecenia, menu i paski narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 61
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 337bc4de9171d2f98bf0be0068b298b7f600b979
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779819"
---
# <a name="commands-menus-and-toolbars"></a>Polecenia, menu i paski narzędzi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Menu i paski narzędzi są użytkownicy sposób uzyskiwać dostęp do poleceń Twoje pakietu VSPackage. Polecenia są funkcje, które wykonywania zadań, takich jak drukowanie dokumentu, odświeżyć widok lub tworzenia nowego pliku. Menu i pasków zadań to wygodny graficzny sposoby przedstawiania poleceń dla użytkowników. Zazwyczaj powiązane polecenia są zgrupowane razem na tym samym menu lub paska narzędzi.  
  
- Menu zwykle są wyświetlane jako ciągi jednowyrazową klastrowane w wierszu w górnej części zintegrowanego środowiska programistycznego (IDE) lub okna narzędzi. Menu również mogą być wyświetlane jako wynik zdarzenia, kliknij prawym przyciskiem myszy i są określane jako menu skrótów w tym kontekście. Po kliknięciu menu rozwinąć w celu wyświetlenia co najmniej jedno polecenie. Polecenia, po kliknięciu, można wykonywać zadania lub uruchom podmenu zawierające dodatkowe polecenia. Niektóre nazwy menu dobrze znane są plik, Edytuj, widok i okna. Aby uzyskać więcej informacji, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).  
  
- Paski narzędzi są zazwyczaj wiersze przyciski i inne formanty, takie jak pola kombi, pola listy, pola tekstowe i kontrolery menu. Wszystkie kontrolki paska narzędzi są skojarzone z poleceniami. Po kliknięciu przycisku paska narzędzi, polecenia skojarzone jest aktywowane. Przyciski paska narzędzi zwykle mają ikon, które sugerują podstawowych poleceń, takich jak drukarki dla polecenia drukowania. W kontrolce listy rozwijanej każdego elementu na liście jest skojarzony z innego polecenia. Kontroler menu jest hybrydowego, w którym obok kontrolki jest przycisku paska narzędzi, a druga strona jest strzałkę w dół, wyświetlający dodatkowe polecenia, po kliknięciu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolera Menu do paska narzędzi](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
- Podczas tworzenia polecenia należy również utworzyć program obsługi zdarzeń dla niego. Program obsługi zdarzeń określa, gdy polecenie jest widoczny czy włączone, można zmodyfikować jego tekstu i gwarantuje, że polecenie odpowiednio reaguje ("trasy") po aktywacji. W większości przypadków środowiska IDE programu obsługi poleceń przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Polecenia w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] trasy hierarchicznie, począwszy od najbardziej polecenia w kontekście, na podstawie wybranych lokalnych i kontynuowanie prowadzące kontekstu, w oparciu o wybór globalnego. Polecenia dodane do menu głównego są natychmiast dostępne dla skryptów. Aby uzyskać więcej informacji, zobacz [MenuCommands programu Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) i [wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md).  
  
  Aby zdefiniować nowe menu i paski narzędzi, możesz opisać je w pliku tabeli poleceń w usłudze Visual Studio (vsct). Szablon do pakietu Visual Studio tworzy tego pliku, wraz z elementów wymaganych do obsługi niezależnie od poleceń, paskach narzędzi i edytory, które wybrano w szablonie. Alternatywnie można napisać własny plik vsct przy użyciu schematu xml, opisane w tym miejscu: [Odwołanie do schematu VSCT XML](../../extensibility/vsct-xml-schema-reference.md).  
  
  Aby uzyskać więcej informacji na temat pracy z plikami vsct zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
  Tematy w tej sekcji wyjaśniono, jak działają polecenia, menu i paski narzędzi w pakietach VSPackage.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Szczegółowy opis specyfikacji formacie tabeli polecenia.  
  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Opis składni opartej na języku XML i kompilatora dla tabel polecenia.  
  
 [Domyślne położenie poleceń, grup i pasków narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 W tym artykule opisano poleceń wstępnie zdefiniowanych, grup, menu i paski narzędzi.  
  
 [Polecenia, menu i grupy definiowane w środowisku IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Określa wstępnie zdefiniowanych menu, poleceń i dostępne do użycia przez grup poleceń [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Projektowanie poleceń](../../extensibility/internals/command-design.md)  
 Wyjaśnia, jak projektować poleceń.  
  
 [Optymalizacja poleceń menu i paska narzędzi](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Zawiera wskazówki dla polecenia.  
  
 [Udostępnianie poleceń](../../extensibility/internals/making-commands-available.md)  
 Wyjaśnia, jak udostępnić poleceń programu Visual Studio.  
  
 [Polecenia i menu, w których używane są zestawy międzyoperacyjne](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Wyjaśnia sposób implementacji poleceń, które używają zestawów międzyoperacyjnych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 W tym artykule wyjaśniono, routing poleceń w pakietach VSPackage.
