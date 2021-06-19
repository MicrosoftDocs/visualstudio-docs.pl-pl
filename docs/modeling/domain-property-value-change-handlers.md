---
title: Obsługa zmian wartości właściwości domeny
description: Dowiedz się więcej o procedurach obsługi zmian wartości właściwości domeny, których można używać Visual Studio języka specyficznego dla domeny.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1c6cdb027bafdf4d1fe7689d7dd30d697b539370
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389000"
---
# <a name="domain-property-value-change-handlers"></a>Procedury obsługi zmiany wartości właściwości domeny

W Visual Studio języka specyficznego dla domeny, gdy zmienia się wartość właściwości domeny, metody i są wywoływane w `OnValueChanging()` `OnValueChanged()` programie obsługi właściwości domeny. Aby odpowiedzieć na zmianę, można zastąpić te metody.

## <a name="override-the-property-handler-methods"></a>Zastępowanie metod obsługi właściwości

Każda właściwość domeny języka specyficznego dla domeny jest obsługiwany przez klasę, która jest zagnieżdżona wewnątrz jej nadrzędnej klasy domeny. Jego nazwa jest zgodna z *formatem PropertyName* PropertyHandler. Tę klasę procedury obsługi właściwości można sprawdzić w pliku **Dsl\Generated Code\DomainClasses.cs**. W klasie klasa jest wywoływana bezpośrednio przed zmianą `OnValueChanging()` wartości i `OnValueChanged()` jest wywoływana natychmiast po zmianie wartości.

Załóżmy na przykład, że masz klasę domeny o nazwie , która ma właściwość domeny ciągu o nazwie i `Comment` właściwość całkowitą o nazwie `Text` `TextLengthCount` . Aby zawsze zawierać długość ciągu, można napisać następujący kod w oddzielnym pliku `TextLengthCount` `Text` w projekcie Dsl:

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

Zwróć uwagę na następujące punkty dotyczące programów obsługi właściwości:

- Metody obsługi właściwości są wywoływane zarówno wtedy, gdy użytkownik wprowadza zmiany we właściwości domeny, jak i gdy kod programu przypisuje inną wartość do właściwości.

- Metody są wywoływane tylko wtedy, gdy wartość faktycznie się zmienia. Procedura obsługi nie jest wywoływana, jeśli kod programu przypisuje wartość, która jest równa bieżącej wartości.

- Właściwości domeny magazynu obliczanego i niestandardowego nie mają metod OnValueChanged i OnValueChanging.

- Do zmodyfikowania nowej wartości nie można użyć programu obsługi zmian. Jeśli chcesz to zrobić, na przykład aby ograniczyć wartość do określonego zakresu, zdefiniuj . `ChangeRule`

- Do właściwości reprezentującej rolę relacji nie można dodać procedury obsługi zmian. Zamiast tego `AddRule` zdefiniuj klasy i w klasie `DeleteRule` relacji. Te reguły są wyzwalane po utworzeniu lub zmianie linków. Aby uzyskać więcej informacji, zobacz [Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Zmiany w sklepie i poza sklepem

Metody obsługi właściwości są wywoływane wewnątrz transakcji, która zainicjowała zmianę. W związku z tym można wprowadzić więcej zmian w magazynie bez otwierania nowej transakcji. Zmiany mogą spowodować dodatkowe wywołania procedury obsługi.

W przypadku cofania, ponownego lub wycofywania transakcji nie należy wprowadzać zmian w magazynie, czyli zmian elementów modelu, relacji, kształtów, diagramów łączników ani ich właściwości.

Ponadto zazwyczaj nie aktualizuje się wartości podczas ładowania modelu z pliku.

W związku z tym zmiany modelu powinny być zabezpieczane przez test podobny do tego:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Z kolei jeśli procedura obsługi właściwości propaguje zmiany poza magazynem, na przykład do pliku, bazy danych lub zmiennych niechownych, należy zawsze wprowadzać te zmiany, aby wartości zewnętrzne były aktualizowane, gdy użytkownik wywołuje polecenie cofania lub ponownego powtarzania.

### <a name="cancel-a-change"></a>Anulowanie zmiany

Jeśli chcesz zapobiec zmianie, możesz wycofać bieżącą transakcję. Na przykład możesz chcieć upewnić się, że właściwość pozostaje w określonym zakresie.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Alternatywna technika: Właściwości obliczeniowe

W poprzednim przykładzie pokazano, jak można użyć onValueChanged() do propagowania wartości z jednej właściwości domeny do innej. Każda właściwość ma własną przechowywaną wartość.

Zamiast tego można rozważyć zdefiniowanie właściwości pochodnej jako właściwości obliczeniowej. W takim przypadku właściwość nie ma własnego magazynu, a funkcja definiująca jest oceniana za każdym razem, gdy jest wymagana jej wartość. Aby uzyskać więcej informacji, zobacz [Właściwości magazynu obliczeniowego i niestandardowego.](../modeling/calculated-and-custom-storage-properties.md)

Zamiast poprzedniego przykładu można ustawić wartość **pola Kind (Rodzaj)** na `TextLengthCount` Calculated **(Obliczona)** w definicji DSL. Należy podać własną metodę **Get** dla tej właściwości domeny. Metoda **Get** zwróci bieżącą długość `Text` ciągu.

Jednak potencjalną wadą właściwości obliczeniowych jest to, że wyrażenie jest oceniane za każdym razem, gdy jest używana wartość, co może stanowić problem z wydajnością. Ponadto we właściwości obliczeniowej nie ma onValueChanging() ani OnValueChanged().

### <a name="alternative-technique-change-rules"></a>Alternatywna technika: Zmienianie reguł

Jeśli zdefiniujesz changerule, jest ona wykonywana na końcu transakcji, w której zmienia się wartość właściwości.  Aby uzyskać więcej informacji, zobacz [Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

Jeśli w jednej transakcji zostanie wprowadzonych kilka zmian, po zakończeniu wszystkie zmiany zostaną wykonane. Z kolei wartość OnValue... Metody są wykonywane, gdy niektóre zmiany nie zostały wykonane. W zależności od tego, co chcesz osiągnąć, może to spowodować, że zmiana będzie bardziej odpowiednia.

Za pomocą właściwości ChangeRule można również dostosować nową wartość właściwości, aby zachować ją w określonym zakresie.

> [!WARNING]
> Jeśli reguła wprowadza zmiany w zawartości sklepu, mogą zostać wyzwolone inne reguły i procedury obsługi właściwości. Jeśli reguła zmieni właściwość, która ją wyzwoliła, zostanie wywołana ponownie. Należy się upewnić, że definicje reguł nie powodują nieskończonego wyzwalania.

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

Poniższy przykład zastępuje obsługę właściwości właściwości domeny i powiadamia użytkownika o zmianie `ExampleElement` właściwości klasy domeny.

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
