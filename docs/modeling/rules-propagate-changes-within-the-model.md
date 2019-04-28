---
title: Reguły propagujące zmiany w modelu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c30289034c50cc6d754f54ccec3fafcd0f964d15
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437404"
---
# <a name="rules-propagate-changes-within-the-model"></a>Reguły propagujące zmiany w modelu
Można utworzyć regułę magazynu propagowanie zmian jeden element do innego w wizualizacji i modelowania SDK (VMSDK). W przypadku zmiany dowolnego elementu w Store, zasady są zaplanowane do wykonania, zwykle w przypadku, gdy najbardziej zewnętrznej transakcja została zatwierdzona. Istnieją różne typy reguł dla różnych rodzajów zdarzeń, takich jak elementu Dodawanie lub usuwanie go. Zasady można dołączyć do określonych typów elementów, kształty i diagramy. Wiele wbudowanych funkcji są definiowane przez reguły: na przykład zasady upewnij się, że diagram jest aktualizowana po zmianie modelu. Języka specyficznego dla domeny można dostosować, dodając własnych reguł.

 Reguły Store są szczególnie przydatne propagowanie zmian w sklepie — oznacza to, że zmiany do elementów modelu, relacje, łączników i kształtów i ich domeny właściwości. Zasady nie są uruchamiane, gdy użytkownik wywołuje poleceń Cofnij i ponów. Zamiast tego menedżera transakcji sprawia, że się upewnić, że zawartość magazynu zostaną przywrócone do prawidłowy stan. Jeśli chcesz propagujące zmiany do zasobów spoza sklepu używać Store zdarzeń. Aby uzyskać więcej informacji, zobacz [obsługi propagowanie zmian poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Na przykład załóżmy, że chcesz określić, czy zawsze wtedy, gdy użytkownik (lub kodu) tworzy nowy element typu ExampleDomainClass, dodatkowy element innego typu został utworzony w innej części modelu. Można napisać AddRule i skojarzyć ją z ExampleDomainClass. Należy napisać kod w zasadę, aby utworzyć dodatkowy element.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;

namespace ExampleNamespace
{
 // Attribute associates the rule with a domain class:
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class MyAddRule : AddRule
 {
  // Override the abstract method:
  public override void ElementAdded(ElementAddedEventArgs e)
  {
    base.ElementAdded(e);
    ExampleDomainClass element = e.ModelElement;
    Store store = element.Store;
    // Ignore this call if we're currently loading a model:
    if (store.TransactionManager.CurrentTransaction.IsSerializing)
       return;

    // Code here propagates change as required - for example:
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);
      echo.Name = element.Name;
      echo.Parent = element.Parent;
    }
  }
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
   protected override Type[] GetCustomDomainModelTypes()
   {
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
     types.Add(typeof(MyAddRule));
     // If you add more rules, list them here.
     return types.ToArray();
   }
 }
}
```

> [!NOTE]
> Kod regułę, należy zmienić stan tylko elementy wewnątrz Store; oznacza to regułę, należy zmienić tylko elementy modelu, relacje, kształty, łączniki, diagramy lub ich właściwości. Propagowanie zmian do zasobów spoza sklepu, należy zdefiniować Store zdarzenia. Aby uzyskać więcej informacji, zobacz [obsługi propagowanie zmian poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md)

### <a name="to-define-a-rule"></a>Aby zdefiniować regułę

1. Zdefiniuj reguły, zgodnie z prefiksem klasę `RuleOn` atrybutu. Ten atrybut kojarzy regułę z jednej klasy domeny, relacji lub elementów diagramu. Reguła będzie stosowana do każdego wystąpienia tej klasy, która może być abstrakcyjny.

2. Zarejestruj reguły, dodając ją do zestawu, który został zwrócony przez `GetCustomDomainModelTypes()` w klasie modelu domeny.

3. Klasy pochodnej klasy reguł z jednego klas abstrakcyjnych reguły i pisanie kodu metody wykonywania.

   W poniższych sekcjach opisano te kroki, które bardziej szczegółowo.

### <a name="to-define-a-rule-on-a-domain-class"></a>Aby zdefiniować regułę dla klasy domeny

- W pliku kodu niestandardowego, należy zdefiniować klasę i poprzedzić go <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> atrybutu:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- Typ podmiotu, w pierwszym parametrze może być klasą domeny, relacji domeny, kształtu, łącznika lub diagram. Zazwyczaj reguły zastosować do klasy domeny i relacje.

     `FireTime` Jest zazwyczaj `TopLevelCommit`. Daje to gwarancję, że reguła będzie wykonywana tylko wtedy, gdy wprowadzono podstawowe zmiany w transakcji. Alternatyw są wbudowane, która wykonuje regułę wkrótce po zmianie; i LocalCommit, która uruchamia reguły z końcem bieżącej transakcji (co może nie być najbardziej zewnętrzna). Można również ustawić priorytet reguły wpływa na kolejność w kolejce, ale jest to metoda zawodnych osiągania wyników, które są wymagane.

- Możesz określić klasę abstrakcyjną, jako typ tematu.

- Reguła ma zastosowanie do wszystkich wystąpień klasy podmiotu.

- Wartością domyślną dla `FireTime` jest TimeToFire.TopLevelCommit. Powoduje to reguły, które zostaną wykonane podczas peryferyjnych transakcja została zatwierdzona. Alternatywą jest TimeToFire.Inline. Powoduje to reguły, które mają być wykonane wkrótce po zdarzeniu wyzwalającym.

### <a name="to-register-the-rule"></a>Aby zarejestrować reguły

- Dodawanie klasy reguły do listy typów zwrócony przez `GetCustomDomainModelTypes` w modelu domeny:

    ```csharp
    public partial class ExampleDomainModel
     {
       protected override Type[] GetCustomDomainModelTypes()
       {
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
         types.Add(typeof(MyAddRule));
         // If you add more rules, list them here.
         return types.ToArray();
       }
     }

    ```

- Jeśli nie masz pewności nazwy klasy modelu domeny, poszukaj wewnątrz pliku **Dsl\GeneratedCode\DomainModel.cs**

- Napisać ten kod w pliku niestandardowego kodu w projekcie języka DSL.

### <a name="to-write-the-code-of-the-rule"></a>Aby napisać kod reguły

- Pochodną klasy reguł z jednej z następujących klas bazowych:

  | Klasa bazowa | Wyzwalacz |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Element, link lub kształt zostanie dodany.<br /><br /> Umożliwia wykrywanie nowych relacji, oprócz nowych elementów. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Wartość właściwość domeny została zmieniona. Argument metody zawiera starej i nowej wartości.<br /><br /> Dla kształtów, ta reguła jest wyzwalana, gdy wbudowane `AbsoluteBounds` zmiany właściwości, jeśli jest przesuwany.<br /><br /> W wielu przypadkach jest bardziej wygodne zastąpić `OnValueChanged` lub `OnValueChanging` w obsłudze właściwości. Te metody są wywoływane bezpośrednio przed zmianą i po niej. Z drugiej strony gdy zasada jest wykonywana zwykle na końcu transakcji. Aby uzyskać więcej informacji, zobacz [Obsługa zmian wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md). **Uwaga:**  Ta zasada nie zostanie wywołany, po utworzeniu lub usunięciu linku. Zamiast tego należy napisać `AddRule` i `DeleteRule` dla relacji domeny. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Wyzwalane, gdy element lub link ma być usunięty. Właściwość ModelElement.IsDeleting ma wartość true, aż do zakończenia transakcji. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Wykonywane, gdy element lub link został usunięty. Reguła będzie wykonywana po zostały wykonane wszystkie inne zasady, w tym DeletingRules. ModelElement.IsDeleting ma wartość false, a ModelElement.IsDeleted ma wartość true. Aby zezwolić na kolejne cofania, element nie jest usuwany z pamięci, ale zostanie on usunięty z Store.ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Element jest przenoszony z jednego magazynu partycji do innej.<br /><br /> (Zwróć uwagę, że to nie jest powiązana graficzny położenie kształtu). |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Ta reguła ma zastosowanie tylko do relacji domeny. Zostanie on wyzwolony, jeśli element modelu jawnie przypisać do dowolnego końca łącza. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Wyzwalane, gdy kolejność łączy do lub z elementu ulegnie zmianie za pomocą metod MoveBefore lub MoveToIndex łącze. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Wykonania, gdy transakcja jest tworzona. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Wykonania, gdy transakcja ma zostać zatwierdzone. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Wykonania, gdy transakcja zostanie wycofana. |

- Każda klasa ma metodę, która można zastąpić. Typ `override` w swojej klasie, aby je odnajdą. Parametr tej metody identyfikuje element, który został zmieniony.

  Zwróć uwagę na następujące kwestie dotyczące reguł:

1. Zestaw zmian w ramach transakcji może wyzwolić wiele reguł. Zazwyczaj reguły są wykonywane, gdy najbardziej zewnętrznej transakcja została zatwierdzona. Są one wykonywane w nieokreślonej kolejności.

2. Reguła jest zawsze wykonywana wewnątrz transakcji. W związku z tym nie trzeba tworzyć nowej transakcji, aby wprowadzić zmiany.

3. Zasady nie są wykonywane, gdy transakcja zostanie wycofana, lub gdy wykonywane są operacje cofania i ponawiania. Te operacje resetowania zawartość Store do jego poprzedniego stanu. W związku z tym jeśli reguła zmieni się stan niczego poza Store, jego może nie przechowywać w synchronism z Store zawartości. Aby zaktualizować stan poza Store, zaleca się korzystanie ze zdarzeń. Aby uzyskać więcej informacji, zobacz [obsługi propagowanie zmian poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Niektóre reguły są wykonywane, gdy model jest ładowany z pliku. Aby określić, czy podczas ładowania lub zapisywania jest w toku, użyj `store.TransactionManager.CurrentTransaction.IsSerializing`.

5. Jeśli kod reguły tworzy więcej wyzwolenie reguły powoduje zostanie dodany na końcu listy uruchomieniu którego i zostaną wykonane przed zakończeniem transakcji. DeletedRules są wykonywane po wszystkie inne zasady. Jedna reguła można uruchamiać wiele razy w transakcji, jeden raz dla każdej zmiany.

6. Do przekazywania informacji do i z zasad, dane są zapisywane w `TransactionContext`. Jest to po prostu słownik zachowywane podczas wykonywania tej transakcji. Jest on usuwany po zakończeniu transakcji. Argumenty zdarzeń w każdej regule zapewniają dostęp do niego. Należy pamiętać, że zasady nie są wykonywane w przewidywalnej kolejności.

7. Użyj reguł po uwzględnieniu inne alternatywy. Na przykład jeśli chcesz zaktualizować właściwości podczas zmiany wartości, należy rozważyć użycie obliczonej właściwości. Jeśli chcesz ograniczyć rozmiar lub położenie kształtu, użyj `BoundsRule`. Aby odpowiedzieć na zmianę wartości właściwości, należy dodać `OnValueChanged` obsługi do właściwości. Aby uzyskać więcej informacji, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Przykład
 Poniższy przykład aktualizuje właściwości podczas tworzenia wystąpienia relacji domeny połączyć dwa elementy. Zasady zostaną wyzwolone, nie tylko w przypadku, gdy użytkownik tworzy łącze na diagramie, ale także jeśli kod programu służy do tworzenia linku.

 Aby przetestować ten przykład, Utwórz DSL za pomocą szablonu rozwiązania przepływu zadań i Wstaw następujący kod w pliku w projekcie języka Dsl. Tworzenie i uruchamianie rozwiązania i otworzyć przykładowy plik w projekcie debugowanie. Rysuj Link komentarza między kształt komentarza i elementu przepływu. Zmiany tekstu w komentarzu do raportu w elemencie najbardziej aktualne, które połączyły się.

 W praktyce należy zwykle napisać DeleteRule dla każdego AddRule.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.TaskRuleExample
{

  [RuleOn(typeof(CommentReferencesSubjects))]
  public class RoleRule : AddRule
  {

    public override void ElementAdded(ElementAddedEventArgs e)
    {
      base.ElementAdded(e);
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;
      Comment comment = link.Comment;
      FlowElement subject = link.Subject;
      Transaction current = link.Store.TransactionManager.CurrentTransaction;
      // Don't want to run when we're just loading from file:
      if (current.IsSerializing) return;
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";
    }

  }

  public partial class TaskRuleExampleDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(RoleRule));
      return types.ToArray();
    }
  }

}
```

## <a name="see-also"></a>Zobacz też

- [Programy obsługi zdarzeń propagujące zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md)