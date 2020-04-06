---
title: Strony nieruchomości | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac788f51bcdc52cd39469a272909890333c5016b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706057"
---
# <a name="property-pages"></a>Strony właściwości
Użytkownicy mogą wyświetlać i zmieniać właściwości zależne od konfiguracji projektu i niezależne od niego przy użyciu stron właściwości. Przycisk **Strony właściwości** jest włączony w oknie **Właściwości** lub na pasku narzędzi Eksploratora rozwiązań dla obiektów, które zapewniają widok strony właściwości zaznaczonego obiektu. Strony właściwości są tworzone przez środowisko i są dostępne dla rozwiązań i projektów. Można je jednak również udostępnić dla elementów projektu, które korzystają z właściwości zależnych od konfiguracji. Ta funkcja może być używana, gdy pliki w projekcie wymagają różnych ustawień przełącznika kompilatora do prawidłowego tworzenia.

## <a name="using-property-pages"></a>Korzystanie ze stron właściwości
 Jeśli strona właściwości jest już wyświetlana i zaznaczenie zmienia się (na przykład z rozwiązania do projektu), informacje wyświetlane na stronach zmieniają się, aby wyświetlić właściwości nowego zaznaczenia. Jeśli nie ma żadnych właściwości na obiekcie, które obsługują strony właściwości, strona właściwości jest pusta.

 Jeśli zaznaczono wiele obiektów, na stronie właściwości zostanie wyświetlone przecięcie właściwości wszystkich zaznaczonych elementów. Jeśli zaznaczony element nie zawiera właściwości zależnych od konfiguracji, a przycisk **Strony właściwości** na pasku narzędzi Eksploratora rozwiązań zostanie kliknięty, fokus zmieni się w oknie Właściwości. Aby uzyskać więcej informacji dotyczących okna Właściwości i zaznaczenia, zobacz [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md).

 Jeśli właściwości są wyświetlane dla wielu obiektów i można zmienić wartość na stronie właściwości, wszystkie wartości dla obiektów są ustawione na nową wartość, nawet jeśli były one początkowo różne i strona była pusta, gdy właściwości poszczególnych obiektów były wyświetlane.

 Dostępne są dwa ogólne typy okien dialogowych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Strony projectproperty** dostępne w programie . W pierwszym dla projektów języka Visual Basic, na przykład strony właściwości są wyświetlane przy użyciu formatu pola, jak pokazano na poniższym zrzucie ekranu. W drugim, pokazanym w dalszej części tej sekcji, strona właściwości zawiera siatkę właściwości podobną do tej znalezionej w oknie Właściwości.

 ![Strony właściwości visual basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Okno dialogowe Strony właściwości projektu z formatem pola i strukturą drzewa

 Struktura drzewa w oknie dialogowym Strony <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>właściwości nie jest zbudowana przy użyciu programu . Środowisko, na podstawie nazwy poziomu przekazywane <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> niego przez i interfejsów, tworzy go.

 Istnieją tylko dwie kategorie najwyższego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poziomu dostępne na stronach właściwości:

- Common Properties, który wyświetla informacje niezależne od konfiguracji dla zaznaczonego obiektu lub obiektów. W rezultacie po wybraniu jednej z podkategorii właściwości wspólnych opcje konfiguracji, platformy i programu Menedżer konfiguracji w górnej części okna dialogowego nie są dostępne.

- Właściwości konfiguracji, który zawiera informacje zależne od konfiguracji odnoszące się do debugowania, optymalizacji i kompilacji parametrów dla rozwiązania lub projektu.

  Nie można utworzyć żadnych dodatkowych kategorii najwyższego poziomu, ale można wybrać, aby `IVsPropertyPage`nie wyświetlać jednej lub drugiej w implementacji programu . Jeśli na przykład nie masz żadnych właściwości niezależnych od konfiguracji do wyświetlenia dla obiektu, można wybrać opcję nie wyświetlania common properties kategorii. Właściwości Common są `ISpecifyPropertyPages` wyświetlane, jeśli są implementowane z obiektu przeglądania elementu `ISpecifyPropertyPages` i właściwości Konfiguracja podczas `IVsCfg`implementacji w obiekcie konfiguracji (obiekt implementujący , `IVsProjectCfg`i interfejsy pokrewne).

  Każda kategoria wyświetlana w kategorii najwyższego poziomu reprezentuje oddzielną stronę właściwości. Wpisy kategorii i podkategorii dostępne w oknie `ISpecifyPropertyPages` dialogowym są określane przez implementację i `IVsPropertyPage`.

  `IDispatch`obiekty dla elementów w kontenerze zaznaczenia, które mają `ISpecifyPropertyPages` właściwości, które mają być wyświetlane na stronach właściwości implementacji do wyliczenia listy identyfikatorów klas. Identyfikatory klas są przekazywane jako `ISpecifyPropertyPages` zmienne i są używane do tworzenia wystąpienia stron właściwości. Lista identyfikatorów klas jest również `IVsPropertyPage` przekazywana do tworzenia struktury drzewa po lewej stronie okna dialogowego. Strony właściwości następnie przekazać informacje `IDispatch` z powrotem do obiektu, który implementuje `ISpecifyPropertyPages` i wypełnia informacje dla każdej strony.

  Właściwości obiektu browse są pobierane `IDispatch` przy użyciu dla każdego obiektu w kontenerze zaznaczenia.

  Implementacja `Help::DisplayTopicFromF1Keyword` w programie VSPackage udostępnia funkcje przycisku Pomoc.

  Aby uzyskać więcej `IDispatch` `ISpecifyPropertyPages`informacji, zobacz i w bibliotece MSDN.

  Drugi typ stron właściwości wyświetlanych w przykładach zawiera formę siatki właściwości, jak pokazano na poniższym zrzucie ekranu.

  ![Strony właściwości VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Okno dialogowe Strony właściwości z siatką właściwości

  Interfejsy `IVSMDPropertyBrowser` i `IVSMDPropertyGrid` (zadeklarowane w vsmanaged.h) są używane do tworzenia i wypełniania siatki właściwości w oknie dialogowym lub oknie.

  Architektura projektów znacznie się zmieniła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]w porównaniu z poprzednimi wersjami . W szczególności zmieniło się pojęcie, który projekt jest aktywny. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]programie nie ma koncepcji aktywnego projektu. W poprzednich środowiskach programistycznych aktywnym projektem był projekt, który tworzył i wdrażał polecenia, aby domyślnie niezależnie od kontekstu. Teraz rozwiązanie kontroluje i rozstrzyga, które polecenia kompilacji i wdrażania mają zastosowanie do projektów.

  To, co wcześniej było aktywnym projektem, jest teraz przechwytywane na jeden z trzech różnych sposobów:

- Projekt Uruchamianie

   Można określić projekt lub projekty ze strony właściwości rozwiązania, które zostaną uruchomione, gdy użytkownik naciśnie klawisz F5 lub wybierz uruchom z menu Kompilacja. Działa to w sposób podobny do starego aktywnego projektu w tym sensie, że jego nazwa jest wyświetlana w Eksploratorze rozwiązań z pogrubioną czcionką.

   Projekt uruchamiania można pobrać jako właściwość w `DTE.Solution.SolutionBuild.StartupProjects`modelu automatyzacji, wywołując program . W VSPackage, można <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> lub metody. `IVsSolutionBuildManager`jest dostępna jako `QueryService` usługa przez SID_SVsSolutionBuildManager. Aby uzyskać więcej informacji, zobacz [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md) i [konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md).

- Konfiguracja kompilacji aktywnego rozwiązania

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]posiada aktywną konfigurację rozwiązania, dostępną `DTE.Solution.SolutionBuild.ActiveConfiguration`w modelu automatyzacji poprzez wdrożenie . Konfiguracja rozwiązania to kolekcja, która zawiera jedną konfigurację projektu dla każdego projektu w rozwiązaniu (każdy projekt może mieć wiele konfiguracji, na wielu platformach, z odmiennymi nazwami). Aby uzyskać więcej informacji dotyczących stron właściwości rozwiązania, zobacz [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md).

- Projekt aktualnie wybrany

   Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metodę pobierania hierarchii projektu i elementu projektu lub wybranych elementów. Z DTE, należy `SelectedItems.SelectedItem.Project` użyć `SelectedItems.SelectedItem.ProjectItem` i metody. Istnieje przykładowy kod pod tymi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nagłówkami w dokumentach podstawowych.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
