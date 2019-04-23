---
title: Dostosowywanie pól tekstowych i obrazu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a7259fc0-5afa-4356-b27e-5641e01628a9
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3c1e6aa853d2f8202ed42652a0d0f70a7300c0b5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077170"
---
# <a name="customizing-text-and-image-fields"></a>Dostosowywanie pól tekstowych i obrazu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zdefiniowaniu dekoratora tekstu w kształcie jest reprezentowana przez element TextField. Przykłady inicjalizacji TextFields i innych ShapeFields należy sprawdzić Dsl\GeneratedCode\Shapes.cs w rozwiązaniu języka DSL.  
  
 Element TextField jest obiektem, który zarządza obszar wewnątrz kształtu, takie jak miejsca, przypisać etykietę. Jedno wystąpienie TextField jest współużytkowana przez wiele kształtów w tej samej klasy. Wystąpienie TextField nie przechowuje tekst etykiety osobno dla poszczególnych wystąpień: zamiast tego `GetDisplayText(ShapeElement)` metoda przyjmuje kształt jako parametr i wyszukiwać zależy od bieżącego stanu kształt i element modelu tekstu.  
  
## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Sposób ustalania wygląd pole tekstowe  
 `DoPaint()` Wywoływana jest metoda wyświetla pola na ekranie. Można albo zastąpić domyślną `DoPaint(),` lub możesz zastąpić niektóre metody, które wywołuje. Uproszczoną wersję domyślnych metod może pomóc Ci zrozumieć, jak można zastąpić domyślne zachowanie:  
  
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
  
 Istnieje kilka innych pary `Get` metod i `Default` właściwości, takie jak `DefaultMultipleLine/GetMultipleLine()`. Można przypisać wartości do właściwości domyślne, aby zmienić wartość dla wszystkich wystąpień pole kształtu. Aby wprowadzić wartości różnią się od wystąpienia jeden kształt do innego lub zależny od stanu kształtu lub jego element modelu, należy zastąpić `Get` metody.  
  
## <a name="static-customizations"></a>Dostosowania statyczne  
 Jeśli chcesz zmienić każde wystąpienie to pole kształtu, najpierw sprawdzić, czy można ustawić właściwości w definicji DSL. Na przykład można ustawić styl i rozmiar czcionki w oknie dialogowym właściwości.  
  
 Jeśli nie, następnie zastąpić `InitializeShapeFields` metodę klasy kształt i przypisywanie wartości do odpowiedniego `Default...` właściwości pola tekstowego.  
  
> [!WARNING]
>  Aby zastąpić `InitializeShapeFields()`, należy ustawić **Generates Double Derived** właściwość klasy kształtu do `true` w definicji DSL.  
  
 W tym przykładzie kształt ma pola tekstowego, który będzie używany dla komentarzy do użytkownika. Chcemy używana czcionka standardowa komentarz. Ponieważ istnieje standardowa czcionkę z zestaw stylów, możemy ustawić domyślny identyfikator czcionki:  
  
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
  
## <a name="dynamic-customizations"></a>Dynamicznego dostosowania  
 Aby wygląd różnią się zależy od stanu kształtu lub jego element modelu, pochodzi z własną podklasę klasy `TextField` i zastąpić co najmniej jeden `Get...` metody. Musi również zastąpić metodę InitializeShapeFields swoje kształt i Zastąp wystąpienia TextField wystąpienia własne klasy.  
  
 Poniższy przykład sprawia, że czcionka pole tekstowe jest zależny od stanu właściwość logiczna domeny kształtu elementu modelu.  
  
 Aby uruchomić ten przykładowy kod, Utwórz nowe rozwiązanie języka DSL za pomocą szablonu minimalnego języka. Dodaj właściwość logiczna domeny `AlternateState` ExampleElement klasy domeny. Dodaj ikonę dekoratora klasy ExampleShape i ustaw jego obraz w pliku mapy bitowej. Kliknij przycisk **Transformuj wszystkie szablony**. Dodaj nowy plik kodu w projekcie języka DSL i Wstaw następujący kod.  
  
 Aby przetestować kod, naciśnij klawisz F5, a następnie w przypadku debugowania rozwiązania Otwórz diagram przykładowej. Domyślny stan ikona powinna zostać wyświetlona. Wybierz kształt, a następnie w oknie Właściwości zmień wartość **AlternateState** właściwości. Należy zmienić czcionkę nazwy elementu.  
  
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
  
## <a name="style-sets"></a>Ustawia styl  
 Powyższy przykład pokazuje, jak zmienić pole tekstowe do każdej czcionki, który jest dostępny. Jednak preferowaną metodą jest Zmień go na jeden zestaw stylów skojarzonej z kształtem lub z aplikacją. Aby to zrobić, możesz zastąpić <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> lub GetTextBrushId().  
  
 Można również rozważyć zmianę stylu zbiór kształt przez zastąpienie <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Ma to wpływ zmiana czcionek i pędzle dla wszystkich pól kształtów.  
  
## <a name="customizing-image-fields"></a>Dostosowywanie pól obrazu  
 Podczas definiowania dekoratora obrazu w kształcie, a podczas definiowania kształt obrazu, obszar, w którym jest wyświetlany kształt zarządza ImageField. Przykłady inicjalizacji ImageFields i innych ShapeFields należy sprawdzić Dsl\GeneratedCode\Shapes.cs w rozwiązaniu języka DSL.  
  
 ImageField jest obiektem, który zarządza obszar wewnątrz kształtu, takie jak miejsce przypisane do dekoratora. Jedno wystąpienie ImageField jest współużytkowana przez wiele kształtów w tej samej klasy kształtu. Wystąpienie ImageField nie przechowuje osobny obraz każdego z kształtów: zamiast tego `GetDisplayImage(ShapeElement)` metoda przyjmuje kształt jako parametr i wyszukiwać obraz, który zależy od bieżącego stanu kształtu oraz jego elementu modelu.  
  
 Jeśli mają specjalne zachowanie, takich jak obraz zmiennej, można utworzyć własne klasy pochodne ImageField.  
  
#### <a name="to-create-a-subclass-of-imagefield"></a>Aby utworzyć podklasę ImageField  
  
1. Ustaw **Generates Double Derived** właściwości z klasy nadrzędnej kształtu w definicji DSL.  
  
2. Zastąp `InitializeShapeFields` metody klasy kształtu.  
  
    - Utwórz nowy plik kodu w projekcie języka DSL i zapisać definicję klasy częściowej klasy kształtu. Zastąp definicję metody istnieje.  
  
3. Sprawdź kod `InitializeShapeFields` w DSL\GeneratedCode\Shapes.cs.  
  
     W metodzie zastąpienie wywołanie metody podstawowej, a następnie utwórz wystąpienie klasy pola własnego obrazu. Umożliwia to Zastąp pole zwykłego obrazu w `shapeFields` listy.  
  
## <a name="dynamic-icons"></a>Dynamiczne ikony  
 W tym przykładzie sprawia, że ikona zmiany jest zależny od stanu elementu modelu kształtu.  
  
> [!WARNING]
>  W tym przykładzie pokazano, jak wprowadzić dekoratora dynamiczny obraz. Jednak jeżeli chcesz przełączać się między co najmniej dwa obrazy w zależności od stanu zmiennej modelu, jest łatwiejsze tworzenie kilku dekoratory obrazu, zlokalizuj je w tym samym położeniu na kształcie, a następnie ustaw filtr widoczności, aby była zależna od określonej wartości modelu Zmienna. Ustawienie tego filtru, wybierz mapowanie kształtów w definicji DSL, Otwórz okno Szczegóły języka DSL, i kliknij kartę Dekoratory.  
  
 Aby uruchomić ten przykładowy kod, Utwórz nowe rozwiązanie języka DSL za pomocą szablonu minimalnego języka. Dodaj właściwość logiczna domeny `AlternateState` ExampleElement klasy domeny. Dodaj ikonę dekoratora klasy ExampleShape i ustaw jego obraz w pliku mapy bitowej. Kliknij przycisk **Transformuj wszystkie szablony**. Dodaj nowy plik kodu w projekcie języka DSL i Wstaw następujący kod.  
  
 Aby przetestować kod, naciśnij klawisz F5, a następnie w przypadku debugowania rozwiązania Otwórz diagram przykładowej. Domyślny stan ikona powinna zostać wyświetlona. Wybierz kształt, a następnie w oknie Właściwości zmień wartość **AlternateState** właściwości. Ikony są wyświetlane obrócony do 90 stopni tego kształtu.  
  
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
 [Definiowanie kształtów i łączników](../modeling/defining-shapes-and-connectors.md)   
 [Ustawienie obrazu tła w diagramie](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
