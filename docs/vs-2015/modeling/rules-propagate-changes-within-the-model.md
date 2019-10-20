---
title: Reguły propagują zmiany w modelu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 901d809b5f194bb4e66990b0a0e946be2521bbb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671300"
---
# <a name="rules-propagate-changes-within-the-model"></a>Reguły propagujące zmiany w modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można utworzyć regułę sklepu, aby propagować zmianę z jednego elementu do innego w programie Wizualizacja i Modeling SDK (VMSDK). Gdy zmiana dotyczy dowolnego elementu w magazynie, reguły są planowane do wykonania, zazwyczaj gdy zostanie zatwierdzona nietypowa transakcja. Istnieją różne typy reguł dla różnych rodzajów zdarzeń, takich jak dodawanie elementu lub usuwanie go. Można dołączyć reguły do określonych typów elementów, kształtów lub diagramów. Wiele wbudowanych funkcji jest definiowanych przez reguły: na przykład, gdy model zmienia się, należy zaktualizować diagram. Język specyficzny dla domeny można dostosować przez dodanie własnych reguł.

 Reguły sklepu są szczególnie przydatne w przypadku propagowania zmian w magazynie — to oznacza, że zmiany dotyczą elementów modelu, relacji, kształtów lub łączników oraz ich właściwości domeny. Reguły nie są uruchamiane, gdy użytkownik wywołuje polecenia Cofnij lub wykonaj ponownie. Zamiast tego Menedżer transakcji upewnia się, że zawartość sklepu jest przywracana do odpowiedniego stanu. Jeśli chcesz propagować zmiany do zasobów poza magazynem, użyj zdarzeń ze sklepu. Aby uzyskać więcej informacji, zobacz [programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Załóżmy na przykład, że chcesz określić, że za każdym razem, gdy użytkownik (lub kod) tworzy nowy element typu ExampleDomainClass, w innej części modelu jest tworzony dodatkowy element innego typu. Można napisać AddRule i skojarzyć ją z ExampleDomainClass. Napisz kod w regule, aby utworzyć dodatkowy element.

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

    // Code here propagates change as required – for example:
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
> Kod reguły powinien zmienić stan tylko elementów wewnątrz sklepu; oznacza to, że reguła powinna zmieniać tylko elementy modelu, relacje, kształty, łączniki, diagramy lub ich właściwości. Aby propagować zmiany do zasobów znajdujących się poza magazynem, zdefiniuj zdarzenia ze sklepu. Aby uzyskać więcej informacji, zobacz [programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md)

### <a name="to-define-a-rule"></a>Aby zdefiniować regułę

1. Zdefiniuj regułę jako klasę poprzedzoną atrybutem `RuleOn`. Ten atrybut kojarzy regułę z jedną z klas domeny, relacji lub elementów diagramu. Reguła zostanie zastosowana do każdego wystąpienia tej klasy, które może być abstrakcyjne.

2. Zarejestruj regułę, dodając ją do zestawu zwróconego przez `GetCustomDomainModelTypes()` w klasie modelu domeny.

3. Utwórz klasę reguły z jednej z klas abstrakcyjnych reguł i napisz kod metody wykonania.

   W poniższych sekcjach opisano te kroki bardziej szczegółowo.

### <a name="to-define-a-rule-on-a-domain-class"></a>Aby zdefiniować regułę w klasie domeny

- W pliku kodu niestandardowego Zdefiniuj klasę i poprzedź ją prefiksem <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute>:

    ```
    [RuleOn(typeof(ExampleElement),
         // Usual value – but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- Typ podmiotu w pierwszym parametrze może być klasą domeny, relacją domeny, kształtem, łącznikiem lub diagramem. Zwykle reguły są stosowane do klas domen i relacji.

     @No__t_0 jest zazwyczaj `TopLevelCommit`. Gwarantuje to, że reguła jest wykonywana tylko po wykonaniu wszystkich podstawowych zmian transakcji. Alternatywy są wbudowane, co powoduje wykonanie reguły wkrótce po zmianie; i LocalCommit, która wykonuje regułę na końcu bieżącej transakcji (co może nie być najbardziej zewnętrzne). Możesz również ustawić priorytet reguły, która ma wpływ na jej kolejność w kolejce, ale jest to niezawodna metoda osiągnięcia wymaganego wyniku.

- Jako typ podmiotu można określić klasę abstrakcyjną.

- Reguła jest stosowana do wszystkich wystąpień klasy Subject.

- Wartość domyślna dla `FireTime` to TimeToFire. TopLevelCommit. Powoduje to, że reguła zostanie wykonana po zatwierdzeniu zewnętrznej transakcji. Alternatywą jest TimeToFire. inline. Powoduje to, że reguła zostanie wykonana wkrótce po zdarzeniu wyzwalającym.

### <a name="to-register-the-rule"></a>Aby zarejestrować regułę

- Dodaj klasę reguły do listy typów zwracanych przez `GetCustomDomainModelTypes` w modelu domeny:

    ```
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

- Jeśli nie masz pewności co do nazwy klasy modelu domeny, poszukaj wewnątrz pliku **Dsl\GeneratedCode\DomainModel.cs**

- Napisz ten kod w niestandardowym pliku kodu w projekcie DSL.

### <a name="to-write-the-code-of-the-rule"></a>Aby napisać kod reguły

- Utwórz klasę reguły z jednej z następujących klas podstawowych:

  |                             Klasa bazowa                              |                                                                                                                                                                                                                                                                                                                                                                              Uruchamiać                                                                                                                                                                                                                                                                                                                                                                              |
  |---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |           <xref:Microsoft.VisualStudio.Modeling.AddRule>            |                                                                                                                                                                                                                                                                                                                        Element, link lub kształt są dodawane.<br /><br /> Służy do wykrywania nowych relacji oprócz nowych elementów.                                                                                                                                                                                                                                                                                                                        |
  |          <xref:Microsoft.VisualStudio.Modeling.ChangeRule>          | Wartość właściwości domeny jest zmieniana. Argument Method zawiera stare i nowe wartości.<br /><br /> Dla kształtów ta reguła jest wyzwalana po zmianie wbudowanej właściwości `AbsoluteBounds`, jeśli kształt zostanie przeniesiony.<br /><br /> W wielu przypadkach bardziej wygodne jest przesłonięcie `OnValueChanged` lub `OnValueChanging` w obsłudze właściwości. Metody te są wywoływane bezpośrednio przed zmianą i po niej. Z drugiej strony reguła jest zwykle uruchamiana na końcu transakcji. Aby uzyskać więcej informacji, zobacz [Obsługa zmian wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md). **Uwaga:**  Ta reguła nie jest wyzwalana podczas tworzenia lub usuwania linku. Zamiast tego należy napisać `AddRule` i `DeleteRule` dla relacji domeny. |
  |         <xref:Microsoft.VisualStudio.Modeling.DeletingRule>         |                                                                                                                                                                                                                                                                                                             Wyzwalane, gdy element lub łącze ma zostać usunięte. Właściwość ModelElement. isusuwanie jest prawdziwa do końca transakcji.                                                                                                                                                                                                                                                                                                              |
  |          <xref:Microsoft.VisualStudio.Modeling.DeleteRule>          |                                                                                                                                                                                                       Wykonywane po usunięciu elementu lub łącza. Reguła jest wykonywana po wykonaniu wszystkich innych reguł, w tym DeletingRules. ModelElement. isusunięć ma wartość false, a ModelElement. IsDeleted ma wartość true. Aby zezwolić na kolejne cofnięcie, element nie zostanie faktycznie usunięty z pamięci, ale zostanie usunięty z magazynu. ElementDirectory.                                                                                                                                                                                                       |
  |           <xref:Microsoft.VisualStudio.Modeling.MoveRule>           |                                                                                                                                                                                                                                                                                                           Element jest przenoszony z jednej partycji magazynu do innej.<br /><br /> (Należy zauważyć, że nie jest to związane z położeniem graficznym kształtu).                                                                                                                                                                                                                                                                                                            |
  |     <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>     |                                                                                                                                                                                                                                                                                                                 Ta reguła ma zastosowanie tylko do relacji domeny. Jest wyzwalany, jeśli jawnie przypiszesz element modelu do dowolnego końca łącza.                                                                                                                                                                                                                                                                                                                 |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> |                                                                                                                                                                                                                                                                                                                   Wyzwalane po zmianie kolejności linków do lub z elementu przy użyciu metod MoveBefore lub MoveToIndex na linku.                                                                                                                                                                                                                                                                                                                    |
  |   <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>   |                                                                                                                                                                                                                                                                                                                                                              Wykonywane po utworzeniu transakcji.                                                                                                                                                                                                                                                                                                                                                              |
  |  <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>   |                                                                                                                                                                                                                                                                                                                                                      Wykonywane, gdy transakcja zostanie zatwierdzona.                                                                                                                                                                                                                                                                                                                                                      |
  |  <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>  |                                                                                                                                                                                                                                                                                                                                                     Wykonywane, gdy transakcja zostanie wycofana.                                                                                                                                                                                                                                                                                                                                                     |

- Każda klasa ma metodę, która została przesłonięta. Wpisz `override` w swojej klasie, aby ją odnaleźć. Parametr tej metody identyfikuje element, który jest zmieniany.

  Zwróć uwagę na następujące kwestie dotyczące reguł:

1. Zestaw zmian w transakcji może wyzwolić wiele reguł. Zwykle reguły są wykonywane podczas zatwierdzania transakcji na zewnątrz. Są one wykonywane w nieokreślonej kolejności.

2. Reguła jest zawsze wykonywana wewnątrz transakcji. W związku z tym nie trzeba tworzyć nowej transakcji, aby wprowadzać zmiany.

3. Reguły nie są wykonywane w przypadku wycofania transakcji lub wykonywania operacji cofania lub ponawiania. Te operacje resetują całą zawartość sklepu do poprzedniego stanu. W związku z tym, jeśli reguła zmienia stan wszystkich elementów poza sklepem, może nie być w synchronism z zawartością ze sklepu. Aby zaktualizować stan spoza magazynu, lepiej jest używać zdarzeń. Aby uzyskać więcej informacji, zobacz [programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Niektóre reguły są wykonywane, gdy model jest ładowany z pliku. Aby określić, czy ładowanie lub zapisywanie jest w toku, użyj `store.TransactionManager.CurrentTransaction.IsSerializing`.

5. Jeśli kod reguły tworzy więcej wyzwalaczy reguł, zostaną one dodane na końcu listy wyzwalania i zostaną wykonane przed zakończeniem transakcji. DeletedRules są wykonywane po wszystkich innych regułach. Jedną regułę można uruchamiać wiele razy w transakcji, jednorazowo dla każdej zmiany.

6. Aby przekazać informacje do i z reguł, można przechowywać informacje w `TransactionContext`. Jest to tylko słownik, który jest obsługiwany w trakcie transakcji. Jest ona usuwana po zakończeniu transakcji. Argumenty zdarzeń w każdej regule zapewniają do niej dostęp. Należy pamiętać, że reguły nie są wykonywane w przewidywalnej kolejności.

7. Użyj reguł po uwzględnieniu innych alternatyw. Na przykład jeśli chcesz zaktualizować właściwość po zmianie wartości, rozważ użycie właściwości obliczeniowej. Jeśli chcesz ograniczyć rozmiar lub lokalizację kształtu, użyj `BoundsRule`. Jeśli chcesz odpowiedzieć na zmianę wartości właściwości, Dodaj do właściwości procedurę obsługi `OnValueChanged`. Aby uzyskać więcej informacji, zobacz [reagowanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Przykład
 Poniższy przykład aktualizuje właściwość, gdy tworzona jest relacja domeny, aby połączyć dwa elementy. Reguła zostanie wyzwolona nie tylko wtedy, gdy użytkownik tworzy link na diagramie, ale również wtedy, gdy program Code tworzy link.

 Aby przetestować ten przykład, Utwórz DSL przy użyciu szablonu rozwiązania przepływu zadań i Wstaw następujący kod w pliku w projekcie DSL. Kompiluj i uruchamiaj rozwiązanie, a następnie otwórz przykładowy plik w projekcie debugowania. Narysuj link komentarza między kształtem komentarza a elementem przepływu. Tekst w komentarzu zostanie zmieniony na ostatni element, z którym został połączony.

 W tym przypadku zazwyczaj należy napisać DeleteRule dla każdej AddRule.

```
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
 [Programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md) [BoundsRules — ograniczenia lokalizacji i rozmiaru kształtu](../modeling/boundsrules-constrain-shape-location-and-size.md)
