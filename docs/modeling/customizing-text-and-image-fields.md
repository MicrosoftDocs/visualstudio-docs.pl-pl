---
title: Dostosowywanie pól tekstowych i obrazu
description: Dowiedz się więcej o dostosowywaniu plików tekstowych i obrazów. Dowiedz się również, że definiowanie dekoratora tekstu w kształcie jest reprezentowane przez pole TextField.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52c4deda5b934a9b55c5ecfeec95ca633edf15e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389270"
---
# <a name="customizing-text-and-image-fields"></a>Dostosowywanie pól tekstowych i obrazu
Gdy definiujesz dekorator tekstu w kształcie, jest on reprezentowany przez textField. Aby uzyskać przykłady inicjowania textfields i innych kontrolek ShapeField, sprawdź plik Dsl\GeneratedCode\Shapes.cs w rozwiązaniu DSL.

 TextField to obiekt, który zarządza obszarem w obrębie kształtu, takim jak miejsce przypisane do etykiety. Jedno wystąpienie TextField jest współużytczne przez wiele kształtów tej samej klasy. Wystąpienie TextField nie przechowuje tekstu etykiety oddzielnie dla każdego wystąpienia: zamiast tego metoda przyjmuje kształt jako parametr i może szukać tekstu zależnego od bieżącego stanu kształtu i jego `GetDisplayText(ShapeElement)` elementu modelu.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Jak jest określany wygląd pola tekstowego
 Metoda `DoPaint()` jest wywoływana, aby wyświetlać pole na ekranie. Możesz przesłonić wartość `DoPaint(),` domyślną lub przesłonić niektóre metody, które wywołuje. Następująca uproszczona wersja metod domyślnych może ułatwić zrozumienie sposobu zastępowania domyślnego zachowania:

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }
```

 Istnieje kilka innych par metod `Get` i `Default` właściwości, takich jak `DefaultMultipleLine/GetMultipleLine()` . Możesz przypisać wartość do właściwości Default, aby zmienić wartość dla wszystkich wystąpień pola kształtu. Aby wartość różniła się w zależności od jednego wystąpienia kształtu lub od stanu kształtu lub jego elementu modelu, zastąp `Get` metodę .

## <a name="static-customizations"></a>Dostosowania statyczne
 Jeśli chcesz zmienić każde wystąpienie tego pola kształtu, najpierw sprawdź, czy możesz ustawić właściwość w definicji DSL. Na przykład możesz ustawić rozmiar i styl czcionki w okno Właściwości.

 Jeśli nie, zastąp metodę klasy shape i przypisz wartość do odpowiedniej `InitializeShapeFields` `Default...` właściwości pola tekstowego.

> [!WARNING]
> Aby przesłonić metodę , należy ustawić właściwość `InitializeShapeFields()` **Generates Double Derived** klasy kształtu na `true` wartość w definicji DSL.

 W tym przykładzie kształt ma pole tekstowe, które będzie używane do komentarzy użytkowników. Chcemy użyć standardowej czcionki komentarza. Ponieważ jest to standardowa czcionka z zestawu stylów, możemy ustawić domyślny identyfikator czcionki:

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;
```

## <a name="dynamic-customizations"></a>Dostosowania dynamiczne
 Aby wygląd różnił się w zależności od stanu kształtu lub jego elementu modelu, należy uzyskać własną podklasę i zastąpić `TextField` jedną lub więcej `Get...` metod. Należy również zastąpić metodę InitializeShapeFields kształtu i zastąpić wystąpienie obiektu TextField wystąpieniem własnej klasy.

 Poniższy przykład sprawia, że czcionka pola tekstowego zależy od stanu właściwości domeny logicznych elementu modelu kształtu.

 Aby uruchomić ten przykładowy kod, utwórz nowe rozwiązanie DSL przy użyciu szablonu Minimalny język. Dodaj właściwość domeny logicznych do `AlternateState` klasy domeny ExampleElement. Dodaj dekorator ikon do klasy ExampleShape i ustaw jego obraz na plik mapy bitowej. Kliknij **pozycję Przekształć wszystkie szablony.** Dodaj nowy plik kodu w projekcie DSL i wstaw następujący kod.

 Aby przetestować kod, naciśnij klawisz F5 i w rozwiązaniu debugowania otwórz przykładowy diagram. Powinien zostać wyświetlony domyślny stan ikony. Wybierz kształt i w okno Właściwości zmień wartość właściwości **AlternateState.** Czcionka nazwy elementu powinna ulec zmianie.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }
```

## <a name="style-sets"></a>Zestawy stylów
 W poprzednim przykładzie pokazano, jak można zmienić pole tekstowe na dowolną dostępną czcionkę. Jednak preferowaną metodą jest zmiana jej na jeden z zestawu stylów skojarzonych z kształtem lub z aplikacją. Aby to zrobić, należy zastąpić <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> lub GetTextBrushId().

 Alternatywnie rozważ zmianę zestawu stylów kształtu przez zastąpienie <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Ma to wpływ na zmianę czcionek i pędzli dla wszystkich pól kształtu.

## <a name="customizing-image-fields"></a>Dostosowywanie pól obrazu
 Podczas definiowania dekoratora obrazów w kształcie, a podczas definiowania kształtu obrazu obszar, w którym jest wyświetlany kształt, jest zarządzany przez element ImageField. Aby uzyskać przykłady inicjowania pliku ImageFields i innych kontrolek ShapeField, sprawdź plik Dsl\GeneratedCode\Shapes.cs w rozwiązaniu DSL.

 ImageField to obiekt, który zarządza obszarem w obrębie kształtu, takim jak miejsce przypisane do dekoratora. Jedno wystąpienie ImageField jest współużytczne przez wiele kształtów tej samej klasy kształtu. Wystąpienie ImageField nie przechowuje oddzielnego obrazu dla każdego kształtu: zamiast tego metoda przyjmuje kształt jako parametr i może szukać obrazu zależnego od bieżącego stanu kształtu i jego `GetDisplayImage(ShapeElement)` elementu modelu.

 Jeśli potrzebujesz specjalnego zachowania, takiego jak obraz zmiennej, możesz utworzyć własną klasę pochodzącą od klasy ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Aby utworzyć podklasę ImageField

1. Ustaw właściwość **Generates Double Derived klasy** kształtu nadrzędnego w definicji DSL.

2. Zastąp `InitializeShapeFields` metodę klasy kształtu.

    - Utwórz nowy plik kodu w projekcie DSL i napisz częściową definicję klasy dla klasy kształtu. Zastąp definicję metody w tym miejscu.

3. Sprawdź kod w `InitializeShapeFields` DSL\GeneratedCode\Shapes.cs.

     W metodzie przesłonięcia wywołaj metodę bazową, a następnie utwórz wystąpienie własnej klasy pola obrazu. Użyj tej funkcji, aby zastąpić pole zwykłego obrazu na `shapeFields` liście.

## <a name="dynamic-icons"></a>Ikony dynamiczne
 Ten przykład sprawia, że zmiana ikony zależy od stanu elementu modelu kształtu.

> [!WARNING]
> W tym przykładzie pokazano, jak sprawić, aby dynamiczny dekorator obrazu. Jeśli jednak chcesz przełączać się między jednym lub dwoma obrazami w zależności od stanu zmiennej modelu, łatwiej jest utworzyć kilka dekoratorów obrazów, zlokalizować je w tej samej pozycji na kształcie, a następnie ustawić filtr Widoczność tak, aby zależeć od określonych wartości zmiennej modelu. Aby ustawić ten filtr, wybierz mapę kształtów w definicji DSL, otwórz okno Szczegóły DSL i kliknij kartę Dekoratory.

 Aby uruchomić ten przykładowy kod, utwórz nowe rozwiązanie DSL przy użyciu szablonu Minimalny język. Dodaj właściwość domeny logicznych do `AlternateState` klasy domeny ExampleElement. Dodaj dekorator ikon do klasy ExampleShape i ustaw jego obraz na plik mapy bitowej. Kliknij **pozycję Przekształć wszystkie szablony.** Dodaj nowy plik kodu w projekcie DSL i wstaw następujący kod.

 Aby przetestować kod, naciśnij klawisz F5 i w rozwiązaniu debugowania otwórz przykładowy diagram. Powinien zostać wyświetlony domyślny stan ikony. Wybierz kształt i w okno Właściwości zmień wartość właściwości **AlternateState.** Ikona powinna być następnie wyświetlana obrócona o 90 stopni na tym kształcie.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}
```

## <a name="see-also"></a>Zobacz też

- [Definiowanie kształtów i łączników](../modeling/defining-shapes-and-connectors.md)
- [Ustawienie obrazu tła w diagramie](../modeling/setting-a-background-image-on-a-diagram.md)
- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)