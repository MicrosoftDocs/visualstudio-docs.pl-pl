---
title: Strony właściwości | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f7aa506e806cc83876475a2fea0a3a949a7198f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837891"
---
# <a name="property-pages"></a>Strony właściwości
Użytkownicy mogą przeglądać i zmieniać właściwości zależne od konfiguracji i - niezależny od projektu za pomocą strony właściwości. A **stron właściwości** przycisk jest aktywny w **właściwości** oknie lub na pasku narzędzi Eksploratora rozwiązań dla obiektów, które zapewniają widok strony właściwości wybranego obiektu. Strony właściwości są tworzone przez środowisko i są dostępne dla projektów i rozwiązań. Jednak mogą również być udostępnione dla elementów projektu, które należy używać właściwości zależne od konfiguracji. Ta funkcja może być używany, gdy pliki w obrębie projektu wymaga ustawienia przełącznika kompilatora różnych, aby kompilować się właściwie.  
  
## <a name="using-property-pages"></a>Używanie stron właściwości  
 Jeśli już zostanie wyświetlona strona właściwości i zmieni się zaznaczenie (np. z rozwiązaniem do projektu), informacje wyświetlane na stronach zmiany, aby wyświetlić właściwości dla nowego wyboru. Jeśli nie istnieją w obiekcie właściwości, które obsługują strony właściwości, strona właściwości jest pusta.  
  
 Jeśli wybrano wiele obiektów, na stronie właściwości wyświetla część wspólną właściwości dla wszystkich wybranych elementów. Jeśli wybrany element nie zawiera właściwości zależne od konfiguracji i **stron właściwości** kliknięto przycisk na pasku narzędzi Eksploratora rozwiązań, fokus zmieni się na oknie dialogowym właściwości. Aby uzyskać więcej informacji dotyczących okna właściwości i wyboru, zobacz [rozszerzanie właściwości](../../extensibility/internals/extending-properties.md).  
  
 Jeśli właściwości są wyświetlane dla wielu obiektów, a następnie zmień wartość na stronie właściwości, wszystkie wartości dla obiektów są ustawione na nową wartość nawet jeśli zostały one początkowo różnych i strony podczas pustej właściwości poszczególnych obiektów były wyświetlane.  
  
 Istnieją dwa ogólne typy **stron ProjectProperty** dialogowych dostępne w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W pierwszym w projektach języka Visual Basic na przykład na stronach właściwości są wyświetlane przy użyciu formatu pola, jak pokazano na poniższym zrzucie ekranu. W drugim przedstawione później w tej sekcji, właściwości hostów strony siatki właściwości doświadczyli w oknie dialogowym właściwości.  
  
 ![Strony właściwości języka Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Okno dialogowe strony właściwości projektu o strukturze format i drzewa pola  
  
 Struktura drzewa w oknie dialogowym stron właściwości nie został skompilowany przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Środowisko, na podstawie poziomu nazwy przekazany przez <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> interfejsy, tworzy go.  
  
 Tylko dwóm kategoriom najwyższego poziomu są dostępne na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stron właściwości:  
  
- Typowe właściwości, które wyświetla informacje o niezależne od konfiguracji dla zaznaczonego obiektu lub obiektów. W rezultacie po wybraniu jednej z podkategorii wspólne właściwości opcje konfiguracji, platformy i programu Configuration Manager, w górnej części okna dialogowego nie są dostępne.  
  
- Właściwości konfiguracji, który zawiera informacje zależne od konfiguracji odnoszące się do parametrów debugowanie, optymalizacji i kompilacji dla rozwiązania lub projektu.  
  
  Nie można utworzyć dowolne dodatkowe kategorie najwyższego poziomu, ale można wybrać nie wyświetlać jednej z nich w danej implementacji `IVsPropertyPage`. Jeśli na przykład nie masz żadnych właściwości niezależne od konfiguracji do wyświetlenia dla obiektu, istnieje możliwość nie kategorii Wspólne właściwości wyświetlania. Wyświetl typowe właściwości, jeśli `ISpecifyPropertyPages` jest implementowany z obiektu przeglądania elementu i właściwości konfiguracji podczas implementowania `ISpecifyPropertyPages` w obiekcie konfiguracji (obiektu implementującego `IVsCfg`, `IVsProjectCfg`i pokrewne interfejsy).  
  
  Każda kategoria wyświetlane w obszarze kategorii najwyższego poziomu reprezentuje stronę osobne właściwości. Kategorii i podkategorii wpisów w oknie dialogowym są określane przez implementacji `ISpecifyPropertyPages` i `IVsPropertyPage`.  
  
  `IDispatch` obiekty dla elementów w kontenerze zaznaczenia, które mają właściwości, które mają być wyświetlane na implementowanie stron właściwości `ISpecifyPropertyPages` wyliczyć listy identyfikatorów klas. Identyfikatory klasy są przekazywane jako zmienne `ISpecifyPropertyPages` i służą do tworzenia wystąpienia na stronach właściwości. Lista identyfikatorów klas również jest przekazywany do `IVsPropertyPage` do tworzenia struktury drzewa po lewej stronie okna dialogowego. Strony właściwości, a następnie Przekaż informacje z powrotem do `IDispatch` obiekt, który implementuje `ISpecifyPropertyPages` i wypełnia pola informacji dla każdej strony.  
  
  Właściwości obiektu przeglądania są pobierane przy użyciu `IDispatch` dla każdego obiektu w kontenerze zaznaczenia.  
  
  Implementowanie `Help::DisplayTopicFromF1Keyword` w swojej pakietu VSPackage oferuje funkcje dla przycisk Pomoc.  
  
  Aby uzyskać więcej informacji, zobacz `IDispatch` i `ISpecifyPropertyPages`w bibliotece MSDN.  
  
  Drugi typ strony właściwości wyświetlane w hostach przykłady postaci siatki właściwości, jak pokazano na poniższym zrzucie ekranu.  
  
  ![Strony właściwości VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
  Okno dialogowe strony właściwości z siatki właściwości  
  
  Interfejsy `IVSMDPropertyBrowser` i `IVSMDPropertyGrid` (deklaracja w vsmanaged.h) są używane do tworzenia i wypełniania siatki właściwości, w ramach lub oknie dialogowym.  
  
  Architektura projektów zmienił się znacznie z poprzednich wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W szczególności jest aktywny pojęcie projektu została zmieniona. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], nie obowiązuje koncepcja aktywnego projektu. W poprzednim środowiskach rozwojowych, polegającej aktywnego projektu była domyślnie projektu, który tworzenie i wdrażanie polecenia niezależnie od tego, w kontekście. Teraz rozwiązanie kontroluje i rozstrzyga o kolejności przetwarzania którego tworzenie i wdrażanie polecenia zastosowanie do projektów.  
  
  Jaki był wcześniej aktywny projekt teraz są przechwytywane w jednym z trzech sposobów:  
  
- Projekt startowy  
  
   Można określić projekt lub projekty ze strony właściwości rozwiązania, który zostanie uruchomiony, gdy użytkownik naciśnie klawisz F5 lub wybiera Uruchom z menu Kompiluj. Działa to w sposób podobny do starego aktywnego projektu w tym sensie, że jego nazwa jest wyświetlana w Eksploratorze rozwiązań pogrubioną czcionką.  
  
   Możesz pobrać projekt startowy jako właściwość w modelu automatyzacji, wywołując `DTE.Solution.SolutionBuild.StartupProjects`. W VSPackage, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metody. `IVsSolutionBuildManager` jest dostępna jako usługa przez `QueryService` na SID_SVsSolutionBuildManager. Aby uzyskać więcej informacji, zobacz [obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md) i [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md).  
  
- Konfiguracja kompilacji rozwiązania Active  
  
   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Konfiguracja aktywnego rozwiązania dostępne w modelu automatyzacji, implementując ma `DTE.Solution.SolutionBuild.ActiveConfiguration`. Konfiguracja rozwiązania jest kolekcja, która zawiera jedną konfigurację projektu dla każdego projektu w rozwiązaniu (każdy projekt może mieć wiele konfiguracji na wielu platformach, z różnymi nazwami). Aby uzyskać więcej informacji dotyczących strony właściwości rozwiązania, zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md).  
  
- Obecnie wybranego projektu  
  
   Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metodę, aby pobrać hierarchii projektu i elementu projektu lub wybrane elementy. Z DTE, należy użyć `SelectedItems.SelectedItem.Project` i `SelectedItems.SelectedItem.ProjectItem` metody. Brak przykładowego kodu w ramach tych nagłówków w obszarach podstawowych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dokumentów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)   
 [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)   
 [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)