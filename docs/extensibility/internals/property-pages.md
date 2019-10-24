---
title: Strony właściwości | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51487b35686da9676f201a157ddb8e47afb75ce8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725058"
---
# <a name="property-pages"></a>Strony właściwości
Użytkownicy mogą wyświetlać i zmieniać właściwości zależne od konfiguracji projektu i niezależne za pomocą stron właściwości. Przycisk **strony właściwości** jest włączony w oknie **właściwości** lub na Eksplorator rozwiązań pasku narzędzi dla obiektów, które udostępniają widok strony właściwości zaznaczonego obiektu. Strony właściwości są tworzone przez środowisko i są dostępne dla rozwiązań i projektów. Mogą one być jednak dostępne dla elementów projektu, które wykorzystują właściwości zależne od konfiguracji. Tej funkcji można użyć, gdy pliki w projekcie wymagają różnych ustawień przełącznika kompilatora w celu poprawnego skompilowania.

## <a name="using-property-pages"></a>Korzystanie ze stron właściwości
 Jeśli strona właściwości jest już wyświetlana i zmieni się zaznaczenie (na przykład z rozwiązania do projektu), informacje wyświetlane na stronach zmieniają się, aby wyświetlić właściwości nowego zaznaczenia. Jeśli nie ma żadnych właściwości w obiekcie, który obsługuje strony właściwości, Strona właściwości jest pusta.

 W przypadku wybrania wielu obiektów na stronie właściwości zostanie wyświetlona część wspólna właściwości dla wszystkich wybranych elementów. Jeśli wybrany element nie zawiera właściwości zależnych od konfiguracji, a przycisk **strony właściwości** na pasku narzędzi Eksplorator rozwiązań zostanie kliknięty, fokus zmieni się na okno właściwości. Aby uzyskać więcej informacji dotyczących okno Właściwości i wyboru, zobacz [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md).

 Jeśli właściwości są wyświetlane dla wielu obiektów i zmieniasz wartość na stronie właściwości, wszystkie wartości dla obiektów są ustawiane na nową wartość, nawet jeśli były one początkowo inne, a strona była pusta, gdy zostaną wyświetlone właściwości poszczególnych obiektów.

 @No__t_1 dostępne są dwa ogólne typy okien dialogowych **stron ProjectProperty** . Na przykład w przypadku projektów Visual Basic są wyświetlane strony właściwości przy użyciu formatu pola, jak pokazano na poniższym zrzucie ekranu. W drugim pokazano w dalszej części tej sekcji Strona właściwości zawiera siatkę właściwości podobną do tej, która znajduje się w oknie właściwości.

 ![Visual Basic strony właściwości](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Okno dialogowe strony właściwości projektu z formatem pola i strukturą drzewa

 Struktura drzewa w oknie dialogowym strony właściwości nie jest skompilowana przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Środowisko, na podstawie nazwy poziomu przekazaną do niej przez <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> i interfejsy <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>, kompiluje ją.

 Na stronach właściwości [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są dostępne tylko dwie kategorie najwyższego poziomu:

- Wspólne właściwości, które wyświetlają informacje niezależne od konfiguracji dla wybranego obiektu lub obiektów. W związku z tym, gdy zostanie wybrana jedna z kategorii wspólnych właściwości, opcje konfiguracji, platformy i Configuration Manager w górnej części okna dialogowego są niedostępne.

- Właściwości konfiguracji, które zawierają informacje zależne od konfiguracji dotyczące debugowania, optymalizacji i parametrów kompilacji dla rozwiązania lub projektu.

  Nie można utworzyć żadnych dodatkowych kategorii najwyższego poziomu, ale możesz zrezygnować z wyświetlania jednej lub drugiej w implementacji `IVsPropertyPage`. Jeśli na przykład nie masz żadnych właściwości niezależnych od konfiguracji do wyświetlenia dla obiektu, możesz wybrać opcję nie wyświetlaj kategorii wspólnych właściwości. W `ISpecifyPropertyPages` przypadku zaimplementowania `ISpecifyPropertyPages` w obiekcie Configuration (obiekt implementujący `IVsCfg`, `IVsProjectCfg` i interfejsy pokrewne) są wyświetlane wspólne właściwości.

  Każda kategoria wyświetlana w kategorii najwyższego poziomu reprezentuje osobną stronę właściwości. Pozycje kategorii i podkategorii dostępne w oknie dialogowym są określane przez implementację `ISpecifyPropertyPages` i `IVsPropertyPage`.

  `IDispatch` obiektów dla elementów w kontenerze wyboru, które mają właściwości, które mają być wyświetlane na stronach właściwości Implementuj `ISpecifyPropertyPages`, aby wyliczyć listę identyfikatorów klas. Identyfikatory klas są przesyłane jako zmienne do `ISpecifyPropertyPages` i są używane do tworzenia wystąpień stron właściwości. Lista identyfikatorów klas jest również przenoszona do `IVsPropertyPage`, aby utworzyć strukturę drzewa po lewej stronie okna dialogowego. Strony właściwości przekazują informacje z powrotem do obiektu `IDispatch`, który implementuje `ISpecifyPropertyPages` i wypełnia informacje dla każdej strony.

  Właściwości obiektu Browse są pobierane przy użyciu `IDispatch` dla każdego obiektu w kontenerze wyboru.

  Wdrożenie `Help::DisplayTopicFromF1Keyword` w pakietu VSPackage udostępnia funkcje przycisku pomoc.

  Aby uzyskać więcej informacji, zobacz `IDispatch` i `ISpecifyPropertyPages`in bibliotece MSDN.

  Drugi typ stron właściwości wyświetlanych w przykładach obsługuje formularz siatki właściwości, jak pokazano na poniższym zrzucie ekranu.

  ![Strony właściwości VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Okno dialogowe strony właściwości z siatką właściwości

  Interfejsy `IVSMDPropertyBrowser` i `IVSMDPropertyGrid` (zadeklarowane w vsmanaged. h) służą do tworzenia i wypełniania siatki właściwości w oknie dialogowym lub w oknach.

  Architektura projektów została znacznie zmieniona z wcześniejszych wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W szczególności pojęcie, dla którego projekt jest aktywny, zostało zmienione. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie ma koncepcji aktywnego projektu. W poprzednich środowiskach programistycznych aktywny projekt był projektem, który kompiluje i wdraża polecenia domyślnie, bez względu na kontekst. Teraz rozwiązanie kontroluje i rozstrzyga, które polecenia Kompiluj i Wdróż mają zastosowanie do projektów.

  Wcześniej aktywny projekt jest teraz przechwytywany na jeden z trzech różnych sposobów:

- Projekt startowy

   Możesz określić projekt lub projekty na stronie właściwości rozwiązania, która będzie uruchamiana, gdy użytkownik naciśnie klawisz F5 lub wybierze opcję Uruchom z menu Kompilacja. Działa to podobnie jak w przypadku starego aktywnego projektu w sensie, że jego nazwa jest wyświetlana w Eksplorator rozwiązań z pogrubioną czcionką.

   Możesz pobrać projekt startowy jako właściwość w modelu automatyzacji, wywołując `DTE.Solution.SolutionBuild.StartupProjects`. W pakietu VSPackage można wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metody. `IVsSolutionBuildManager` jest dostępna jako usługa, `QueryService` w SID_SVsSolutionBuildManager. Aby uzyskać więcej informacji, zobacz temat Konfiguracja [obiektu i projektu](../../extensibility/internals/project-configuration-object.md) [rozwiązania](../../extensibility/internals/solution-configuration.md).

- Konfiguracja kompilacji aktywnego rozwiązania

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ma aktywną konfigurację rozwiązania dostępną w modelu automatyzacji przez implementację `DTE.Solution.SolutionBuild.ActiveConfiguration`. Konfiguracja rozwiązania jest kolekcją zawierającą jedną konfigurację projektu dla każdego projektu w rozwiązaniu (każdy projekt może mieć wiele konfiguracji na wielu platformach z niepodobnymi nazwami). Aby uzyskać więcej informacji dotyczących stron właściwości rozwiązania, zobacz [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md).

- Aktualnie wybrany projekt

   Zaimplementuj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>, aby pobrać hierarchię projektu i element projektu lub wybrane elementy. Z DTE można użyć metod `SelectedItems.SelectedItem.Project` i `SelectedItems.SelectedItem.ProjectItem`. Poniżej znajdują się przykładowe kody w dokumentach podstawowych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)