---
title: Obsługa zmian wartości właściwości domeny
description: Dowiedz się więcej o obsłudze zmian wartości właściwości domeny, które mogą być używane w języku specyficznym dla domeny programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34f7dcf97498895f841f2a68fd3bc1abac224824
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361732"
---
# <a name="domain-property-value-change-handlers"></a>Obsługa zmian wartości właściwości domeny

W języku specyficznym dla domeny programu Visual Studio, gdy wartość właściwości domeny ulega zmianie, `OnValueChanging()` `OnValueChanged()` metody i są wywoływane w programie obsługi właściwości domeny. Aby odpowiedzieć na zmianę, można zastąpić te metody.

## <a name="override-the-property-handler-methods"></a>Przesłoń metody obsługi właściwości

Każda właściwość domeny języka właściwego dla domeny jest obsługiwana przez klasę, która jest zagnieżdżona wewnątrz klasy domeny nadrzędnej. Jego nazwa jest zgodna z formatem *PropertyName* PropertyHandler. Tę klasę programu obsługi właściwości można sprawdzić w pliku **Dsl\Generated Code\DomainClasses.cs**. W klasie, `OnValueChanging()` jest wywoływana bezpośrednio przed zmianą wartości i `OnValueChanged()` jest wywoływana natychmiast po zmianie wartości.

Załóżmy na przykład, że masz klasę domeny o nazwie `Comment` , która ma właściwość domeny typu String o nazwie `Text` i Właściwość Integer o nazwie `TextLengthCount` . Aby `TextLengthCount` zawsze zawierać długość `Text` ciągu, można napisać następujący kod w osobnym pliku w projekcie DSL:

```csharp
// Domain Class "Comment":
public partial class Comment
{
  // Domain Property "Text":
  partial class TextPropertyHandler
  {
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)
    {
      base.OnValueChanging(element, oldValue, newValue);

      // To update values outside the Store, write code here.

      // Let the transaction manager handle undo:
      Store store = element.Store;
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;

      // Update values in the Store:
      this.TextLengthCount = newValue.Length;
    }
  }
}
```

Zwróć uwagę na następujące kwestie dotyczące obsługi właściwości:

- Metody obsługi właściwości są wywoływane zarówno wtedy, gdy użytkownik wprowadza zmiany do właściwości domeny i gdy kod programu przypisuje inną wartość właściwości.

- Metody są wywoływane tylko wtedy, gdy wartość rzeczywiście ulega zmianie. Procedura obsługi nie jest wywoływana, jeśli kod programu przypisuje wartość równą bieżącej wartości.

- Właściwości obliczeniowe i niestandardowe domeny magazynu nie mają metod OnValueChanged i OnValueChanging.

- Nie można użyć obsługi zmiany w celu zmodyfikowania nowej wartości. Jeśli chcesz to zrobić, na przykład w celu ograniczenia wartości do określonego zakresu, zdefiniuj `ChangeRule` .

- Nie można dodać obsługi zmiany do właściwości, która reprezentuje rolę relacji. Zamiast tego należy zdefiniować `AddRule` i `DeleteRule` dla klasy Relationship. Te reguły są wyzwalane po utworzeniu lub zmianie linków. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Zmiany w sklepie i poza nim

Metody obsługi właściwości są wywoływane wewnątrz transakcji, która zainicjowała zmianę. W związku z tym można wprowadzić więcej zmian w sklepie bez otwierania nowej transakcji. Zmiany mogą spowodować dodatkowe wywołania procedury obsługi.

Po cofnięciu lub wycofaniu transakcji nie należy wprowadzać zmian w sklepie, to oznacza, zmiany elementów modelu, relacji, kształtów, łączników lub ich właściwości.

Ponadto zazwyczaj nie można aktualizować wartości podczas ładowania modelu z pliku.

W związku z tym zmiany w modelu powinny być chronione przez test podobny do tego:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Z kolei, jeśli program obsługi właściwości propaguje zmiany poza magazynem, na przykład do pliku, bazy danych lub zmiennych niemagazynowych, należy zawsze wprowadzić te zmiany, aby wartości zewnętrzne były aktualizowane, gdy użytkownik wywoła polecenie Cofnij lub wykonaj ponownie.

### <a name="cancel-a-change"></a>Anuluj zmianę

Jeśli chcesz zapobiec zmianie, możesz wycofać bieżącą transakcję. Na przykład możesz chcieć upewnić się, że właściwość pozostaje w określonym zakresie.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Metoda alternatywna: właściwości obliczeniowe

W poprzednim przykładzie pokazano, jak OnValueChanged () może służyć do propagowania wartości z jednej domeny do drugiej. Każda właściwość ma własną przechowywaną wartość.

Zamiast tego można rozważyć zdefiniowanie właściwości pochodnej jako właściwości obliczeniowej. W takim przypadku właściwość nie ma własnego magazynu i definiuje funkcję, która jest szacowana, gdy jej wartość jest wymagana. Aby uzyskać więcej informacji, zobacz [właściwości magazynu obliczeniowego i niestandardowego](../modeling/calculated-and-custom-storage-properties.md).

Zamiast poprzedniego przykładu, można ustawić pole **rodzaju** , które `TextLengthCount` ma zostać **obliczone** w definicji DSL. Należy podać własną metodę **Get** dla tej właściwości domeny. Metoda **Get** zwróci bieżącą długość `Text` ciągu.

Jednak potencjalną wadą obliczonych właściwości jest to, że wyrażenie jest oceniane za każdym razem, gdy wartość jest używana, co może stanowić problem z wydajnością. Ponadto nie ma żadnych OnValueChanging () i OnValueChanged () na właściwości obliczeniowej.

### <a name="alternative-technique-change-rules"></a>Alternatywna Technika: reguły zmian

Jeśli zdefiniujesz ChangeRule, jest ono wykonywane na końcu transakcji, w której zmienia się wartość właściwości.  Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

Jeśli w jednej transakcji wprowadzono kilka zmian, ChangeRule wykonuje się po zakończeniu. Z drugiej strony, onvalue... metody są wykonywane, gdy niektóre zmiany nie zostały wykonane. W zależności od tego, co chcesz osiągnąć, może być ChangeRule bardziej odpowiednie.

Możesz również użyć ChangeRule, aby dostosować nową wartość właściwości, aby zachować ją w określonym zakresie.

> [!WARNING]
> Jeśli reguła wprowadza zmiany w zawartości magazynu, mogą być wyzwalane inne reguły i programy obsługi właściwości. Jeśli reguła zmieni właściwość, która ją wywołała, zostanie ponownie wywołana. Należy upewnić się, że definicje reguł nie powodują nieskończonego wyzwalania.

```csharp
using Microsoft.VisualStudio.Modeling;
...
// Change rule on the domain class Comment:
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]
class MyCommentTrimRule : ChangeRule
{
  public override void
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)
  {
    base.ElementPropertyChanged(e);
    Comment comment = e.ModelElement as Comment;

    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))
      comment.Text = comment.Text.Trim();
    // If changed, rule will trigger again.
  }
}

// Register the rule:
public partial class MyDomainModel
{
 protected override Type[] GetCustomDomainModelTypes()
 { return new Type[] { typeof(MyCommentTrimRule) };
 }
}
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład zastępuje procedurę obsługi właściwości domeny i powiadamia użytkownika o `ExampleElement` zmianie właściwości klasy domeny.

### <a name="code"></a>Kod

```csharp
using DslModeling = global::Microsoft.VisualStudio.Modeling;
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;

namespace msft.FieldChangeSample
{
  public partial class ExampleElement
  {
    internal sealed partial class NamePropertyHandler
    {
      protected override void OnValueChanged(ExampleElement element,
         string oldValue, string newValue)
      {
        if (!this.Store.InUndoRedoOrRollback)
        {
           // make in-store changes here...
        }
        // This part is called even in undo:
        System.Windows.Forms.MessageBox.Show("Value Has Changed");
        base.OnValueChanged(element, oldValue, newValue);
      }
    }
  }
}
```
