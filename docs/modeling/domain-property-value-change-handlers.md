---
title: Obsługa zmian wartości właściwości domeny
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 834ee518269c414c8a4ee08b056369813e0a1751
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057551"
---
# <a name="domain-property-value-change-handlers"></a>Obsługa zmian wartości właściwości domeny

W języku specyficznym dla domeny programu Visual Studio: po zmianie wartości właściwości domeny `OnValueChanging()` i `OnValueChanged()` metody są wywoływane w obsłudze właściwości domeny. Aby reagować na zmiany, można zastąpić tych metod.

## <a name="override-the-property-handler-methods"></a>Przesłaniaj metody procedury obsługi właściwości

Każda właściwość domeny języka specyficznego dla domeny jest obsługiwany przez klasę, która jest zagnieżdżona w swojej klasie domeny nadrzędnej. Nazwy w formacie *PropertyName*PropertyHandler. Ta klasa procedury obsługi właściwości w pliku możesz sprawdzić **Dsl\Generated Code\DomainClasses.cs**. W klasie `OnValueChanging()` jest wywoływana tuż przed zmianami wartości i `OnValueChanged()` jest wywoływana bezpośrednio po zmianie wartości.

Załóżmy na przykład, posiadasz klasę domeny o nazwie `Comment` zawierający ciąg właściwość domeny o nazwie `Text` i właściwością liczby całkowitej o nazwie `TextLengthCount`. Aby spowodować `TextLengthCount` zawsze w celu uwzględnienia długość `Text` ciągu, można napisać następujący kod w oddzielnym pliku w projekcie języka Dsl:

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

-   Metody obsługi właściwości są nazywane po użytkownik wprowadza zmiany do właściwości domeny, i gdy program kod przypisuje inną wartość właściwości.

-   Metody są wywoływane tylko wtedy, gdy faktycznie zmienia wartość. Program obsługi nie jest wywoływana, jeśli program kod przypisuje wartość, która jest równa wartości bieżącej.

-   Magazyn obliczone i niestandardowe właściwości domeny nie ma metody OnValueChanged i OnValueChanging.

-   Program obsługi zmiany nie można używać do modyfikowania nowych wartości. Jeśli chcesz to zrobić, na przykład ograniczyć wartość do określonego zakresu, definiowanie `ChangeRule`.

-   Nie można dodać program obsługi zmiany właściwości, który reprezentuje rolę relacji. Zamiast tego Zdefiniuj `AddRule` i `DeleteRule` klasy relacji. Te zasady są wyzwalane, gdy łącza są tworzone lub zmienione. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Zmiany i Magazyn

Metody obsługi właściwości są nazywane wewnątrz transakcji, która zainicjowała zmiany. W związku z tym można wprowadzić więcej zmian w magazynie, bez konieczności otwierania nowych transakcji. Zmiany może prowadzić do dodatkowych obsługi zdarzeń wywołuje.

Gdy jest cofnięcie transakcji, ponowne wykonanie pośrednich lub wycofana, możesz nie powinna dokonywać zmian w magazynie, oznacza to, że zmiany do elementów modelu, relacje, kształty, diagramy łączników lub ich właściwości.

Ponadto należy zwykle nie zaktualizować wartości podczas ładowania modelu z pliku.

W związku z tym powinny być chronione podobnie zmiany w modelu przez test następująco:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Z drugiej strony jeśli procedury obsługi właściwości propaguje zmiany poza magazynu, na przykład w pliku, bazy danych lub zmienne-store, następnie należy zawsze wprowadzić te zmiany, tak aby zewnętrzne wartości są aktualizowane, gdy użytkownik wywołuje cofania lub wykonaj ponownie.

### <a name="cancel-a-change"></a>Anuluj zmianę

Jeśli chcesz uniemożliwić zmiany, możesz je wycofać bieżącej transakcji. Na przykład możesz chcieć upewnij się, że właściwość pozostanie w określonym zakresie.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Alternatywna metoda: obliczane właściwości

W poprzednim przykładzie pokazano, jak OnValueChanged() może służyć do propagowania wartości z właściwości w jednej domenie. Każda właściwość ma swój własny przechowywanej wartości.

Zamiast tego należy rozważyć Definiowanie właściwości pochodnej jako właściwość obliczeniowe. W tym przypadku właściwość ma nie swój własny magazyn, a jest zdefiniowanie szacowania funkcji będzie zawsze wtedy, gdy jej wartość jest wymagana. Aby uzyskać więcej informacji, zobacz [obliczeniowe i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md).

Zamiast poprzedni przykład można ustawić **rodzaj** pole `TextLengthCount` jako **obliczona** w definicji DSL. Czy podać własne **uzyskać** metody dla tej właściwości domeny. **Uzyskać** metoda zwróci Bieżąca długość `Text` ciągu.

Potencjalną wadą właściwości obliczeniowej jest jednak, że wyrażenie jest obliczane, za każdym razem, gdy wartość jest używana, które mogą stanowić problem z wydajnością. Ponadto jest mało bez OnValueChanging() i OnValueChanged() na obliczonej właściwości.

### <a name="alternative-technique-change-rules"></a>Alternatywna metoda: zmiana reguł

Jeśli zdefiniujesz ChangeRule, jest ono wykonywane na końcu transakcji, w którym ulega zmianie wartość właściwości.  Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

Jeśli kilka zmian jest wprowadzonych w jednej transakcji, ChangeRule wykonuje, gdy są one wszystkie ukończone. Natomiast OnValue... metody są wykonywane, gdy niektóre zmiany nie zostały wykonane. W zależności od tego, co chcesz osiągnąć to może spowodować ChangeRule bardziej odpowiednie.

ChangeRule umożliwia również dostosować nowe wartości właściwości, aby utrzymać ją do określonego zakresu.

> [!WARNING]
> Jeśli reguła sprawia, że zmiany do zawartości ze sklepu, inne zasady i procedury obsługi właściwości mogą być wyzwalane. Jeśli reguła zmieni się właściwość, która je wyzwoliło, zostanie ponownie wywołana. Upewnij się, że definicji reguły nie powodują wyzwolenie nieskończone.

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

Poniższy przykład zastępuje procedury obsługi właściwości właściwości domeny i powiadamia użytkownika, gdy właściwość `ExampleElement` klasy domeny została zmieniona.

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