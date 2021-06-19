---
title: Reguły propagujące zmiany w modelu
description: Dowiedz się, jak utworzyć regułę sklepu w celu propagowania zmiany z jednego elementu do innego w zestawie SDK wizualizacji i modelowania (VMSDK).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bde67bd8375e3752370b3b815f8ed155d3123741
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387596"
---
# <a name="rules-propagate-changes-within-the-model"></a>Reguły propagujące zmiany w modelu
Możesz utworzyć regułę sklepu, aby propagować zmianę z jednego elementu do innego w zestawie SDK wizualizacji i modelowania (VMSDK). Gdy nastąpi zmiana w dowolnym elemencie w magazynie, zaplanowano wykonanie reguł, zazwyczaj po zatwierdzona najbardziej zewnętrzna transakcja. Istnieją różne typy reguł dla różnych rodzajów zdarzeń, takich jak dodawanie elementu lub usuwanie go. Reguły można dołączać do określonych typów elementów, kształtów lub diagramów. Wiele wbudowanych funkcji jest definiowanych przez reguły: na przykład reguły zapewniają, że diagram jest aktualizowany po zmianie modelu. Język specyficzny dla domeny można dostosować, dodając własne reguły.

 Reguły magazynu są szczególnie przydatne w przypadku propagacji zmian wewnątrz magazynu, czyli zmian elementów modelu, relacji, kształtów lub łączników oraz ich właściwości domeny. Reguły nie są uruchamiane, gdy użytkownik wywołuje polecenia Cofnij lub Wykonaj ponownie. Zamiast tego Menedżer transakcji zapewnia, że zawartość magazynu są przywracane do prawidłowego stanu. Jeśli chcesz propagować zmiany do zasobów poza magazynem, użyj funkcji Store Events. Aby uzyskać więcej informacji, zobacz [Programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Załóżmy na przykład, że chcesz określić, że za każdym razem, gdy użytkownik (lub kod) tworzy nowy element typu ExampleDomainClass, dodatkowy element innego typu jest tworzony w innej części modelu. Można napisać addrule i skojarzyć ją z ExampleDomainClass. Należy napisać kod w regułę, aby utworzyć dodatkowy element.

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
> Kod reguły powinien zmieniać tylko stan elementów wewnątrz magazynu; oznacza to, że reguła powinna zmieniać tylko elementy modelu, relacje, kształty, łączniki, diagramy lub ich właściwości. Jeśli chcesz propagować zmiany do zasobów poza magazynem, zdefiniuj zdarzenia magazynu. Aby uzyskać więcej informacji, zobacz [Programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>Aby zdefiniować regułę

1. Zdefiniuj regułę jako klasę poprzedzoną `RuleOn` atrybutem . Atrybut kojarzy regułę z jedną z klas domeny, relacji lub elementów diagramu. Reguła zostanie zastosowana do każdego wystąpienia tej klasy, co może być abstrakcyjne.

2. Zarejestruj regułę, dodając ją do zestawu zwróconego przez w `GetCustomDomainModelTypes()` klasie modelu domeny.

3. Wyprowadzanie klasy reguł z jednej z abstrakcyjnych klas reguł i pisanie kodu metody wykonywania.

   W poniższych sekcjach opisano te kroki bardziej szczegółowo.

### <a name="to-define-a-rule-on-a-domain-class"></a>Aby zdefiniować regułę w klasie domeny

- W pliku kodu niestandardowego zdefiniuj klasę i poprzed ją <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> atrybutem :

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- Typ podmiotu w pierwszym parametrze może być klasą domeny, relacją domeny, kształtem, łącznikiem lub diagramem. Zazwyczaj reguły są stosowane do klas domen i relacji.

     Zazwyczaj `FireTime` jest `TopLevelCommit` to . Gwarantuje to, że reguła jest wykonywana tylko po wymusieniu wszystkich podstawowych zmian transakcji. Alternatywami są wbudowane, które wykonują regułę zaraz po zmianie. i LocalCommit, który wykonuje regułę na końcu bieżącej transakcji (która może nie być najbardziej zewnętrzna). Można również ustawić priorytet reguły, aby wpłynąć na jej kolejność w kolejce, ale jest to zawodna metoda osiągnięcia wymaganego wyniku.

- Jako typ podmiotu można określić klasę abstrakcyjną.

- Reguła ma zastosowanie do wszystkich wystąpień klasy podmiotu.

- Wartość domyślna dla `FireTime` to TimeToFire.TopLevelCommit. Powoduje to wykonanie reguły po zatwierdzona najbardziej zewnętrzna transakcja. Alternatywą jest TimeToFire.Inline. Spowoduje to wykonanie reguły zaraz po zdarzeniu wyzwalania.

### <a name="to-register-the-rule"></a>Aby zarejestrować regułę

- Dodaj klasę reguł do listy typów zwracanych przez w `GetCustomDomainModelTypes` modelu domeny:

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

- Jeśli nie masz pewności co do nazwy klasy modelu domeny, poszukaj w pliku **Dsl\GeneratedCode\DomainModel.cs**

- Napisz ten kod w niestandardowym pliku kodu w projekcie DSL.

### <a name="to-write-the-code-of-the-rule"></a>Aby napisać kod reguły

- Wyprowadz klasę reguł z jednej z następujących klas bazowych:

  | Klasa bazowa | Wyzwalacz |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Dodawany jest element, link lub kształt.<br /><br /> Pozwala to wykrywać nowe relacje, a także nowe elementy. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Wartość właściwości domeny jest zmieniana. Argument metody zawiera stare i nowe wartości.<br /><br /> W przypadku kształtów ta reguła jest wyzwalana po zmianie właściwości `AbsoluteBounds` wbudowanej, jeśli kształt zostanie przeniesiony.<br /><br /> W wielu przypadkach wygodniej jest przesłonić właściwość `OnValueChanged` lub `OnValueChanging` w programie obsługi właściwości. Te metody są wywoływane bezpośrednio przed zmianą i po tej zmianie. Z kolei reguła zwykle jest uruchamiana na końcu transakcji. Aby uzyskać więcej informacji, zobacz Procedury obsługi zmian wartości [właściwości domeny](../modeling/domain-property-value-change-handlers.md). **Uwaga:**  Ta reguła nie jest wyzwalana po utworzeniu lub usunięciu linku. Zamiast tego należy napisać dla relacji domeny i `AddRule` `DeleteRule` . |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Wyzwalane, gdy element lub link ma zostać usunięty. Właściwość ModelElement.IsDeleting ma wartość true do momentu zakończenia transakcji. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Wykonywane po usunięciu elementu lub linku. Reguła jest wykonywana po wykonaniu wszystkich innych reguł, w tym deletingRules. Element ModelElement.IsDeleting ma wartość false, a element ModelElement.IsDeleted ma wartość true. Aby umożliwić kolejne Cofnij, element nie jest faktycznie usuwany z pamięci, ale jest usuwany z Store.ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Element jest przenoszony z jednej partycji magazynu do innej.<br /><br /> (Zwróć uwagę, że nie jest to związane z położeniem graficznym kształtu). |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Ta reguła ma zastosowanie tylko do relacji domeny. Jest on wyzwalany, jeśli jawnie przypiszesz element modelu do każdego końca linku. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Wyzwalany, gdy kolejność linków do lub z elementu zostanie zmieniona przy użyciu metod MoveBefore lub MoveToIndex w linku. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Wykonywane po utworzeniu transakcji. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Wykonywane, gdy transakcja ma zostać zatwierdzona. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Wykonywane, gdy transakcja ma zostać wycofana. |

- Każda klasa ma przesłonięcie metody. Wpisz `override` klasę , aby ją odnaleźć. Parametr tej metody identyfikuje element, który jest zmieniany.

  Zwróć uwagę na następujące kwestie dotyczące reguł:

1. Zestaw zmian w transakcji może wyzwalać wiele reguł. Zazwyczaj reguły są wykonywane po zatwierdzona najbardziej zewnętrzna transakcja. Są one wykonywane w nieokreślonym porządku.

2. Reguła jest zawsze wykonywana wewnątrz transakcji. W związku z tym nie trzeba tworzyć nowej transakcji, aby wprowadzić zmiany.

3. Reguły nie są wykonywane podczas wycofywania transakcji lub wykonywania operacji Cofnij lub Ponownie. Te operacje resetuje całą zawartość magazynu do poprzedniego stanu. W związku z tym, jeśli reguła zmienia stan czegokolwiek poza Sklepem, może nie być na bieżąco z zawartością sklepu. Aby zaktualizować stan poza magazynem, lepiej użyć zdarzeń. Aby uzyskać więcej informacji, zobacz [Programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Niektóre reguły są wykonywane po załadowaniu modelu z pliku. Aby określić, czy trwa ładowanie lub zapisywanie, `store.TransactionManager.CurrentTransaction.IsSerializing` użyj .

5. Jeśli kod reguły tworzy więcej wyzwalaczy reguły, zostaną one dodane na końcu listy wyzwalania i zostaną wykonane przed zakończeniem transakcji. Elementy DeletedRules są wykonywane po wszystkich innych zasadach. Jedna reguła może być uruchamiana wiele razy w transakcji, jeden raz dla każdej zmiany.

6. Aby przekazać informacje do i z reguł, można przechowywać informacje w `TransactionContext` . Jest to tylko słownik, który jest utrzymywany podczas transakcji. Jest on usuwany po zakończeniu transakcji. Argumenty zdarzeń w każdej regułie zapewniają do niego dostęp. Pamiętaj, że reguły nie są wykonywane w przewidywalnej kolejności.

7. Użyj reguł po rozważeniu innych alternatyw. Jeśli na przykład chcesz zaktualizować właściwość po zmianie wartości, rozważ użycie właściwości obliczeniowej. Jeśli chcesz ograniczyć rozmiar lub lokalizację kształtu, użyj obiektu `BoundsRule` . Jeśli chcesz odpowiedzieć na zmianę wartości właściwości, dodaj do właściwości `OnValueChanged` program obsługi. Aby uzyskać więcej informacji, zobacz [Odpowiadanie na zmiany i propagowanie ich.](../modeling/responding-to-and-propagating-changes.md)

## <a name="example"></a>Przykład
 W poniższym przykładzie właściwość jest aktualizowana, gdy relacja domeny jest owana w celu połączenia dwóch elementów. Reguła zostanie wyzwolona nie tylko wtedy, gdy użytkownik utworzy link na diagramie, ale także wtedy, gdy kod programu utworzy link.

 Aby przetestować ten przykład, utwórz DSL przy użyciu szablonu rozwiązania przepływu zadań i wstaw następujący kod w pliku w projekcie Dsl. Skompilowanie i uruchomienie rozwiązania oraz otwarcie przykładowego pliku w projekcie Debugowanie. Rysowanie linku komentarza między kształtem Komentarz i elementem przepływu. Tekst w komentarzu zmieni się na raport o najnowszym elemencie, z który został połączony.

 W praktyce zazwyczaj pisze się reguły DeleteRule dla każdej reguły Dodatku.

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