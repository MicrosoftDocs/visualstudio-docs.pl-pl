---
title: Sprawdzanie poprawności w języku specyficznym dla domeny
description: Dowiedz się, jak zdefiniować ograniczenia weryfikacji, aby sprawdzić, czy model utworzony przez użytkownika ma znaczenie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6de3a8940c845b29d2d0c7454b7c585f4676dba0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388337"
---
# <a name="validation-in-a-domain-specific-language"></a>Sprawdzanie poprawności w języku specyficznym dla domeny
Jako autor języka specyficznego dla domeny (DSL) możesz zdefiniować ograniczenia weryfikacji, aby sprawdzić, czy model utworzony przez użytkownika ma znaczenie. Jeśli na przykład dsl umożliwia użytkownikom rysowanie drzewa rodziny osób i ich nadrzędnych, można napisać ograniczenie, które zapewnia, że dzieci mają daty urodzenia po ich rodziców.

 Ograniczenia weryfikacji mogą być wykonywane podczas zapisania modelu, jego otwarcia i jawnego wykonania przez użytkownika polecenia menu **Weryfikuj.** Walidację można również wykonać pod kontrolą programu. Na przykład można wykonać walidację w odpowiedzi na zmianę wartości właściwości lub relacji.

 Walidacja jest szczególnie ważna w przypadku pisania szablonów tekstowych lub innych narzędzi, które przetwarzają modele użytkowników. Walidacja zapewnia, że modele spełniają warunki wstępne zakładane przez te narzędzia.

> [!WARNING]
> Możesz również zezwolić na zdefiniowane ograniczenia weryfikacji w oddzielnych rozszerzeniach dsl, a także polecenia menu rozszerzenia i programy obsługi gestów. Użytkownicy mogą zainstalować te rozszerzenia oprócz DSL. Aby uzyskać więcej informacji, zobacz [Rozszerzanie DSL przy użyciu MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="running-validation"></a>Uruchamianie walidacji
 Gdy użytkownik edytuje model, czyli wystąpienie języka specyficznego dla domeny, następujące akcje mogą uruchomić walidację:

- Kliknij prawym przyciskiem myszy diagram i wybierz polecenie **Weryfikuj wszystko.**

- Kliknij prawym przyciskiem myszy górny węzeł w Eksploratorze DSL i wybierz polecenie **Sprawdź poprawność wszystkich**

- Zapisz model.

- Otwórz model.

- Ponadto można napisać kod programu, który uruchamia walidację, na przykład jako część polecenia menu lub w odpowiedzi na zmianę.

  Wszelkie błędy walidacji zostaną wyświetlone w **oknie Lista** błędów. Użytkownik może kliknąć dwukrotnie komunikat o błędzie, aby wybrać elementy modelu, które są przyczyną błędu.

## <a name="defining-validation-constraints"></a>Definiowanie ograniczeń walidacji
 Ograniczenia weryfikacji definiuje się przez dodanie metod walidacji do klas domeny lub relacji DSL. Po uruchomieniu walidacji przez użytkownika lub pod kontrolą programu są wykonywane niektóre lub wszystkie metody weryfikacji. Każda metoda jest stosowana do każdego wystąpienia jej klasy i w każdej klasie może być kilka metod weryfikacji.

 Każda metoda walidacji zgłasza wszelkie znalezione błędy.

> [!NOTE]
> Metody walidacji zgłaszają błędy, ale nie zmieniają modelu. Jeśli chcesz dostosować lub zapobiec niektórym zmianom, zobacz [Alternatywy dla walidacji](#alternatives).

#### <a name="to-define-a-validation-constraint"></a>Aby zdefiniować ograniczenie walidacji

1. Włącz walidację w **węźle Editor\Validation:**

   1. Otwórz **dsl\DslDefinition.dsl.**

   2. W Eksploratorze DSL rozwiń węzeł **Edytor** i wybierz pozycję **Walidacja.**

   3. W oknie okno Właściwości właściwości **Uses**  (Używa) na wartość `true` . Najdogodniej jest ustawić wszystkie te właściwości.

   4. Kliknij **pozycję Przekształć wszystkie** szablony na **Eksplorator rozwiązań** narzędzi.

2. Napisz definicje klas częściowych dla co najmniej jednej klasy domeny lub relacji domeny. Zapisz te definicje w nowym pliku kodu w **projekcie Dsl.**

3. Poprzedaj każdą klasę tym atrybutem:

   ```csharp
   [ValidationState(ValidationState.Enabled)]
   ```

   - Domyślnie ten atrybut umożliwia również weryfikację klas pochodnych. Jeśli chcesz wyłączyć walidację dla określonej klasy pochodnej, możesz użyć metody `ValidationState.Disabled` .

4. Dodaj metody walidacji do klas. Każda metoda weryfikacji może mieć dowolną nazwę, ale ma jeden parametr typu <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext> .

    Musi ona być poprzedzona co najmniej jednym `ValidationMethod` atrybutem:

   ```csharp
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
   ```

    ValidationCategories określ, kiedy jest wykonywana metoda.

   Na przykład:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;

// Allow validation methods in this class:
[ValidationState(ValidationState.Enabled)]
// In this DSL, ParentsHaveChildren is a domain relationship
// from Person to Person:
public partial class ParentsHaveChildren
{
  // Identify the method as a validation method:
  [ValidationMethod
  ( // Specify which events cause the method to be invoked:
    ValidationCategories.Open // On file load.
  | ValidationCategories.Save // On save to file.
  | ValidationCategories.Menu // On user menu command.
  )]
  // This method is applied to each instance of the
  // type (and its subtypes) in a model:
  private void ValidateParentBirth(ValidationContext context)
  {
    // In this DSL, the role names of this relationship
    // are "Child" and "Parent":
     if (this.Child.BirthYear < this.Parent.BirthYear
        // Allow user to leave the year unset:
        && this.Child.BirthYear != 0)
      {
        context.LogError(
             // Description:
                       "Child must be born after Parent",
             // Unique code for this error:
                       "FAB001ParentBirthError",
              // Objects to select when user double-clicks error:
                       this.Child,
                       this.Parent);
    }
  }
```

 Zwróć uwagę na następujące kwestie dotyczące tego kodu:

- Metody walidacji można dodać do klas domeny lub relacji domeny. Kod dla tych typów znajduje się w **katalogu Dsl\Generated Code\Domain \* .cs**.

- Każda metoda walidacji jest stosowana do każdego wystąpienia jej klasy i jej podklas. W przypadku relacji domeny każde wystąpienie jest łączem między dwoma elementami modelu.

- Metody walidacji nie są stosowane w określonej kolejności, a każda metoda nie jest stosowana do wystąpień jej klasy w dowolnej przewidywalnej kolejności.

- Zaktualizowanie zawartości sklepu jest zwykle złym rozwiązaniem w przypadku metody weryfikacji, ponieważ może to prowadzić do niespójnych wyników. Zamiast tego metoda powinna zgłosić dowolny błąd, wywołując `context.LogError` metodę lub `LogWarning` `LogInfo` .

- W wywołaniu LogError możesz podać listę elementów modelu lub linków relacji, które zostaną wybrane, gdy użytkownik kliknie dwukrotnie komunikat o błędzie.

- Aby uzyskać informacje na temat odczytywania modelu w kodzie programu, zobacz [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md)(Nawigowanie i aktualizowanie modelu w kodzie programu).

  Przykład dotyczy następującego modelu domeny. Relacja ParentHave Nie ma ról o nazwach Child i Parent.

  ![Diagram definicji DSL &#45; modelu drzewa rodziny](../modeling/media/familyt_person.png)

## <a name="validation-categories"></a>Kategorie weryfikacji
 W <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> atlicie określasz, kiedy należy wykonać metodę weryfikacji.

|Kategoria|Wykonanie|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy użytkownik wywołuje polecenie menu Weryfikuj.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Po otwarciu pliku modelu.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Po zapisaniu pliku. Jeśli występują błędy walidacji, użytkownik będzie miał możliwość anulowania operacji zapisywania.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Po zapisaniu pliku. Jeśli w tej kategorii występują błędy metod, użytkownik jest ostrzegany, że ponowne otwarcie pliku może nie być możliwe.<br /><br /> Użyj tej kategorii dla metod weryfikacji, które testuje zduplikowane nazwy lub identyfikatory albo inne warunki, które mogą powodować błędy ładowania.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy wywoływana jest metoda ValidateCustom. Walidacje w tej kategorii mogą być wywoływane tylko z kodu programu.<br /><br /> Aby uzyskać więcej informacji, zobacz [Niestandardowe kategorie weryfikacji](#custom).|

## <a name="where-to-place-validation-methods"></a>Gdzie umieścić metody weryfikacji
 Ten sam efekt można często osiągnąć, umieszczając metodę weryfikacji na innym typie. Na przykład można dodać metodę do klasy Person zamiast relacji ParentsHave Niezależność i iterować po linkach:

```
[ValidationState(ValidationState.Enabled)]
public partial class Person
{[ValidationMethod
 ( ValidationCategories.Open
 | ValidationCategories.Save
 | ValidationCategories.Menu
 )
]
  private void ValidateParentBirth(ValidationContext context)
  {
    // Iterate through ParentHasChildren links:
    foreach (Person parent in this.Parents)
    {
        if (this.BirthYear <= parent.BirthYear)
        { ...
```

 **Agregowanie ograniczeń walidacji.** Aby zastosować walidację w przewidywalnej kolejności, zdefiniuj pojedynczą metodę weryfikacji dla klasy właściciela, taką jak element główny modelu. Ta technika umożliwia również agregowanie wielu raportów o błędach w jeden komunikat.

 Wadą jest to, że połączona metoda jest mniej łatwa do zarządzania i że wszystkie ograniczenia muszą mieć taki sam typ `ValidationCategories` . W związku z tym zalecamy, aby w miarę możliwości zachować każde ograniczenie w oddzielnej metodzie.

 **Przekazywanie wartości w pamięci podręcznej kontekstu.** Parametr kontekstu ma słownik, w którym można umieścić dowolne wartości. Słownik jest trwały przez czas życia uruchomienia walidacji. Określonej metody weryfikacji można na przykład zachować liczbę błędów w kontekście i użyć jej w celu uniknięcia zalewania okna błędu powtórzonymi komunikatami. Na przykład:

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }
```

## <a name="validation-of-multiplicities"></a>Walidacja mnożenia
 Metody sprawdzania minimalnej liczebności są generowane automatycznie dla DSL. Kod jest zapisywany w **dsl\Generated Code\MultiplicityValidation.cs.** Te metody są stosowane po włączeniu weryfikacji w węźle **Editor\Validation** w eksploratorze DSL.

 Jeśli ustawisz liczebność roli relacji domeny na 1..* lub 1..1, ale użytkownik nie utworzy połączenia tej relacji, zostanie wyświetlony komunikat o błędzie weryfikacji.

 Jeśli na przykład DSL ma klasy Person i Town oraz relację PersonLivesInWiersz z relacją **1.. \\** * w roli miejscowość, a następnie dla każdej osoby, która nie ma miejscowości, zostanie wyświetlony komunikat o błędzie.

## <a name="running-validation-from-program-code"></a>Uruchamianie walidacji z kodu programu
 Walidację można uruchomić, korzystając z kontrolera ValidationController lub tworząc go. Jeśli chcesz, aby błędy były wyświetlane użytkownikowi w oknie błędu, użyj kontrolera ValidationController dołączonego do danych DocData diagramu. Jeśli na przykład piszesz polecenie menu, `CurrentDocData.ValidationController` polecenie jest dostępne w klasie zestawu poleceń:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
partial class MyLanguageCommandSet
{
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
  {
   ValidationController controller = this.CurrentDocData.ValidationController;
...
```

 Aby uzyskać więcej informacji, [zobacz Jak dodać polecenie do menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 Możesz również utworzyć oddzielny kontroler weryfikacji i samodzielnie zarządzać błędami. Na przykład:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
Store store = ...;
VsValidationController validator = new VsValidationController(s);
// Validate all elements in the Store:
if (!validator.Validate(store, ValidationCategories.Save))
{
  // Deal with errors:
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }
}
```

## <a name="running-validation-when-a-change-occurs"></a>Uruchamianie walidacji w przypadku wystąpienia zmiany
 Jeśli chcesz się upewnić, że użytkownik jest natychmiast ostrzegany, jeśli model stanie się nieprawidłowy, możesz zdefiniować zdarzenie magazynu, które uruchamia walidację. Aby uzyskać więcej informacji na temat zdarzeń magazynu, zobacz [Procedury obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Oprócz kodu walidacji dodaj niestandardowy plik kodu do projektu **DslPackage** z zawartością podobną do poniższego przykładu. Ten kod używa kodu `ValidationController` dołączonego do dokumentu. Ten kontroler wyświetla błędy weryfikacji na Visual Studio błędów.

```csharp
using System;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
namespace Company.FamilyTree
{
  partial class FamilyTreeDocData // Change name to your DocData.
  {
    // Register the store event handler:
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded();
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(ParentsHaveChildren));
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(Person));
      EventManagerDirectory events = this.Store.EventManagerDirectory;
      events.ElementAdded
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));
    }
    // Handler will be called after transaction that creates a link:
    private void ParentLinkAddedHandler(object sender,
                                ElementAddedEventArgs e)
    {
      this.ValidationController.Validate(e.ModelElement,
           ValidationCategories.Save);
    }
    // Called when a link is deleted:
    private void ParentLinkDeletedHandler(object sender,
                                ElementDeletedEventArgs e)
    {
      // Don't apply validation to a deleted item!
      // - Validate store to refresh the error list.
      this.ValidationController.Validate(this.Store,
           ValidationCategories.Save);
    }
    // Called when any property of a Person element changes:
    private void BirthDateChangedHandler(object sender,
                      ElementPropertyChangedEventArgs e)
    {
      Person person = e.ModelElement as Person;
      // Not interested in changes in other properties:
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)
          return;

      // Validate all parent links to and from the person:
      this.ValidationController.Validate(
        ParentsHaveChildren.GetLinksToParents(person)
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))
        , ValidationCategories.Save);
    }
  }
}
```

 Programy obsługi są również wywoływane po operacjach Cofnij lub Ponownie wywołuj, które mają wpływ na linki lub elementy.

## <a name="custom-validation-categories"></a><a name="custom"></a> Niestandardowe kategorie weryfikacji
 Oprócz standardowych kategorii weryfikacji, takich jak Menu i Otwórz, można zdefiniować własne kategorie. Te kategorie można wywoływać z kodu programu. Użytkownik nie może wywołać ich bezpośrednio.

 Typowym zastosowaniem kategorii niestandardowych jest zdefiniowanie kategorii, która sprawdza, czy model spełnia warunki wstępne określonego narzędzia.

 Aby dodać metodę weryfikacji do określonej kategorii, poprzedaj ją atrybutem w ten sposób:

```csharp
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]
[ValidationMethod(ValidationCategory.Menu)]
private void TestForCircularLinks(ValidationContext context)
{...}
```

> [!NOTE]
> Możesz dodać do metody prefiks o tylu `[ValidationMethod()]` atrybutach, ile chcesz. Metodę można dodać do kategorii niestandardowych i standardowych.

 Aby wywołać weryfikację niestandardową:

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

## <a name="alternatives-to-validation"></a><a name="alternatives"></a> Alternatywy dla walidacji
 Ograniczenia walidacji zgłaszają błędy, ale nie zmieniają modelu. Jeśli zamiast tego chcesz zapobiec unieważnieniu modelu, możesz użyć innych technik.

 Jednak te techniki nie są zalecane. Zazwyczaj lepiej jest pozwolić użytkownikowi zdecydować, jak poprawić nieprawidłowy model.

 **Dostosuj zmianę, aby przywrócić poprawność modelu.** Jeśli na przykład użytkownik ustawia właściwość powyżej dozwolonej wartości maksymalnej, można zresetować właściwość do wartości maksymalnej. W tym celu zdefiniuj regułę. Aby uzyskać więcej informacji, zobacz [Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

 **Wycofaj transakcję, jeśli podjęto próbę nieprawidłowej zmiany.** W tym celu można również zdefiniować regułę, ale w niektórych przypadkach można przesłonić program obsługi właściwości **OnValueChanging()** lub przesłonić metodę, taką jak Aby wycofać transakcję. Aby uzyskać więcej informacji, zobacz Obsługa zmian wartości właściwości `OnDeleted().` `this.Store.TransactionManager.CurrentTransaction.Rollback().` [domeny](../modeling/domain-property-value-change-handlers.md).

> [!WARNING]
> Upewnij się, że użytkownik wie, że zmiana została dostosowana lub wycofana. Na przykład użyj `System.Windows.Forms.MessageBox.Show("message").`

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Programy obsługi zdarzeń propagujące zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md)
