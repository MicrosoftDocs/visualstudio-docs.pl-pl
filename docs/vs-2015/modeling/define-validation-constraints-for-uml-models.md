---
title: Definiowanie ograniczeń walidacji dla modeli UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9591875b525d44e343f8326b7f5a145b04b57cff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071165"
---
# <a name="define-validation-constraints-for-uml-models"></a>Definiowanie ograniczeń walidacji dla modeli UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zdefiniować ograniczenia sprawdzania poprawności, które sprawdzić, czy model spełnia określony warunek, który określisz. Na przykład można zdefiniować ograniczenie, aby upewnić się, że użytkownik nie utworzy pętli relacji dziedziczenia. Ograniczenie jest wywoływane, gdy użytkownik próbuje otworzyć lub zapisać model i można również uruchomić ręcznie. Jeśli ograniczenie nie powiedzie się, komunikat o błędzie, który zdefiniujesz jest dodawany do okna błędu. Można spakować te ograniczenia w rozszerzeniu integracji programu Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) i rozdystrybuować je innym użytkownikom programu Visual Studio.  
  
 Można również zdefiniować ograniczenia, które sprawdzają poprawność modelu przed zasobami zewnętrznymi, takich jak bazy danych. Jeśli chcesz sprawdzić poprawność kodu programu względem diagramu warstwy, zobacz [Dodawanie niestandardowej walidacji architektury do diagramów warstw](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują modeli UML, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="requirements"></a>Wymagania  
 Zobacz [wymagania](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="applying-validation-constraints"></a>Stosowanie ograniczeń sprawdzania poprawności  
 Sprawdzanie poprawności ograniczenia jest stosowane w trzech przypadkach: po zapisaniu modelu; Po otwarciu modelu; i po kliknięciu **Sprawdź poprawność modelu UML** na **architektury** menu. W każdym przypadku tylko ograniczenia, które zostały zdefiniowane dla tego przypadku zostaną zastosowane, chociaż zazwyczaj można zdefiniować każde ograniczenie do zastosowania w więcej niż jednym przypadku.  
  
 Błędy sprawdzania poprawności są zgłaszane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] błędy, a następnie kliknąć dwukrotnie błąd, aby wybrać elementy modelu, które znajdują się w błędzie.  
  
 Aby uzyskać więcej informacji dotyczących stosowania walidacji, zobacz [Weryfikacja modelu UML](../modeling/validate-your-uml-model.md).  
  
## <a name="defining-a-validation-extension"></a>Definiowanie rozszerzenia sprawdzania poprawności  
 Aby utworzyć rozszerzenie sprawdzania poprawności dla projektanta UML, należy utworzyć klasę, która definiuje ograniczenia sprawdzania poprawności i osadzić tę klasę w Visual Studio Integration rozszerzenie (VSIX). VSIX działa jako kontener, który może zainstalować ograniczenie. Istnieją dwie alternatywne metody definiowania rozszerzenia sprawdzania poprawności:  
  
- **Utwórz rozszerzenie walidacji w jego własnym VSIX przy użyciu szablonu projektu.** Jest to szybsza metoda. Użyj go, jeśli nie chcesz połączyć ograniczeń sprawdzania poprawności z innymi rodzajami rozszerzeń takich jak polecenia menu, elementy do przybornika niestandardowego lub program obsługi gestów. Można zdefiniować kilka ograniczeń w jednej klasie.  
  
- **Utwórz osobną klasę weryfikacji i projektów VSIX.** Użyj tej metody, jeśli chcesz połączyć kilka rodzajów rozszerzeń w samym VSIX. Na przykład jeśli polecenie menu oczekuje modelu do przestrzegania szczególnych ograniczeń, można ją osadzić w samym VSIX jako metodę sprawdzania poprawności.  
  
#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>Aby utworzyć rozszerzenie sprawdzania poprawności w jego własnym VSIX  
  
1. W **nowy projekt** dialogowego **projekty modelowania**, wybierz opcję **rozszerzenie sprawdzania poprawności**.  
  
2. Otwórz **.cs** plik w nowym projekcie i Modyfikuj klasę, aby wdrożyć swoje ograniczenia sprawdzania poprawności.  
  
    Aby uzyskać więcej informacji, zobacz [oceny ograniczenie sprawdzania poprawności](#Implementing).  
  
   > [!IMPORTANT]
   >  Upewnij się, że Twoje **.cs** pliki zawierają następujące `using` instrukcji:  
   >   
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
3. Możesz dodać dodatkowe ograniczenia definiując nowe metody. Aby określić metodę jako metodę sprawdzania poprawności, jego muszą być oznakowane za pomocą atrybutów w taki sam sposób, jak metoda wstępnego sprawdzania poprawności.  
  
4. Przetestuj swoje ograniczenia, naciskając klawisz F5. Aby uzyskać więcej informacji, zobacz [wykonywanie ograniczenia sprawdzania poprawności](#Executing).  
  
5. Zainstaluj polecenie menu na innym komputerze przez skopiowanie pliku **bin\\\*\\\*.vsix** utworzonego w projekcie. Aby uzyskać więcej informacji, zobacz [Instalowanie i odinstalowywanie rozszerzenia](#Installing).  
  
   Po dodaniu innych **.cs** plików, będzie zwykle wymagają następującej `using` instrukcji:  
  
```csharp  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Uml.Classes;  
  
```  
  
 W tym miejscu jest alternatywna procedura:  
  
#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>Aby utworzyć ograniczenie osobnego sprawdzania poprawności w projekcie biblioteki klas  
  
1. Utwórz projekt biblioteki klas, dodając go do istniejącego rozwiązania VSIX albo tworząc nowe rozwiązanie.  
  
    1. Na **pliku** menu, wybierz **New**, **projektu**.  
  
    2. W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C#** lub **języka Visual Basic**, a następnie w środkowej kolumnie Wybierz **biblioteki klas**.  
  
2. Chyba że rozwiązanie zawiera już jeden, Utwórz projekt VSIX:  
  
    1. W **Eksploratora rozwiązań**, w menu skrótów rozwiązania wybierz **Dodaj**, **nowy projekt**.  
  
    2. W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C#** lub **języka Visual Basic**, następnie wybierz **rozszerzalności**. W środkowej kolumnie kliknij **projekt VSIX**.  
  
3. Ustaw projekt VSIX jako projekt startowy rozwiązania.  
  
    - W Eksploratorze rozwiązań w menu skrótów projektu VSIX wybierz **Ustaw jako projekt startowy**.  
  
4. W **source.extension.vsixmanifest**w obszarze **zawartości**, Dodaj projekt biblioteki klas jako składnik MEF:  
  
    1. Na **metadanych** kartę, ustaw nazwę VSIX.  
  
    2. Na **Instaluj obiekty docelowe** kartę, należy ustawić wersji programu Visual Studio jako obiekty docelowe.  
  
    3. Na **zasoby** kartę, wybrać **New**i w oknie dialogowym Ustaw:  
  
         **Typ** = **składnik MEF**  
  
         **Źródło** = **projekt w bieżącym rozwiązaniu**  
  
         **Projekt** = *projektu biblioteki klas*  
  
#### <a name="to-define-the-validation-class"></a>Aby zdefiniować klasę walidacji  
  
1. Nie potrzebujesz tej procedury, jeśli utworzono klasy weryfikacji z własnej VSIX z szablonu projektu sprawdzania poprawności.  
  
2. W projekcie klasy sprawdzania poprawności, należy dodać odwołania do następujących [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] zestawów:  
  
     `Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
     `Microsoft.VisualStudio.Uml.Interfaces`  
  
     `System.ComponentModel.Composition`  
  
3. Dodaj plik do projektu biblioteki klas zawierający kod, który jest podobny do poniższego przykładu.  
  
    - Każde ograniczenie sprawdzania poprawności znajduje się w metodzie, która jest oznaczona szczególnym atrybutem. Metoda akceptuje parametr typu elementu modelu. Podczas sprawdzania poprawności, szablon sprawdzania poprawności zastosuje każdej metody sprawdzania poprawności do każdego elementu modelu, który odpowiada jego typowi parametru.  
  
    - Metody te można umieścić w jakiejkolwiek klasie i przestrzeni nazw. Należy je zmienić zgodnie z preferencjami.  
  
    ```  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using Microsoft.VisualStudio.Modeling.Validation;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
    using Microsoft.VisualStudio.Uml.Classes;  
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.  
  
    namespace Validation  
    {  
      public class MyValidationExtensions  
      {  
        // SAMPLE VALIDATION METHOD.  
        // All validation methods have the following attributes.  
        [Export(typeof(System.Action<ValidationContext, object>))]  
        [ValidationMethod(  
           ValidationCategories.Save  
         | ValidationCategories.Open  
         | ValidationCategories.Menu)]  
        public void ValidateClassNames  
          (ValidationContext context,   
           // This type determines what elements   
           // will be validated by this method:  
           IClass elementToValidate)  
        {  
          // A validation method should not change the model.  
  
          List<string> attributeNames = new List<string>();  
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)  
          {  
            string name = attribute.Name;  
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))  
            {  
              context.LogError(  
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),  
                "001", elementToValidate);  
            }  
            attributeNames.Add(name);  
          }  
  
        }  
        // Add more validation methods for different element types.  
      }  
    }  
    ```  
  
## <a name="Executing"></a> Wykonywanie ograniczenia sprawdzania poprawności  
 Do celów testowych wykonaj metody walidacji w trybie debugowania.  
  
#### <a name="to-test-the-validation-constraint"></a>Aby przetestować ograniczenie sprawdzania poprawności  
  
1. Naciśnij klawisz **F5**, lub na **debugowania** menu, wybierz **Rozpocznij debugowanie**.  
  
     Eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoczyna się.  
  
     **Rozwiązywanie problemów z**: Jeśli nowy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie można uruchomić:  
  
    - Jeśli masz więcej niż jeden projekt, upewnij się, że projekt VSIX jest ustawiony jako projekt startowy rozwiązania.  
  
    - W Eksploratorze rozwiązań w menu skrótów uruchamiania lub tylko projektu, wybierz **właściwości**. W edytorze właściwości projektu zaznacz **debugowania** kartę. Upewnij się, że ciąg w **uruchomienia programu zewnętrznego** pole jest pełna nazwa ścieżki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zazwyczaj:  
  
         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2. W eksperymentalnym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Otwórz lub Utwórz projekt modelowania i otworzyć lub utworzyć diagram modelowania.  
  
3. Aby skonfigurować test próbki ograniczenia podany w poprzedniej sekcji:  
  
    1. Otwórz diagram klas.  
  
    2. Utwórz klasę i dodaj dwa atrybuty, które mają taką samą nazwę.  
  
4. W menu skrótów w dowolnym miejscu na diagramie wybierz **weryfikacji**.  
  
5. Błędy w modelu będą raportowane w oknie błędów.  
  
6. Kliknij dwukrotnie raport o błędach. Jeśli elementy wymienione w raporcie są widoczne na ekranie, zostaną one wyróżnione.  
  
     **Rozwiązywanie problemów z**: Jeśli **weryfikacji** nie ma polecenia menu, upewnij się, że:  
  
    - Projekt sprawdzania poprawności jest wymieniony jako składnik listy MEF **zasoby** karcie **source.extensions.manifest** w projekcie VSIX.  
  
    - Poprawny `Export` i `ValidationMethod` atrybuty są dołączone do metody sprawdzania poprawności.  
  
    - `ValidationCategories.Menu` znajduje się w argumencie `ValidationMethod` atrybutu i składa się z innych wartości przy użyciu logicznych lub (&#124;).  
  
    - Parametry wszystkich `Import` i `Export` atrybuty są prawidłowe.  
  
## <a name="Implementing"></a> Ocena ograniczenia  
 Metoda sprawdzania poprawności powinna ustalić, czy ograniczenie sprawdzania poprawności, które chcesz zastosować jest wartość PRAWDA lub FAŁSZ. W przypadku opcji true nie powinny nic robić. Jeśli ma wartość FAŁSZ, należy zgłosić błąd przy użyciu metod dostarczonych przez `ValidationContext` parametru.  
  
> [!NOTE]
>  Metody sprawdzania poprawności nie powinny zmieniać modelu. Nie ma gwarancji po lub w jakiej kolejności ograniczenia zostaną wykonane. Jeśli masz do przekazywania informacji między kolejnymi wykonaniami metody sprawdzania poprawności w ramach przebiegu weryfikacji, można użyć pamięci podręcznej kontekstu opisanej w obszarze [koordynacja wielokrotnego sprawdzania poprawności](#ContextCache).  
  
 Na przykład jeśli chcesz upewnić się, że każdy typ (klasą, interfejsem lub moduł wyliczający) ma nazwę, która ma co najmniej trzech znaków, można użyć tej metody:  
  
```  
public void ValidateTypeName(ValidationContext context, IType type)  
{  
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)  
  {  
    context.LogError(  
      string.Format("Type name {0} is too short", type.Name),  
               "001", type);  
   }  
 }  
```  
  
 Zobacz [Programowanie przy użyciu interfejsu API UML](../modeling/programming-with-the-uml-api.md) informacji o metodach i typach, można użyć do nawigacji i odczytania modelu.  
  
### <a name="about-validation-constraint-methods"></a>Sprawdzanie poprawności ograniczenia metody — informacje  
 Każde ograniczenie sprawdzania poprawności jest określone metodą o następującej postaci:  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
 [ValidationMethod(ValidationCategories.Save   
  | ValidationCategories.Menu   
  | ValidationCategories.Open)]  
public void ValidateSomething  
  (ValidationContext context, IClassifier elementToValidate)  
{...}  
```  
  
 Atrybuty i parametry każdej metody sprawdzania poprawności są następujące:  
  
|||  
|-|-|  
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Definiuje metodę jako ograniczenie walidacji za pomocą Managed Extensibility Framework (MEF).|  
|`[ValidationMethod (ValidationCategories.Menu)]`|Określa, kiedy będzie można przeprowadzić walidacji. Użyj wartości logicznej lub (&#124;) Jeśli chcesz połączyć więcej niż jedną opcję.<br /><br /> `Menu` = wywoływany przez menu sprawdzania poprawności.<br /><br /> `Save` = wywoływana przy zapisywaniu modelu.<br /><br /> `Open` = wywoływana na otwieranie modelu. `Load` = wywoływana przy zapisywaniu modelu, ale z powodu naruszenia ostrzega użytkownika że może nie być możliwe ponownie otworzyć model. Wywoływany także w czasie ładowania, zanim model jest analizowany.|  
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|Zamień drugi parametr `IElement` przez typ elementu, do której chcesz zastosować ograniczenie. Metoda ograniczenia zostanie wywołana na wszystkie elementy w określonym typie.<br /><br /> Nazwa metody jest nieważna.|  
  
 Można zdefiniować dowolną liczbę metod sprawdzania poprawności, jak chcesz, z różnymi typami w drugim parametrze. Podczas sprawdzania poprawności, każda metoda sprawdzania poprawności będzie wywoływana dla każdego elementu modelu, który jest zgodny z typem parametru.  
  
### <a name="reporting-validation-errors"></a>Raportowanie błędów sprawdzania poprawności  
 Aby utworzyć raport o błędzie, należy użyć metod dostarczonych przez `ValidationContext`:  
  
 `context.LogError("error string", errorCode, elementsWithError);`  
  
- `"error string"` pojawia się w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lista błędów  
  
- `errorCode` jest ciągiem, który powinien być unikatowy identyfikator tego błędu  
  
- `elementsWithError` identyfikuje elementy w modelu. Gdy użytkownik kliknie dwukrotnie raport o błędach, zostanie wybrany kształt reprezentujący ten element.  
  
  `LogError(),` `LogWarning()` i `LogMessage()` umieszczają wiadomości w różnych sekcjach listy błędów.  
  
## <a name="how-validation-methods-are-applied"></a>Jak są stosowane metody sprawdzania poprawności  
 Sprawdzanie poprawności jest stosowana do każdego elementu w modelu, w tym relacji i części większych elementy, takie jak atrybuty klasy i parametry operacji.  
  
 Każda metoda sprawdzania poprawności są stosowane do każdego elementu, który jest zgodny z typem określonym w drugim parametrem. Oznacza to, że na przykład po zdefiniowaniu metody sprawdzania poprawności z drugim parametrem `IUseCase` i drugi z jego nadtypów `IElement`, a następnie obie te metody zostaną zastosowane do każdego przypadku użycia w modelu.  
  
 Hierarchia typów jest podsumowywana w [typy elementów modelu UML](../modeling/uml-model-element-types.md).  
  
 Można również dostęp do elementów poprzez następujące relacje. Na przykład, jeśli potrzeba zdefiniowania metody sprawdzania poprawności na `IClass`, można przejść przez jej własne właściwości:  
  
```  
public void ValidateTypeName(ValidationContext context, IClass c)  
{  
   foreach (IProperty property in c.OwnedAttributes)  
   {  
       if (property.Name.Length < 3)  
       {  
            context.LogError(  
                 string.Format(  
                        "Property name {0} is too short",   
                        property.Name),   
                 "001", property);  
        }  
   }  
}  
```  
  
### <a name="creating-a-validation-method-on-the-model"></a>Tworzenie metody sprawdzania poprawności na modelu  
 Jeśli chcesz upewnić się, że metody sprawdzania poprawności jest wywoływana, dokładnie tak, gdy podczas każdego przebiegu walidacji, można sprawdzić poprawność `IModel`:  
  
```  
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  foreach (IElement element in model.OwnedElements)  
   { ...  
```  
  
### <a name="validating-shapes-and-diagrams"></a>Sprawdzanie poprawności kształtów i diagramów  
 Metody sprawdzania poprawności nie są wywoływane na wyświetlanych elementach, takich jak diagramy i kształty, ponieważ podstawowym celem metody sprawdzania poprawności jest sprawdzania poprawności modelu. Ale możesz uzyskać dostęp do bieżącego diagramu korzystając z kontekstu diagramu.  
  
 W klasie sprawdzania poprawności Zadeklaruj `DiagramContext` jako właściwość importowaną:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
...  
[Import]  
public IDiagramContext DiagramContext { get; set; }  
```  
  
 W metodzie sprawdzania poprawności, można użyć `DiagramContext` dostępu do bieżącego diagramu fokus, jeśli istnieje:  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;  
  if (focusDiagram != null)  
  {  
    foreach (IShape<IUseCase> useCaseShape in  
              focusDiagram.GetChildShapes<IUseCase>())  
    { ...  
```  
  
 Aby zarejestrować błąd, musisz uzyskać element modelu, który reprezentuje kształt, ponieważ nie można przekazać kształtu do `LogError`:  
  
```  
IUseCase useCase = useCaseShape.Element;  
context.LogError(... , usecase);  
```  
  
### <a name="ContextCache"></a> Koordynowanie wielokrotnego sprawdzania poprawności  
 Podczas sprawdzania poprawności, na przykład przez użytkownika menu wykresu, każda metoda sprawdzania poprawności ma zastosowanie do każdego elementu modelu. Oznacza to, że w pojedynczej grupy wywołanie RAM sprawdzania poprawności, tę samą metodę można stosować wiele razy do różnych elementów.  
  
 Stanowi to problem dla sprawdzanie poprawności, które zajmuje się relacją między elementami. Na przykład można napisać sprawdzanie poprawności, które zaczyna się, powiedzmy, przypadek użycia i sprawdzić **obejmują** relacje, aby zweryfikować, że nie istnieją żadne pętle. Ale kiedy metoda jest stosowana do każdego przypadku użycia w modelu, który ma wiele **obejmują** łącza, prawdopodobnie będzie wielokrotnie przetwarzać te same obszary modelu.  
  
 Aby uniknąć tej sytuacji, istnieje pamięć podręczna kontekstu, w którym jest przechowywana informacja podczas uruchomienia sprawdzania poprawności. Służy do przekazywania informacji między różnymi wykonaniami metody sprawdzania poprawności. Można na przykład przechowywać listę elementów, które zostały już omówione w tym przebiegu weryfikacji. Pamięć podręczna jest tworzona na początku każdego przebiegu weryfikacji i nie można używać do przekazywania informacji między różne procesy sprawdzania poprawności.  
  
|||  
|-|-|  
|`context.SetCacheValue<T> (name, value)`|Wartość Store|  
|`context.TryGetCacheValue<T> (name, out value)`|Pobierz wartość. Zwraca wartość PRAWDA, jeśli to się powiedzie.|  
|`context.GetValue<T>(name)`|Pobierz wartość.|  
|`Context.GetValue<T>()`|Pobierz wartość określonego typu.|  
  
## <a name="Installing"></a> Instalowanie i odinstalowywanie rozszerzenia  
 Możesz zainstalować [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozszerzenie zarówno na swoim komputerze, jak i na innych komputerach.  
  
#### <a name="to-install-an-extension"></a>Aby zainstalować rozszerzenie  
  
1. Na komputerze, należy znaleźć **.vsix** pliku, który został zbudowany w danym projekcie VSIX.  
  
    1. W **Eksploratora rozwiązań**, w menu skrótów projektu VSIX wybierz **Otwórz Folder w Eksploratorze Windows**.  
  
    2. Zlokalizuj plik **bin\\\*\\**_YourProject_**.vsix**  
  
2. Kopiuj **.vsix** plik na komputer docelowy, na którym chcesz zainstalować rozszerzenie. Może to być Twój własny komputer lub innej.  
  
    - Komputer docelowy musi mieć jedną z wersji [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ustawionego w **source.extension.vsixmanifest**.  
  
3. Na komputerze docelowym, otwórz **.vsix** pliku.  
  
     **Instalator rozszerzenia programu Visual Studio** otwiera i instaluje rozszerzenia.  
  
4. Uruchom lub uruchom ponownie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-uninstall-an-extension"></a>Aby odinstalować rozszerzenie  
  
1. Na **narzędzia** menu, wybierz **rozszerzenia i aktualizacje**.  
  
2. Rozwiń **zainstalowanych rozszerzeń**.  
  
3. Zaznacz rozszerzenie, a następnie wybierz **Odinstaluj**.  
  
   Rzadko wadliwe rozszerzenie nie ładuje się i tworzy raport w oknie błędów, ale nie są wyświetlane w Menedżerze rozszerzeń. W takim przypadku można usunąć rozszerzenie poprzez usunięcie pliku z następującej lokalizacji gdzie *% LocalAppData %* jest zazwyczaj *DriveName*: \Users\\*nazwyużytkownika*\AppData\Local:  
  
   *% LocalAppData %* **\Microsoft\VisualStudio\\\Extensions [wersja]**  
  
## <a name="Example"></a> Przykład  
 W tym przykładzie wyszukuje pętli w relacji zależności między elementami.  
  
 Będzie sprawdzać poprawność zarówno na zapisu i polecenia menu sprawdzania poprawności.  
  
```  
/// <summary>  
/// Verify that there are no loops in the dependency relationsips.  
/// In our project, no element should be a dependent of itself.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">Element to start validation from.</param>  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu   
     | ValidationCategories.Save | ValidationCategories.Open)]  
public void NoDependencyLoops(ValidationContext context, INamedElement element)  
{  
    // The validation framework will call this method  
    // for every element in the model. But when we follow  
    // the dependencies from one element, we will validate others.  
    // So we keep a list of the elements that we don't need to validate again.   
    // The list is kept in the context cache so that it is passed  
    // from one execution of this method to another.  
    List<INamedElement> alreadySeen = null;  
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))  
    {  
       alreadySeen = new List<INamedElement>();  
       context.SetCacheValue("No dependency loops", alreadySeen);  
    }  
  
    NoDependencyLoops(context, element,   
                new INamedElement[0], alreadySeen);      
}  
  
/// <summary>  
/// Log an error if there is any loop in the dependency relationship.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">The element to be validated.</param>  
/// <param name="dependants">Elements we've followed in this recursion.</param>  
/// <param name="alreadySeen">Elements that have already been validated.</param>  
/// <returns>true if no error was detected</returns>  
private bool NoDependencyLoops(ValidationContext context,   
    INamedElement element, INamedElement[] dependants,   
    List<INamedElement> alreadySeen)  
{  
    if (dependants.Contains(element))  
    {  
        context.LogError(string.Format("{0} should not depend on itself", element.Name),   
        "Fabrikam.UML.NoGenLoops", // unique code for this error  
        dependants.SkipWhile(e => e != element).ToArray());   
            // highlight elements that are in the loop  
        return false;  
    }  
    INamedElement[] dependantsPlusElement =   
        new INamedElement[dependants.Length + 1];  
    dependants.CopyTo(dependantsPlusElement, 0);  
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;  
  
    if (alreadySeen.Contains(element))  
    {  
        // We have already validated this when we started   
        // from another element during this validation run.  
        return true;  
    }  
    alreadySeen.Add(element);  
  
    foreach (INamedElement supplier in element.GetDependencySuppliers())  
    {  
        if (!NoDependencyLoops(context, supplier,  
             dependantsPlusElement, alreadySeen))  
        return false;  
    }  
    return true;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie i instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md)   
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)
