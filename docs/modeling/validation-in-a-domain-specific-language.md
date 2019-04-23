---
title: Sprawdzanie poprawności w języku specyficznym dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09c16e55766c0239346540dfcc74b99b2ed8579b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103598"
---
# <a name="validation-in-a-domain-specific-language"></a>Sprawdzanie poprawności w języku specyficznym dla domeny
Autor języka specyficznego dla domeny (DSL) można zdefiniować ograniczenia sprawdzania poprawności, aby sprawdzić, czy model utworzony przez użytkownika jest znaczący. Na przykład modem DSL umożliwia użytkownikom rysowanie drzewa rodziny osób oraz ich elementów nadrzędnych, można zapisać ograniczenie, które gwarantuje, że elementy podrzędne daty urodzenia po ich elementy nadrzędne.

 Może mieć ograniczenia sprawdzania poprawności, wykonać po zapisaniu modelu po otwarciu i po użytkownik jawnie uruchamia **weryfikacji** polecenia menu. Można również wykonać sprawdzanie poprawności pod kontrolą programu. Na przykład można wykonać sprawdzanie poprawności w odpowiedzi na zmianę wartości właściwości lub relacji.

 Sprawdzanie poprawności jest szczególnie ważne, jeśli piszesz szablony tekstowe lub innych narzędzi, które przetwarzają modeli użytkowników. Sprawdzanie poprawności zapewnia, że modele spełniają warunki wstępne, zakłada, że za pomocą tych narzędzi.

> [!WARNING]
>  Można również zezwolić ograniczenia sprawdzania poprawności, należy zdefiniować w oddzielnym rozszerzenia DSL, wraz z rozszerzenia poleceń menu i program obsługi gestów. Użytkownicy mogą wybierać do zainstalowania tych rozszerzeń, oprócz DSL. Aby uzyskać więcej informacji, zobacz [rozszerzanie DSL za pomocą MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="running-validation"></a>Uruchamianie sprawdzania poprawności
 Gdy użytkownik edytuje modelu, oznacza to, wystąpienie języka specyficznego dla domeny następujące akcje można uruchomić sprawdzania poprawności:

- Kliknij prawym przyciskiem myszy diagram i wybierz **Sprawdź poprawność wszystkich**.

- Kliknij prawym przyciskiem myszy najwyższy węzeł w Eksplorator DSL i wybierz **zweryfikować wszystkie**

- Zapisz model.

- Otwórz model.

- Ponadto można napisać kod programu, który uruchamia sprawdzania poprawności, na przykład, jako część polecenia menu lub w odpowiedzi na zmianę.

  Wszelkie błędy sprawdzania poprawności, pojawi się w **lista błędów** okna. Użytkownik może kliknąć dwukrotnie komunikat o błędzie, aby wybrać elementy modelu, które są przyczyną tego błędu.

## <a name="defining-validation-constraints"></a>Definiowanie ograniczeń walidacji
 Należy zdefiniować ograniczenia sprawdzania poprawności, dodając metody sprawdzania poprawności do klasy domeny lub relacjami DSL. Po uruchomieniu sprawdzania poprawności przez użytkownika lub pod kontrolą programu niektóre lub wszystkie metody sprawdzania poprawności są wykonywane. Każda metoda jest stosowana do każdego wystąpienia klasy, a każda klasa może być kilka metod sprawdzania poprawności.

 Każda metoda sprawdzania poprawności zgłasza wszelkie błędy, które znajdzie.

> [!NOTE]
>  Metody sprawdzania poprawności raportowania błędów, ale nie należy zmieniać modelu. Jeśli chcesz dostosować lub uniemożliwić pewnych zmian, zobacz [alternatywy dla weryfikacji](#alternatives).

#### <a name="to-define-a-validation-constraint"></a>Aby zdefiniować ograniczenie sprawdzania poprawności

1. Włącz sprawdzanie poprawności w **Editor\Validation** węzła:

   1. Otwórz **Dsl\DslDefinition.dsl**.

   2. W Eksploratorze DSL rozwiń **edytora** a następnie wybierz węzeł **weryfikacji**.

   3. W oknie właściwości ustaw **używa** właściwości `true`. Najwygodniej ustawiania tych właściwości jest.

   4. Kliknij przycisk **Przekształć wszystkie szablony** w **Eksploratora rozwiązań** paska narzędzi.

2. Napisz częściowych definicji klasy dla co najmniej jednej klasy domeny lub relacji domeny. Zapisz te definicje w nowym pliku kodu w **Dsl** projektu.

3. Prefiks każdej klasy za pomocą tego atrybutu:

   ```csharp
   [ValidationState(ValidationState.Enabled)]
   ```

   - Domyślnie ten atrybut umożliwi sprawdzania poprawności dla klas pochodnych. Jeśli chcesz wyłączyć sprawdzanie poprawności dla określonej klasy pochodnej, możesz użyć `ValidationState.Disabled`.

4. Dodaj metody sprawdzania poprawności do klasy. Każda metoda sprawdzania poprawności mogą mieć dowolną nazwę, ale ma jeden parametr typu <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext>.

    Musi mieć prefiks z co najmniej `ValidationMethod` atrybuty:

   ```csharp
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
   ```

    ValidationCategories Określ, kiedy metoda jest wykonywana.

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

- Metody sprawdzania poprawności można dodać do domeny, klas lub relacji domeny. Kod dla tych typów znajduje się w **Dsl\Generated Code\Domain\*.cs**.

- Każda metoda sprawdzania poprawności jest stosowana do każdego wystąpienia swojej klasy oraz w jej podklasach. W przypadku relacji domeny każde wystąpienie jest łącze między dwoma elementami modelu.

- Metody sprawdzania poprawności nie są stosowane w dowolnej kolejności określonej, a każda metoda nie ma zastosowania do wystąpienia klasy w dowolnej kolejności przewidywalne.

- Jest zwykle złym zwyczajem dla metody sprawdzania poprawności w celu zaktualizowania zawartości magazynu, ponieważ może to prowadzić do niespójnych wyników. Zamiast tego raportu wszelkie błędy, wywołując metodę `context.LogError`, `LogWarning` lub `LogInfo`.

- W wywołaniu LogError możesz podać listę elementów modelu lub łączy relacji, które wybrano w sytuacji, gdy użytkownik kliknie dwukrotnie komunikat o błędzie.

- Aby uzyskać informacji dotyczących sposobu czytania modelu w kodzie programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Przykład dotyczy następujących modelu domeny. Relacja ParentsHaveChildren ma role, które są nazywane nadrzędnymi i podrzędnymi.

  ![Diagramem definicji DSL &#45; model drzewa rodziny](../modeling/media/familyt_person.png)

## <a name="validation-categories"></a>Sprawdzanie poprawności kategorii
 W <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> atrybut, można określić podczas metody sprawdzania poprawności, które mają zostać wykonane.

|Kategoria|Wykonanie|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Kiedy użytkownik wywoła polecenie menu sprawdzania poprawności.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Po otwarciu pliku modelu.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy plik jest zapisywany. Jeśli występują błędy sprawdzania poprawności, użytkownik będzie mógł skorzystać możliwość zapisywania anulowanie operacji.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy plik jest zapisywany. Jeśli występują błędy z metod opisanych w tej kategorii, użytkownik jest ostrzegany, może nie być możliwe do ponownego otwarcia pliku.<br /><br /> Metody sprawdzania poprawności, które testują zduplikowane nazwy lub identyfikatory lub inne warunki, które mogłyby powodować błędy ładowania, należy używać tej kategorii.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy wywoływana jest metoda ValidateCustom. Liczba ocen w tej kategorii można wywołać tylko z kodu programu.<br /><br /> Aby uzyskać więcej informacji, zobacz [niestandardowego sprawdzania poprawności kategorii](#custom).|

## <a name="where-to-place-validation-methods"></a>Gdzie umieścić metody sprawdzania poprawności
 Często można osiągnąć ten sam efekt, umieszczając metody sprawdzania poprawności na innego typu. Na przykład można dodać metodę do klasy osoby zamiast relacji ParentsHaveChildren i jego iterację łącza:

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

 **Agregowanie ograniczenia sprawdzania poprawności.** Aby zastosować sprawdzania poprawności w przewidywalnej kolejności, należy zdefiniować metodę sprawdzania poprawności pojedynczego w klasie właściciela, taki element główny modelu. Ta technika pozwala też zagregować wiele raportów o błędach w pojedynczym komunikacie.

 Wady są że połączone metoda jest mniej łatwy w zarządzaniu i że ograniczenia musi wszystkie mają taką samą `ValidationCategories`. Dlatego zaleca się zachować każde ograniczenie w oddzielnych metodach, jeśli jest to możliwe.

 **Przekazywanie wartości w pamięci podręcznej kontekstu.** Parametr kontekstu ma słownika, do którego można umieścić dowolne wartości. Słownik utrzymuje się przez cały okres istnienia uruchomienia sprawdzania poprawności. Metody sprawdzania poprawności określonego można na przykład przechowywać liczba błędów w kontekście i użyj go, aby zapobiegać zalewaniu oknie błędów przy użyciu powtarzanych komunikatów. Na przykład:

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }
```

## <a name="validation-of-multiplicities"></a>Sprawdzanie poprawności Liczebność punktów
 Metody sprawdzania poprawności sprawdzania minimalną liczebnością są generowane automatycznie dla DSL. Kod jest zapisywany **Dsl\Generated Code\MultiplicityValidation.cs**. Te metody zaczęły obowiązywać, po włączeniu weryfikacji w **Editor\Validation** węzła w Eksploratorze DSL.

 Jeśli ustawisz Liczebność roli relacji domeny 1.. * lub 1..1, ale użytkownik nie tworzy łącze tę relację, pojawi się komunikat o błędzie weryfikacji.

 Na przykład, jeśli DSL ma klas osoby i miejscowości i relacji PersonLivesInTown z relacją **1..\\** * w roli miejscowości, następnie każda osoba, która jest nie miejscowości, komunikat o błędzie będzie widoczna.

## <a name="running-validation-from-program-code"></a>Uruchamianie sprawdzania poprawności z kodu programu
 Uzyskiwanie dostępu do lub tworząc ValidationController można uruchomić sprawdzania poprawności. Jeśli chcesz, aby błędy, które mają być wyświetlane użytkownikowi w oknie błędów, należy użyć ValidationController, który jest dołączony do DocData dla diagramu. Na przykład jeśli piszesz polecenia menu `CurrentDocData.ValidationController` jest dostępna w klasie zestawu poleceń:

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

 Aby uzyskać więcej informacji, zobacz [jak: Dodawanie polecenia do Menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 Można również utworzyć kontroler osobnego sprawdzania poprawności i zarządzać samodzielnie błędy. Na przykład:

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

## <a name="running-validation-when-a-change-occurs"></a>Uruchamianie sprawdzania poprawności, po wprowadzeniu zmiany
 Jeśli chcesz upewnić się, że użytkownik jest wyświetlane ostrzeżenie natychmiast Jeśli model staje się nieprawidłowy, można zdefiniować zdarzenia magazynu, które uruchamia sprawdzania poprawności. Aby uzyskać więcej informacji o zdarzeniach magazynu, zobacz [obsługi propagowanie zmian poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Oprócz kod sprawdzania poprawności, należy dodać plik kodu niestandardowego do usługi **DslPackage** projektu z zawartością podobny do poniższego przykładu. Ten kod używa `ValidationController` dołączony do dokumentu. Ten kontroler wyświetla błędy sprawdzania poprawności na liście błędów Visual Studio.

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

 Programy obsługi są również nazywane po cofnąć ani ponownego wykonywania operacji, które mają wpływ na łącza lub elementów.

## <a name="custom"></a> Kategorie niestandardowego sprawdzania poprawności
 Oprócz standardowego sprawdzania poprawności kategorii, takich jak Menu i otwórz można zdefiniować własne kategorie. Możesz wywołać tych kategorii z kodu programu. Użytkownik nie może wywołać je bezpośrednio.

 Typowym zastosowaniem niestandardowych kategorii jest definiowanie kategorii, który umożliwia sprawdzenie, czy model spełnia warunki wstępne określonego narzędzia.

 Aby dodać metodę sprawdzania poprawności do określonej kategorii, należy poprzedzić go atrybutem następująco:

```csharp
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]
[ValidationMethod(ValidationCategory.Menu)]
private void TestForCircularLinks(ValidationContext context)
{...}
```

> [!NOTE]
>  Można poprzedzić metodę z dowolnej liczby `[ValidationMethod()]` atrybuty jak chcesz. Możesz dodać metodę do standardowych i niestandardowych kategorii.

 Aby wywołać niestandardowego sprawdzania poprawności:

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

## <a name="alternatives"></a> Alternatywy dla sprawdzania poprawności
 Ograniczenia sprawdzania poprawności raportowania błędów, ale nie należy zmieniać modelu. Jeśli zamiast tego chcesz uniemożliwić modelu staje się nieprawidłowy, można użyć innych technik.

 Techniki te nie są jednak zalecane. Jest to zazwyczaj lepiej zezwolić użytkownikom na podjęcie decyzji o sposobie Popraw nieprawidłowy model.

 **Dostosuj zmian do przywrócenia modelu ważności.** Na przykład jeśli użytkownik ustawi właściwość powyżej maksimum dozwolone, możesz zresetować właściwość maksymalnej wartości. Aby to zrobić, należy zdefiniować regułę. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

 **Wycofaj tę transakcję próbie nieprawidłowe zmiany.** W tym celu można również zdefiniować regułę, ale w niektórych przypadkach istnieje możliwość zastąpienia obsługi właściwości **OnValueChanging()**, lub takie jak przesłonić metodę `OnDeleted().` można wycofać transakcji, należy użyć `this.Store.TransactionManager.CurrentTransaction.Rollback().` Aby uzyskać więcej informacji informacje, zobacz [Obsługa zmian wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md).

> [!WARNING]
> Upewnij się, że użytkownik wie, że zmiana została dostosowana lub wycofana. Na przykład użyć `System.Windows.Forms.MessageBox.Show("message").`

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Programy obsługi zdarzeń propagujące zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md)