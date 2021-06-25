---
title: Strony właściwości | Microsoft Docs
description: Dowiedz się więcej na temat pracy ze stronami właściwości dla nowego typu projektu w zestawie SDK Visual Studio, który umożliwia użytkownikom wyświetlanie i zmienianie właściwości projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88ebf99ef2361a232c4a5c4c02b9a140155d66e9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903414"
---
# <a name="property-pages"></a>Strony właściwości
Użytkownicy mogą wyświetlać i zmieniać właściwości zależne od konfiguracji i niezależne od projektu przy użyciu stron właściwości. Przycisk **Strony właściwości** jest  włączony w oknie Właściwości lub Eksplorator rozwiązań pasku narzędzi dla obiektów, które zapewniają widok strony właściwości wybranego obiektu. Strony właściwości są tworzone przez środowisko i są dostępne dla rozwiązań i projektów. Można je jednak również udostępnić dla elementów projektu, które korzystają z właściwości zależnych od konfiguracji. Ta możliwość może być używana, gdy pliki w projekcie wymagają różnych ustawień przełącznika kompilatora w celu poprawnej kompilacji.

## <a name="using-property-pages"></a>Korzystanie ze stron właściwości
 Jeśli strona właściwości jest już wyświetlana i wybór zmieni się (na przykład z rozwiązania na projekt), informacje wyświetlane na stronach zmienią się, aby wyświetlić właściwości nowego wyboru. Jeśli nie ma żadnych właściwości obiektu, które obsługują strony właściwości, strona właściwości jest pusta.

 Jeśli wybrano wiele obiektów, strona właściwości wyświetla część wspólną właściwości dla wszystkich zaznaczonych elementów. Jeśli wybrany element nie zawiera właściwości zależnych od konfiguracji i przycisk Strony właściwości na pasku Eksplorator rozwiązań narzędziu, fokus zmieni się na okno Właściwości.  Aby uzyskać więcej informacji dotyczących okno Właściwości i wyboru, zobacz [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md).

 Jeśli właściwości są wyświetlane dla wielu obiektów i zmienisz wartość na stronie właściwości, wszystkie wartości obiektów zostaną ustawione na nową wartość, nawet jeśli początkowo były różne, a strona była pusta, gdy były wyświetlane właściwości poszczególnych obiektów.

 Istnieją dwa ogólne typy okien dialogowych **ProjectProperty Pages** dostępne w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Na przykład w przypadku Visual Basic strony właściwości są wyświetlane przy użyciu formatu pola, jak pokazano na poniższym zrzucie ekranu. W drugim, pokazanym w dalszej części tej sekcji, strona właściwości hostuje siatkę właściwości podobną do siatki w oknie Właściwości.

 ![Visual Basic właściwości](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Okno dialogowe Strony właściwości projektu z formatem pola i strukturą drzewa

 Struktura drzewa w oknie dialogowym Strony właściwości nie jest budowaną przy użyciu funkcji <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . Środowisko, na podstawie nazwy poziomu przekazanej do niego przez interfejsy i <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> , tworzy je.

 Na stronach właściwości są dostępne tylko dwie kategorie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] najwyższego poziomu:

- Typowe właściwości, które wyświetla informacje niezależne od konfiguracji dla wybranego obiektu lub obiektów. W związku z tym po wybraniu jednej z podkategorii Właściwości wspólne opcje konfiguracji, platformy i Menedżer konfiguracji w górnej części okna dialogowego nie są dostępne.

- Właściwości konfiguracji, które zawierają informacje zależne od konfiguracji dotyczące parametrów debugowania, optymalizacji i kompilacji dla rozwiązania lub projektu.

  Nie można tworzyć żadnych dodatkowych kategorii najwyższego poziomu, ale możesz nie wyświetlać jednej lub drugiej kategorii w implementacji programu `IVsPropertyPage` . Jeśli na przykład nie masz żadnych właściwości niezależnych od konfiguracji do wyświetlenia dla obiektu, możesz nie wyświetlać kategorii Typowe właściwości. Podczas implementowania w obiekcie konfiguracji (obiekcie implementowym , i powiązanych interfejsach) wyświetlane są typowe właściwości, jeśli zostały zaimplementowane z obiektu przeglądania elementu i `ISpecifyPropertyPages` `ISpecifyPropertyPages` właściwości `IVsCfg` `IVsProjectCfg` konfiguracji.

  Każda kategoria wyświetlana w kategorii najwyższego poziomu reprezentuje oddzielną stronę właściwości. Wpisy kategorii i podkategorii dostępne w oknie dialogowym są określane przez implementację i `ISpecifyPropertyPages` `IVsPropertyPage` .

  `IDispatch` obiekty elementów w kontenerze wyboru, które mają właściwości, które mają być wyświetlane na stronach właściwości, implementują w celu wyliczenia `ISpecifyPropertyPages` listy identyfikatorów klas. Identyfikatory klas są przekazywane jako zmienne do klas i są używane do wystąpienia `ISpecifyPropertyPages` stron właściwości. Lista identyfikatorów klas jest również przekazywana do klasy w celu utworzenia struktury drzewa po lewej `IVsPropertyPage` stronie okna dialogowego. Strony właściwości następnie przekażą informacje z powrotem do obiektu, który implementuje i wypełnia informacje `IDispatch` `ISpecifyPropertyPages` dla każdej strony.

  Właściwości obiektu przeglądania są pobierane przy użyciu właściwości `IDispatch` dla każdego obiektu w kontenerze wyboru.

  Implementacja `Help::DisplayTopicFromF1Keyword` w pakietach VSPackage zapewnia funkcjonalność przycisku Pomoc.

  Aby uzyskać więcej informacji, zobacz `IDispatch` i `ISpecifyPropertyPages` w bibliotece MSDN.

  Drugi typ stron właściwości wyświetlany w przykładach hostuje formularz siatki właściwości, jak pokazano na poniższym zrzucie ekranu.

  ![Strony właściwości VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Okno dialogowe Strony właściwości z siatką właściwości

  Interfejsy i `IVSMDPropertyBrowser` `IVSMDPropertyGrid` (zadeklarowane w pliku vsmanaged.h) są używane do tworzenia i wypełniania siatki właściwości w oknie dialogowym lub oknie.

  Architektura projektów znacznie się zmieniła w poprzednich wersjach programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . W szczególności zmienił się sposób, w jaki projekt jest aktywny. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programie nie ma koncepcji aktywnego projektu. W poprzednich środowiskach programistycznych aktywny projekt był projektem, w ramach których polecenia kompilacji i wdrażania domyślnie były kompilowane i wdrażane niezależnie od kontekstu. Teraz rozwiązanie kontroluje i dowolnie określa, które polecenia kompilacji i wdrażania mają zastosowanie do które projekty.

  To, co wcześniej było aktywnym projektem, jest teraz przechwytywane na jeden z trzech różnych sposobów:

- Projekt startowy

   Projekt lub projekty można określić na stronie właściwości rozwiązania, które zostaną uruchomione, gdy użytkownik naciśnie klawisz F5 lub wybierze polecenie Uruchom z menu Kompilacja. Działa to w sposób podobny do starego aktywnego projektu w tym sensie, że jego nazwa jest wyświetlana w Eksplorator rozwiązań czcionką pogrubioną.

   Projekt startowy można pobrać jako właściwość w modelu automatyzacji, `DTE.Solution.SolutionBuild.StartupProjects` wywołując . W pakietach VSPackage należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metody lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> . `IVsSolutionBuildManager` jest dostępny jako usługa przez na `QueryService` SID_SVsSolutionBuildManager. Aby uzyskać więcej informacji, zobacz [Project Configuration Object](../../extensibility/internals/project-configuration-object.md) and Solution Configuration (Obiekt konfiguracji projektu i Konfiguracja [rozwiązania).](../../extensibility/internals/solution-configuration.md)

- Konfiguracja aktywnej kompilacji rozwiązania

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ma aktywną konfigurację rozwiązania, dostępną w modelu automatyzacji przez zaimplementowanie programu `DTE.Solution.SolutionBuild.ActiveConfiguration` . Konfiguracja rozwiązania to kolekcja zawierająca jedną konfigurację projektu dla każdego projektu w rozwiązaniu (każdy projekt może mieć wiele konfiguracji na wielu platformach o różnych nazwach). Aby uzyskać więcej informacji dotyczących stron właściwości rozwiązania, zobacz [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md).

- Aktualnie wybrany projekt

   <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>Zaim implementuj metodę , aby pobrać wybraną hierarchię projektu i element projektu lub wybrane elementy. Z DTE należy użyć metod `SelectedItems.SelectedItem.Project` `SelectedItems.SelectedItem.ProjectItem` i . Pod tymi nagłówkami w podstawowych dokumentach znajduje się [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przykładowy kod.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
