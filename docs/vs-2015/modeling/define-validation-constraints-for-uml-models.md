---
title: Definiowanie ograniczeń walidacji dla modeli UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 32f249b971e8a37bc5b596203cde6bc7b0bcf6f1
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849741"
---
# <a name="define-validation-constraints-for-uml-models"></a>Definiowanie ograniczeń walidacji dla modeli UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zdefiniować ograniczenia walidacji, które sprawdzają, czy model spełnia określony warunek. Na przykład można zdefiniować ograniczenie, aby upewnić się, że użytkownik nie tworzy pętli relacji dziedziczenia. To ograniczenie jest wywoływane, gdy użytkownik próbuje otworzyć lub zapisać model i może być również wywoływana ręcznie. Jeśli ograniczenie nie powiedzie się, zostanie dodany komunikat o błędzie do okna błędu. Można spakować te ograniczenia do rozszerzenia integracji programu Visual Studio ([VSIX](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)) i rozpowszechnić je innym użytkownikom programu Visual Studio.

 Można także definiować ograniczenia, które weryfikują model względem zasobów zewnętrznych, takich jak bazy danych. Jeśli chcesz sprawdzić poprawność kodu programu na diagramie warstwowym, zobacz [Dodawanie niestandardowej weryfikacji architektury do diagramów warstwowych](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 Aby sprawdzić, które wersje programu Visual Studio obsługują modele UML, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="requirements"></a>Wymagania
 Zobacz [wymagania](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="applying-validation-constraints"></a>Stosowanie ograniczeń walidacji
 Ograniczenia walidacji są stosowane w trzech przypadkach: podczas zapisywania modelu; Po otwarciu modelu; a po kliknięciu przycisku **Weryfikuj model UML** w menu **Architektura** . W każdym przypadku zostaną zastosowane tylko te ograniczenia, które zostały zdefiniowane dla tego przypadku, chociaż zwykle zdefiniujesz każde ograniczenie do zastosowania w więcej niż jednym przypadku.

 Błędy walidacji są raportowane w oknie błędy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i można kliknąć dwukrotnie błąd, aby wybrać elementy modelu z błędami.

 Aby uzyskać więcej informacji na temat stosowania walidacji, zobacz [Validate The UML model](../modeling/validate-your-uml-model.md).

## <a name="defining-a-validation-extension"></a>Definiowanie rozszerzenia walidacji
 Aby utworzyć rozszerzenie sprawdzania poprawności dla projektanta UML, należy utworzyć klasę, która definiuje ograniczenia walidacji, i osadzić klasę w rozszerzeniu integracji programu Visual Studio (VSIX). VSIX działa jako kontener, który może zainstalować ograniczenie. Istnieją dwie alternatywne metody definiowania rozszerzenia walidacji:

- **Utwórz rozszerzenie walidacji w swoim własnym VSIX przy użyciu szablonu projektu.** To jest szybka metoda. Użyj go, jeśli nie chcesz łączyć ograniczeń walidacji z innymi typami rozszerzeń, takimi jak polecenia menu, niestandardowe elementy przybornika lub programy obsługi gestów. Można zdefiniować kilka ograniczeń w jednej klasie.

- **Utwórz oddzielną klasę walidacji i projekty VSIX.** Użyj tej metody, jeśli chcesz połączyć kilka typów rozszerzeń z tym samym VSIX. Na przykład, jeśli polecenie menu oczekuje modelu do przestrzegania określonych ograniczeń, można osadzić je w tym samym VSIX jako metodę sprawdzania poprawności.

#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>Aby utworzyć rozszerzenie sprawdzania poprawności we własnym VSIX

1. W oknie dialogowym **Nowy projekt** w obszarze **projekty modelowania**wybierz pozycję **rozszerzenie sprawdzania poprawności**.

2. Otwórz plik **CS** w nowym projekcie i zmodyfikuj klasę, aby zaimplementować ograniczenie walidacji.

    Aby uzyskać więcej informacji, zobacz [ocenianie ograniczenia walidacji](#Implementing).

   > [!IMPORTANT]
   > Upewnij się, że pliki **. cs** zawierają następujące instrukcje `using`:
   >
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

3. Możesz dodać dodatkowe ograniczenia, definiując nowe metody. Aby zidentyfikować metodę jako metodę walidacji, należy ją oznaczyć przy użyciu atrybutów w taki sam sposób jak początkowa Metoda walidacji.

4. Przetestuj ograniczenia, naciskając klawisz F5. Aby uzyskać więcej informacji, zobacz [wykonywanie ograniczenia walidacji](#Executing).

5. Zainstaluj polecenie menu na innym komputerze przez skopiowanie pliku **bin\\\*\\\*. vsix** skompilowanego przez projekt. Aby uzyskać więcej informacji, zobacz [Instalowanie i odinstalowywanie rozszerzenia](#Installing).

   Po dodaniu innych plików **CS** zwykle wymagane są następujące instrukcje `using`:

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Uml.Classes;

```

 Oto alternatywna procedura:

#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>Aby utworzyć oddzielne ograniczenie walidacji w projekcie biblioteki klas

1. Utwórz projekt biblioteki klas, dodając go do istniejącego rozwiązania VSIX lub tworząc nowe rozwiązanie.

    1. W menu **plik** wybierz polecenie **Nowy**, **projekt**.

    2. W obszarze **zainstalowane szablony**rozwiń **pozycję C# Wizualizacja** lub **Visual Basic**, a następnie w środkowej kolumnie Wybierz pozycję **Biblioteka klas**.

2. Chyba że rozwiązanie zawiera już jeden, Utwórz projekt VSIX:

    1. W **Eksplorator rozwiązań**, w menu skrótów rozwiązania, wybierz **Dodaj**, **Nowy projekt**.

    2. W obszarze **zainstalowane szablony**rozwiń **pozycję C# Wizualizacja** lub **Visual Basic**, a następnie wybierz pozycję **rozszerzalność**. W środkowej kolumnie kliknij pozycję **Projekt VSIX**.

3. Ustaw projekt VSIX jako projekt startowy rozwiązania.

    - W Eksplorator rozwiązań, w menu skrótów projektu VSIX, wybierz **Ustaw jako projekt startowy**.

4. W obszarze **source. Extension. vsixmanifest**w obszarze **zawartość**Dodaj projekt biblioteki klas jako składnik MEF:

    1. Na karcie **metadane** Ustaw nazwę VSIX.

    2. Na karcie **Instalowanie obiektów docelowych** Ustaw wersje programu Visual Studio jako elementy docelowe.

    3. Na karcie **zasoby** wybierz pozycję **Nowy**, a następnie w oknie dialogowym Ustaw wartość:

         **Typ** = **składnik MEF**

         **Źródło** = **projektu w bieżącym rozwiązaniu**

         **Projekt** = *projektu biblioteki klas*

#### <a name="to-define-the-validation-class"></a>Aby zdefiniować klasę walidacji

1. Ta procedura nie jest potrzebna, jeśli utworzono klasę walidacji z własnym VSIX z szablonu projektu walidacji.

2. W projekcie klasy walidacji Dodaj odwołania do następujących zestawów [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]:

     `Microsoft.VisualStudio.Modeling.Sdk.[version]`

     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

     `Microsoft.VisualStudio.Uml.Interfaces`

     `System.ComponentModel.Composition`

3. Dodaj plik do projektu biblioteki klas zawierającego kod, który jest podobny do poniższego przykładu.

    - Każde ograniczenie sprawdzania poprawności jest zawarte w metodzie, która jest oznaczona określonym atrybutem. Metoda akceptuje parametr typu elementu modelu. Po wywołaniu walidacji, struktura walidacji będzie stosowała każdą metodę walidacji do każdego elementu modelu, który jest zgodny z jego typem parametru.

    - Te metody można umieścić w dowolnej klasie i przestrzeni nazw. Zmień je na preferencję.

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

## <a name="Executing"></a>Wykonywanie ograniczenia walidacji
 W celach testowych wykonaj metody walidacji w trybie debugowania.

#### <a name="to-test-the-validation-constraint"></a>Aby przetestować ograniczenie walidacji

1. Naciśnij klawisz **F5**lub w menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie**.

     Zostanie uruchomione doświadczalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

     **Rozwiązywanie problemów**: jeśli nowy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie zostanie uruchomiony:

    - Jeśli masz więcej niż jeden projekt, upewnij się, że projekt VSIX jest ustawiony jako projekt startowy rozwiązania.

    - W Eksplorator rozwiązań, w menu skrótów dla uruchamiania lub tylko projektu, wybierz **Właściwości**. W edytorze właściwości projektu wybierz kartę **debugowanie** . Upewnij się, że ciąg w polu **początkowy program zewnętrzny** jest pełną ścieżką do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zazwyczaj:

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]eksperymentalnym Otwórz lub Utwórz projekt modelowania, a następnie otwórz lub Utwórz diagram modelowania.

3. Aby skonfigurować test dla ograniczenia przykładowego podanym w poprzedniej sekcji:

    1. Otwórz diagram klas.

    2. Utwórz klasę i Dodaj dwa atrybuty, które mają taką samą nazwę.

4. W menu skrótów w dowolnym miejscu na diagramie wybierz polecenie **Weryfikuj**.

5. Wszystkie błędy w modelu będą raportowane w oknie błędy.

6. Kliknij dwukrotnie raport o błędach. Jeśli elementy wymienione w raporcie są widoczne na ekranie, zostaną wyróżnione.

     **Rozwiązywanie problemów**: Jeśli polecenie **Sprawdź poprawność** nie pojawia się w menu, upewnij się, że:

    - Projekt walidacji jest wymieniony jako składnik MEF na karcie **zasoby** w pliku **source. Extensions. manifest** w projekcie VSIX.

    - Poprawne atrybuty `Export` i `ValidationMethod` są dołączone do metod walidacji.

    - `ValidationCategories.Menu` jest zawarty w argumencie atrybutu `ValidationMethod` i składa się z innych wartości przy użyciu operatora logicznego OR (&#124;).

    - Parametry wszystkich atrybutów `Import` i `Export` są prawidłowe.

## <a name="Implementing"></a>Ocenianie ograniczenia
 Metoda walidacji powinna określać, czy ograniczenie walidacji, które ma zostać zastosowane, ma wartość PRAWDA lub FAŁSZ. W przypadku wartości true nie należy nic robić. W przypadku wartości false powinien zgłosić błąd przy użyciu metod dostarczonych przez parametr `ValidationContext`.

> [!NOTE]
> Metody sprawdzania poprawności nie powinny zmieniać modelu. Nie ma gwarancji, gdy lub w jakiej kolejności będą wykonywane ograniczenia. Jeśli konieczne jest przekazanie informacji między kolejnymi wykonaniami metody walidacji w ramach przebiegu walidacji, można użyć pamięci podręcznej kontekstu opisanej w obszarze [koordynacja wielu walidacji](#ContextCache).

 Na przykład, jeśli chcesz mieć pewność, że każdy typ (Klasa, interfejs lub moduł wyliczający) ma nazwę, która ma co najmniej trzy znaki, można użyć tej metody:

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

 Zobacz [Programowanie za pomocą interfejsu API UML,](../modeling/programming-with-the-uml-api.md) Aby uzyskać informacje o metodach i typach, których można użyć do nawigowania i odczytywania modelu.

### <a name="about-validation-constraint-methods"></a>Informacje o metodach ograniczeń walidacji
 Każde ograniczenie sprawdzania poprawności jest zdefiniowane za pomocą metody z następującej formy:

```
[Export(typeof(System.Action<ValidationContext, object>))]
 [ValidationMethod(ValidationCategories.Save
  | ValidationCategories.Menu
  | ValidationCategories.Open)]
public void ValidateSomething
  (ValidationContext context, IClassifier elementToValidate)
{...}
```

 Atrybuty i parametry każdej metody walidacji są następujące:

|||
|-|-|
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Definiuje metodę jako ograniczenie walidacji przy użyciu Managed Extensibility Framework (MEF).|
|`[ValidationMethod (ValidationCategories.Menu)]`|Określa, kiedy zostanie wykonana Walidacja. Użyj opcji bitowe lub&#124;(), jeśli chcesz połączyć więcej niż jedną opcję.<br /><br /> `Menu` = wywołane przez menu walidacji.<br /><br /> `Save` = wywołano podczas zapisywania modelu.<br /><br /> `Open` = wywołano podczas otwierania modelu. `Load` = wywołane przy zapisywaniu modelu, ale w przypadku naruszenia ostrzega użytkownika, że może nie być możliwe ponowne otwarcie modelu. Wywoływana również podczas ładowania, zanim model zostanie przeanalizowany.|
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|Zastąp drugi parametr `IElement` przez typ elementu, do którego ma zostać zastosowane ograniczenie. Metoda ograniczenia zostanie wywołana dla wszystkich elementów w określonym typie.<br /><br /> Nazwa metody jest nieważna.|

 Można zdefiniować dowolną liczbę metod walidacji, z różnymi typami w drugim parametrze. Po wywołaniu walidacji każda metoda sprawdzania poprawności zostanie wywołana dla każdego elementu modelu, który jest zgodny z typem parametru.

### <a name="reporting-validation-errors"></a>Raportowanie błędów walidacji
 Aby utworzyć raport o błędach, należy użyć metod dostarczonych przez `ValidationContext`:

 `context.LogError("error string", errorCode, elementsWithError);`

- `"error string"` pojawia się w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Lista błędów

- `errorCode` jest ciągiem, który powinien być unikatowym identyfikatorem błędu

- `elementsWithError` identyfikuje elementy w modelu. Gdy użytkownik kliknie dwukrotnie raport o błędach, zostanie wybrany kształt reprezentujący ten element.

  `LogError(),` `LogWarning()` i `LogMessage()` umieścić komunikaty w różnych sekcjach listy błędów.

## <a name="how-validation-methods-are-applied"></a>Jak są stosowane metody walidacji
 Walidacja jest stosowana do każdego elementu w modelu, w tym relacji i części większych elementów, takich jak atrybuty klasy i parametrów operacji.

 Każda metoda sprawdzania poprawności jest stosowana do każdego elementu, który jest zgodny z typem w drugim parametrze. Oznacza to, że na przykład, jeśli zdefiniujesz metodę walidacji z drugim parametrem `IUseCase` i drugim z jego nadtype `IElement`, obie te metody zostaną zastosowane do każdego przypadku użycia w modelu.

 Hierarchia typów jest podsumowywana w [typach elementów modelu UML](../modeling/uml-model-element-types.md).

 Możesz również uzyskać dostęp do elementów przez następujące relacje. Na przykład w przypadku zdefiniowania metody sprawdzania poprawności na `IClass`można zapętlić się swoimi właściwościami:

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

### <a name="creating-a-validation-method-on-the-model"></a>Tworzenie metody walidacji w modelu
 Jeśli chcesz mieć pewność, że metoda walidacji jest wywoływana dokładnie raz podczas każdego przebiegu walidacji, można sprawdzić poprawność `IModel`:

```
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{  foreach (IElement element in model.OwnedElements)
   { ...
```

### <a name="validating-shapes-and-diagrams"></a>Sprawdzanie poprawności kształtów i diagramów
 Metody walidacji nie są wywoływane na elementach wyświetlanych, takich jak diagramy i kształty, ponieważ głównym celem metod sprawdzania poprawności jest sprawdzenie poprawności modelu. Ale dostęp do bieżącego diagramu można uzyskać przy użyciu kontekstu diagramu.

 W klasie walidacji Zadeklaruj `DiagramContext` jako zaimportowaną Właściwość:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
...
[Import]
public IDiagramContext DiagramContext { get; set; }
```

 W metodzie walidacji można użyć `DiagramContext`, aby uzyskać dostęp do bieżącego diagramu fokusu, jeśli istnieje:

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

 Aby zarejestrować błąd, należy uzyskać element modelu, który reprezentuje kształt, ponieważ nie można przekazać kształtu do `LogError`:

```
IUseCase useCase = useCaseShape.Element;
context.LogError(... , usecase);
```

### <a name="ContextCache"></a>Koordynowanie wielu walidacji
 Po wywołaniu walidacji, na przykład przez użytkownika z menu diagramu, każda metoda sprawdzania poprawności jest stosowana do każdego elementu modelu. Oznacza to, że w pojedynczym wywołaniu struktury walidacji ta sama metoda może być stosowana wiele razy do różnych elementów.

 Jest to problem dotyczący walidacji, które zajmują się relacjami między elementami. Można na przykład napisać walidację, która zaczyna się od, powiedzmy, przypadek użycia i przechodzą relacje **include** , aby sprawdzić, czy nie ma żadnych pętli. Ale jeśli metoda jest stosowana do każdego przypadku użycia w modelu, który ma wiele linków **dołączania** , prawdopodobnie wielokrotnie przetwarza te same obszary modelu.

 Aby uniknąć tej sytuacji, istnieje pamięć podręczna kontekstu, w której informacje są zachowywane podczas przebiegu walidacji. Można jej użyć do przekazywania informacji między różnymi wykonaniami metod walidacji. Na przykład można przechowywać listę elementów, które zostały już omówione w ramach tego przebiegu walidacji. Pamięć podręczna jest tworzona na początku każdego przebiegu walidacji i nie może służyć do przekazywania informacji między różnymi przebiegami walidacji.

|||
|-|-|
|`context.SetCacheValue<T> (name, value)`|Przechowywanie wartości|
|`context.TryGetCacheValue<T> (name, out value)`|Pobierz wartość. Zwraca wartość true, jeśli powodzenie.|
|`context.GetValue<T>(name)`|Pobierz wartość.|
|`Context.GetValue<T>()`|Pobierz wartość określonego typu.|

## <a name="Installing"></a>Instalowanie i odinstalowywanie rozszerzenia
 Rozszerzenie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] można zainstalować zarówno na swoim komputerze, jak i na innych komputerach.

#### <a name="to-install-an-extension"></a>Aby zainstalować rozszerzenie

1. Na komputerze Znajdź plik **. vsix** , który został skompilowany przez projekt VSIX.

    1. W **Eksplorator rozwiązań**, w menu skrótów projektu VSIX, wybierz polecenie **Otwórz folder w Eksploratorze Windows**.

    2. Zlokalizuj plik **bin\\\*\\** _YourProject_ **. vsix**

2. Skopiuj plik **. vsix** do komputera docelowego, na którym chcesz zainstalować rozszerzenie. Może to być własny komputer lub inny.

    - Komputer docelowy musi mieć jedną z wersji [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] określonych w elemencie **source. Extension. vsixmanifest**.

3. Na komputerze docelowym otwórz plik **. vsix** .

     Zostanie otwarty **Instalator rozszerzenia programu Visual Studio** , który zainstaluje rozszerzenie.

4. Uruchom lub Uruchom ponownie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Aby odinstalować rozszerzenie

1. W menu **Narzędzia** wybierz pozycję **rozszerzenia i aktualizacje**.

2. Rozwiń **zainstalowane rozszerzenia**.

3. Wybierz rozszerzenie, a następnie wybierz **Odinstaluj**.

   Rzadko błędne rozszerzenie nie zostanie załadowane i tworzy raport w oknie błędu, ale nie jest wyświetlany w Menedżerze rozszerzeń. W takim przypadku można usunąć rozszerzenie, usuwając plik z następującej lokalizacji, gdzie *% LocalAppData%* jest zazwyczaj *dysk*: \Users\\*username*\AppData\Local:

   *% LocalAppData%* **\Microsoft\VisualStudio\\[wersja] \Extensions**

## <a name="Example"></a>Przyklad
 Ten przykład odnajduje pętle w relacji zależności między elementami.

 Zostanie zweryfikowane zarówno przy zapisie, jak i w menu walidacji.

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
 [Definiowanie i Instalowanie programowania rozszerzeń modelowania](../modeling/define-and-install-a-modeling-extension.md) [przy użyciu interfejsu API UML](../modeling/programming-with-the-uml-api.md)
