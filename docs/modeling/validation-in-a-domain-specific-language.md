---
title: Sprawdzanie poprawności w języku specyficznym dla domeny
description: Dowiedz się, jak definiować ograniczenia walidacji, aby sprawdzić, czy model utworzony przez użytkownika ma znaczenie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb9baced0a4cc38ae175146d3f3779c5b9c28dd2
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362538"
---
# <a name="validation-in-a-domain-specific-language"></a>Sprawdzanie poprawności w języku specyficznym dla domeny
Jako autor języka specyficznego dla domeny (DSL) można zdefiniować ograniczenia sprawdzania poprawności, aby sprawdzić, czy model utworzony przez użytkownika ma znaczenie. Jeśli na przykład linia DSL umożliwia użytkownikom rysowanie drzewa rodzin osób i ich przodków, można napisać ograniczenie, które zapewnia, że dzieci mają daty urodzenia po nadrzędnych.

 Ograniczenia walidacji można wykonać, gdy model zostanie zapisany, gdy zostanie on otwarty, a użytkownik jawnie uruchamia polecenie **walidacji** menu. Możesz również wykonać walidację w obszarze kontrola programu. Można na przykład wykonać walidację w odpowiedzi na zmianę wartości właściwości lub relacji.

 Walidacja jest szczególnie ważna w przypadku pisania szablonów tekstowych lub innych narzędzi, które przetwarzają modele użytkowników. Sprawdzanie poprawności zapewnia, że modele spełniają warunki wstępne przyjęte przez te narzędzia.

> [!WARNING]
> Można również zezwolić na definiowanie ograniczeń walidacji w osobnych rozszerzeniach dla DSL oraz poleceń menu rozszerzenia i programów obsługi gestów. Użytkownicy mogą zdecydować się na zainstalowanie tych rozszerzeń oprócz połączenia DSL. Aby uzyskać więcej informacji, zobacz sekcję "Rozpoznaj [swój DSL" przy użyciu MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="running-validation"></a>Uruchamianie walidacji
 Gdy użytkownik edytuje model, czyli wystąpienie języka specyficznego dla domeny, można uruchomić weryfikację następujących akcji:

- Kliknij prawym przyciskiem myszy diagram i wybierz polecenie **Weryfikuj wszystko**.

- Kliknij prawym przyciskiem myszy górny węzeł w Eksploratorze DSL i wybierz polecenie **Weryfikuj wszystko**

- Zapisz model.

- Otwórz model.

- Ponadto można napisać kod programu, który uruchamia walidację, na przykład w ramach polecenia menu lub w odpowiedzi na zmianę.

  Wszystkie błędy walidacji będą wyświetlane w oknie **Lista błędów** . Użytkownik może kliknąć dwukrotnie komunikat o błędzie, aby wybrać elementy modelu, które są przyczyną błędu.

## <a name="defining-validation-constraints"></a>Definiowanie ograniczeń walidacji
 Ograniczenia walidacji definiuje się przez dodanie metod sprawdzania poprawności do klas domen lub relacji DSL. Gdy Walidacja jest uruchamiana przez użytkownika lub w obszarze kontrola programu, niektóre lub wszystkie metody sprawdzania poprawności są wykonywane. Każda metoda jest stosowana do każdego wystąpienia klasy, a w każdej klasie może istnieć kilka metod walidacji.

 Każda metoda sprawdzania poprawności raportuje wszystkie znalezione błędy.

> [!NOTE]
> Metody walidacji raportują błędy, ale nie zmieniają modelu. Jeśli chcesz dostosować lub zablokować pewne zmiany, zobacz [alternatywy do walidacji](#alternatives).

#### <a name="to-define-a-validation-constraint"></a>Aby zdefiniować ograniczenie walidacji

1. Włącz weryfikację w węźle **Editor\Validation** :

   1. Otwórz **Dsl\DslDefinition.DSL**.

   2. W Eksploratorze DSL rozwiń węzeł **Edytor** i wybierz pozycję **Walidacja**.

   3. W okno Właściwości ustaw wartość właściwości przy **użyciu** `true` . Najlepiej ustawić wszystkie te właściwości.

   4. Kliknij pozycję **Przekształć wszystkie szablony** na pasku narzędzi **Eksplorator rozwiązań** .

2. Napisz częściowe definicje klas dla co najmniej jednej klasy domeny lub relacji domeny. Napisz te definicje w nowym pliku kodu w projekcie **DSL** .

3. Prefiks każdej klasy z tym atrybutem:

   ```csharp
   [ValidationState(ValidationState.Enabled)]
   ```

   - Domyślnie ten atrybut również włącza walidację dla klas pochodnych. Jeśli chcesz wyłączyć walidację określonej klasy pochodnej, możesz użyć `ValidationState.Disabled` .

4. Dodaj metody walidacji do klas. Każda metoda sprawdzania poprawności może mieć dowolną nazwę, ale ma jeden parametr typu <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext> .

    Musi być poprzedzony prefiksem co najmniej jednego `ValidationMethod` atrybutu:

   ```csharp
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
   ```

    ValidationCategories określa, kiedy Metoda jest wykonywana.

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

- Metody sprawdzania poprawności można dodać do klas domen lub relacji domeny. Kod dla tych typów znajduje się w **Dsl\Generated Code\Domain \* . cs**.

- Każda metoda sprawdzania poprawności jest stosowana do każdego wystąpienia klasy i jego podklas. W przypadku relacji domeny każde wystąpienie jest łączem między dwoma elementami modelu.

- Metody walidacji nie są stosowane w żadnej określonej kolejności, a każda metoda nie jest stosowana do wystąpień jej klasy w żadnej przewidywalnej kolejności.

- Zwykle jest to niewłaściwe rozwiązanie do aktualizowania zawartości magazynu przez metodę walidacji, ponieważ spowodowałoby to powstanie niespójnych wyników. Zamiast tego Metoda powinna zgłosić dowolny błąd przez wywołanie `context.LogError` `LogWarning` lub `LogInfo` .

- W wywołaniu LogError można podać listę elementów modelu lub linków relacji, które zostaną wybrane, gdy użytkownik kliknie dwukrotnie komunikat o błędzie.

- Aby uzyskać informacje o sposobie odczytywania modelu w kodzie programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Przykład dotyczy poniższego modelu domeny. Relacja ParentsHaveChildren ma role, które mają nazwy podrzędne i nadrzędne.

  ![Diagram definicji DSL &#45; Model drzewa genealogicznego](../modeling/media/familyt_person.png)

## <a name="validation-categories"></a>Kategorie walidacji
 W <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> atrybucie należy określić, kiedy ma być wykonywana metoda walidacji.

|Kategoria|Wykonanie|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy użytkownik wywołuje polecenie menu walidacji.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Po otwarciu pliku modelu.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy plik zostanie zapisany. Jeśli występują błędy walidacji, użytkownik otrzyma opcję anulowania operacji zapisywania.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy plik zostanie zapisany. W przypadku błędów z metod w tej kategorii użytkownik jest ostrzegany, że może nie być możliwe ponowne otwarcie pliku.<br /><br /> Ta kategoria służy do metod sprawdzania poprawności, które sprawdzają powielone nazwy lub identyfikatory lub inne warunki, które mogą powodować błędy ładowania.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy wywoływana jest metoda ValidateCustom. Walidacje w tej kategorii mogą być wywoływane tylko z kodu programu.<br /><br /> Aby uzyskać więcej informacji, zobacz [niestandardowe kategorie walidacji](#custom).|

## <a name="where-to-place-validation-methods"></a>Gdzie należy umieścić metody walidacji
 Ten sam efekt można osiągnąć, wprowadzając metodę walidacji innego typu. Na przykład można dodać metodę do klasy Person zamiast relacji ParentsHaveChildren i przeprowadzić iterację przez linki:

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

 **Agregowanie ograniczeń walidacji.** Aby zastosować weryfikację w przewidywalną kolejności, należy zdefiniować pojedynczą metodę sprawdzania poprawności klasy Owner, na przykład element główny modelu. Ta technika umożliwia również agregowanie wielu raportów o błędach do jednej wiadomości.

 Wadą jest to, że połączona Metoda jest mniej łatwa w zarządzaniu i że ograniczenia muszą mieć taki sam sposób `ValidationCategories` . Dlatego zalecamy zachowanie każdego ograniczenia w oddzielnym metodzie, jeśli jest to możliwe.

 **Przekazywanie wartości w pamięci podręcznej kontekstu.** Parametr kontekstowy ma słownik, w którym można umieścić dowolne wartości. Słownik zachowuje się w okresie istnienia przebiegu walidacji. Dana metoda sprawdzania poprawności może na przykład zachować liczbę błędów w kontekście i użyć jej w celu uniknięcia zapełnienia okna błędów powtarzanymi komunikatami. Na przykład:

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }
```

## <a name="validation-of-multiplicities"></a>Walidacja iloczynów
 Metody sprawdzania poprawności umożliwiające sprawdzanie liczebności minimalnej są generowane automatycznie dla DSL. Kod jest zapisywana w **Dsl\Generated Code\MultiplicityValidation.cs**. Te metody zaczną obowiązywać po włączeniu walidacji w węźle **Editor\Validation** w Eksploratorze DSL.

 Jeśli ustawisz liczebność roli relacji domeny na 1.. * lub 1.. 1, ale użytkownik nie utworzy linku do tej relacji, zostanie wyświetlony komunikat o błędzie walidacji.

 Jeśli na przykład DSL ma klasy Person i miasto, a relacja PersonLivesInTown z relacją **1.. \\** w roli miasto, a następnie dla każdej osoby, która nie ma miejscowości, zostanie wyświetlony komunikat o błędzie.

## <a name="running-validation-from-program-code"></a>Uruchamianie walidacji z kodu programu
 Można uruchomić walidację, uzyskując dostęp do lub tworząc ValidationController. Jeśli chcesz, aby błędy były wyświetlane użytkownikowi w oknie błędu, użyj ValidationController, który jest dołączony do DocData diagramu. Na przykład, jeśli piszesz polecenie menu, `CurrentDocData.ValidationController` jest dostępne w klasie zestawu poleceń:

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

 Aby uzyskać więcej informacji, zobacz [jak: Dodawanie polecenia do menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

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

## <a name="running-validation-when-a-change-occurs"></a>Uruchamianie walidacji po wystąpieniu zmiany
 Jeśli chcesz mieć pewność, że użytkownik jest ostrzegany natychmiast, jeśli model stanie się nieprawidłowy, możesz zdefiniować zdarzenie magazynu, które uruchamia walidację. Aby uzyskać więcej informacji na temat zdarzeń ze sklepu, zobacz [programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Oprócz kodu sprawdzania poprawności Dodaj niestandardowy plik kodu do projektu _ *DslPackage** o zawartości podobnej do poniższego przykładu. Ten kod używa programu `ValidationController` , który jest dołączony do dokumentu. Ten kontroler wyświetla błędy walidacji na liście błędów programu Visual Studio.

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

 Procedury obsługi są również wywoływane po wykonaniu operacji Cofnij lub wykonaj ponownie, które mają wpływ na linki lub elementy.

## <a name="custom-validation-categories"></a><a name="custom"></a> Niestandardowe kategorie walidacji
 Oprócz standardowych kategorii walidacji, takich jak menu i otwarte, można definiować własne kategorie. Można wywołać te kategorie z kodu programu. Użytkownik nie może wywoływać ich bezpośrednio.

 Typowym zastosowaniem kategorii niestandardowych jest definiowanie kategorii, która sprawdza, czy model spełnia warunki wstępne określonego narzędzia.

 Aby dodać metodę walidacji do określonej kategorii, poprzedź ją atrybutem podobnym do tego:

```csharp
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]
[ValidationMethod(ValidationCategory.Menu)]
private void TestForCircularLinks(ValidationContext context)
{...}
```

> [!NOTE]
> Można utworzyć prefiks metody z dowolną liczbą `[ValidationMethod()]` atrybutów. Można dodać metodę do kategorii niestandardowych i standardowych.

 Aby wywołać niestandardowe sprawdzanie poprawności:

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

## <a name="alternatives-to-validation"></a><a name="alternatives"></a> Alternatywy do walidacji
 Ograniczenia walidacji raportują błędy, ale nie zmieniają modelu. Jeśli zamiast tego chcesz zapobiec nieprawidłowemu modelowi, możesz użyć innych technik.

 Jednak te techniki nie są zalecane. Zwykle lepszym rozwiązaniem jest poinformowanie użytkownika o sposobie poprawienia nieprawidłowego modelu.

 **Dostosuj zmianę, aby przywrócić prawidłowość modelu.** Na przykład jeśli użytkownik ustawi właściwość powyżej dozwolone maksimum, można zresetować właściwość do wartości maksymalnej. Aby to zrobić, zdefiniuj regułę. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

 **Wycofaj transakcję, Jeśli podjęto próbę nieprawidłowej zmiany.** Dla tego celu można również zdefiniować regułę, ale w niektórych przypadkach można przesłonić procedurę obsługi właściwości **OnValueChanging ()** lub zastąpić metodę, na przykład `OnDeleted().` Aby wycofać transakcję, użyj `this.Store.TransactionManager.CurrentTransaction.Rollback().` Aby uzyskać więcej informacji, zobacz [Obsługa zmian wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md).

> [!WARNING]
> Upewnij się, że użytkownik wie, że zmiana została skorygowana lub wycofana. Na przykład użyj `System.Windows.Forms.MessageBox.Show("message").`

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Programy obsługi zdarzeń propagujące zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md)
