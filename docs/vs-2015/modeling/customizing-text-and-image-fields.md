---
title: Dostosowywanie pól tekstowych i obrazów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a7259fc0-5afa-4356-b27e-5641e01628a9
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6baaa9ceba8f40aa5ad7888384027131e0ffe94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654983"
---
# <a name="customizing-text-and-image-fields"></a>Dostosowywanie pól tekstowych i obrazu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zdefiniowaniu dekoratora tekstu w kształcie jest on reprezentowany przez TextField. Aby zapoznać się z przykładami inicjalizacji textfields i innych ShapeFields, należy sprawdzić Dsl\GeneratedCode\Shapes.cs w rozwiązaniu DSL.

 TextField jest obiektem, który zarządza obszarem w obrębie kształtu, takim jak miejsce przypisane do etykiety. Jedno wystąpienie elementu TextField jest współużytkowane przez wiele kształtów tej samej klasy. W wystąpieniu elementu TextField nie jest przechowywany tekst etykiety osobno dla każdego wystąpienia: zamiast tego `GetDisplayText(ShapeElement)` Metoda przyjmuje kształt jako parametr i może wyszukiwać tekst zależny od bieżącego stanu kształtu i jego elementu modelu.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Sposób określania wyglądu pola tekstowego
 `DoPaint()`Metoda jest wywoływana, aby wyświetlić pole na ekranie. Można zastąpić wartość domyślną lub można `DoPaint(),` zastąpić niektóre metody, które wywołuje. Następująca uproszczona wersja metod domyślnych może pomóc w zrozumieniu sposobu zastąpienia domyślnego zachowania:

```
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
// To change the brush for every field, change the shape’s styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application’s styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape’s styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application’s styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }

```

 Istnieje kilka innych par `Get` metod i `Default` właściwości, takich jak `DefaultMultipleLine/GetMultipleLine()` . Można przypisać wartość do właściwości domyślnej, aby zmienić wartość dla wszystkich wystąpień pola kształtu. Aby zmienić wartość z jednego wystąpienia kształtu na inny lub zależnie od stanu kształtu lub jego elementu modelu, Zastąp `Get` metodę.

## <a name="static-customizations"></a>Dostosowania statyczne
 Aby zmienić każde wystąpienie tego pola kształtu, należy najpierw sprawdzić, czy można ustawić właściwość w definicji DSL. Na przykład można ustawić rozmiar i styl czcionki w okno Właściwości.

 Jeśli nie, Zastąp `InitializeShapeFields` metodę klasy Shape i przypisz wartość do odpowiedniej `Default...` Właściwości pola tekstowego.

> [!WARNING]
> Aby przesłonić `InitializeShapeFields()` , należy ustawić właściwość **Generuj podwójną pochodną** klasy Shape na `true` wartość w definicji DSL.

 W tym przykładzie kształt zawiera pole tekstowe, które będzie używane na potrzeby komentarzy użytkownika. Chcemy użyć standardowej czcionki komentarza. Ponieważ jest to standardowa czcionka z zestawu stylów, można ustawić domyślny identyfikator czcionki:

```

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
 Aby wygląd był różny od stanu kształtu lub jego elementu modelu, należy utworzyć własną podklasę `TextField` i zastąpić jedną lub więcej `Get...` metod. Należy również zastąpić metodę InitializeShapeFields kształtu i zamienić wystąpienie elementu TextField na wystąpienie klasy własnej.

 W poniższym przykładzie czcionka pola tekstowego zależy od stanu właściwości domeny logicznej elementu modelu kształtu.

 Aby uruchomić ten przykładowy kod, Utwórz nowe rozwiązanie DSL przy użyciu szablonu o minimalnym języku. Dodaj właściwość domeny logicznej `AlternateState` do przykładowej klasy domeny. Dodaj ikonę dekoratora do klasy ExampleShape i ustaw jej obraz na plik mapy bitowej. Kliknij kolejno pozycje **Przekształć wszystkie szablony**. Dodaj nowy plik kodu w projekcie DSL i Wstaw następujący kod.

 Aby przetestować kod, naciśnij klawisz F5, a następnie w rozwiązaniu debugowania Otwórz przykładowy diagram. Powinien pojawić się domyślny stan ikony. Zaznacz kształt i w okno Właściwości zmień wartość właściwości **AlternateState** . Czcionka nazwy elementu powinna się zmienić.

```
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
 W poprzednim przykładzie pokazano, jak można zmienić pole tekstowe na dowolną czcionkę, która jest dostępna. Jednak preferowaną metodą jest zmiana na jeden z zestawów stylów, które są skojarzone z kształtem lub aplikacją. W tym celu przesłonisz <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> lub GetTextBrushId ().

 Alternatywnie Rozważ zmianę zestawu stylów kształtu przez zastąpienie <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Ma to wpływ na zmianę czcionek i pędzli dla wszystkich pól kształtów.

## <a name="customizing-image-fields"></a>Dostosowywanie pól obrazu
 Po zdefiniowaniu obrazu dekoratora w kształcie i zdefiniowaniu kształtu obrazu obszar, w którym jest wyświetlany kształt, jest zarządzany przez ImageField. Aby zapoznać się z przykładami inicjalizacji ImageFields i innych ShapeFields, należy sprawdzić Dsl\GeneratedCode\Shapes.cs w rozwiązaniu DSL.

 ImageField jest obiektem, który zarządza obszarem w obrębie kształtu, takim jak miejsce przypisane do Dekoratora. Jedno wystąpienie ImageField jest współużytkowane przez wiele kształtów tej samej klasy kształtu. Wystąpienie ImageField nie przechowuje oddzielnego obrazu dla każdego kształtu: zamiast tego `GetDisplayImage(ShapeElement)` Metoda przyjmuje kształt jako parametr i może wyszukiwać obraz zależny od bieżącego stanu kształtu i jego elementu modelu.

 Jeśli chcesz, aby specjalne zachowanie, takie jak obraz zmiennej, można było utworzyć własną klasę pochodną ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Aby utworzyć podklasę elementu ImageField

1. Ustaw właściwość **Generuj podwójnie pochodną** klasy kształtu nadrzędnego w definicji DSL.

2. Zastąp `InitializeShapeFields` metodę klasy Shape.

    - Utwórz nowy plik kodu w projekcie DSL i napisz częściową definicję klasy dla klasy Shape. Zastąp tam definicję metody.

3. Zbadaj kod `InitializeShapeFields` w DSL\GeneratedCode\Shapes.cs.

     W metodzie override należy wywołać metodę bazową, a następnie utworzyć wystąpienie własnej klasy pól obrazu. Służy do zastępowania pola zwykłego obrazu na `shapeFields` liście.

## <a name="dynamic-icons"></a>Ikony dynamiczne
 Ten przykład powoduje, że zmiana ikony zależy od stanu elementu modelu kształtu.

> [!WARNING]
> W tym przykładzie pokazano, jak utworzyć dynamiczny obraz dekoratora. Jeśli jednak chcesz tylko przełączać się między jednym lub dwoma obrazami, w zależności od stanu zmiennej modelu, można utworzyć kilka dekoratory obrazów, zlokalizować je w tym samym miejscu na kształcie, a następnie ustawić filtr widoczności zależnie od określonych wartości zmiennej modelu. Aby ustawić ten filtr, wybierz mapowanie kształtów w definicji DSL, Otwórz okno Szczegóły DSL i kliknij kartę dekoratory.

 Aby uruchomić ten przykładowy kod, Utwórz nowe rozwiązanie DSL przy użyciu szablonu o minimalnym języku. Dodaj właściwość domeny logicznej `AlternateState` do przykładowej klasy domeny. Dodaj ikonę dekoratora do klasy ExampleShape i ustaw jej obraz na plik mapy bitowej. Kliknij kolejno pozycje **Przekształć wszystkie szablony**. Dodaj nowy plik kodu w projekcie DSL i Wstaw następujący kod.

 Aby przetestować kod, naciśnij klawisz F5, a następnie w rozwiązaniu debugowania Otwórz przykładowy diagram. Powinien pojawić się domyślny stan ikony. Zaznacz kształt i w okno Właściwości zmień wartość właściwości **AlternateState** . Ikona powinna następnie zostać obrócona do 90 stopni na tym kształcie.

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
 [Definiowanie kształtów i łączników](../modeling/defining-shapes-and-connectors.md) [Ustawianie obrazu tła na diagramie](../modeling/setting-a-background-image-on-a-diagram.md) [nawigowanie i aktualizowanie modelu w kodzie programowym](../modeling/navigating-and-updating-a-model-in-program-code.md) [pisanie kodu w celu dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
