---
title: Dostosowywanie okna właściwości
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: c02bdb890ed6e65db4916efa9899e967a1ce897c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936297"
---
# <a name="customizing-the-properties-window"></a>Dostosowywanie okna właściwości
W języku specyficznym dla domeny (DSL) w programie Visual Studio, można dostosować wygląd i zachowanie w oknie właściwości. W definicji DSL definiuje się właściwości domeny na każdej klasy domeny. Domyślnie po wybraniu wystąpienia klasy w diagramie lub w Eksploratorze modelu, dla każdej właściwości domeny znajduje się w oknie dialogowym właściwości. Dzięki temu można wyświetlić i edytować wartości właściwości domeny, nawet jeśli ma nie mapowane do pól kształtów na diagramie.

## <a name="names-descriptions-and-categories"></a>Nazwy, opisy i kategorii
 **Nazwy i nazwy wyświetlanej**. W swojej definicji właściwości domeny nazwa wyświetlana właściwości jest nazwa, która pojawia się w czasie wykonywania w oknie dialogowym właściwości. Z drugiej strony Nazwa jest używana podczas pisania kodu programu do aktualizacji właściwości. Nazwa musi być poprawna nazwa alfanumeryczna CLR, ale nazwa wyświetlana może zawierać spacji.

 Jeśli nazwa właściwości w definicji DSL, jego nazwę wyświetlaną ustawiono automatycznie kopię nazwy. Jeśli zostanie wpisana nazwa cased Pascal, takie jak "FuelGauge", nazwa wyświetlana automatycznie będzie zawierać spacji: "We wprowadzaniu miernika". Można jednak jawnie ustawić nazwę wyświetlaną, z inną wartością.

 **Opis elementu**. Opis właściwości domeny pojawia się w dwóch miejscach:

- W dolnej części okna właściwości, gdy użytkownik wybierze właściwości. Służy do wyjaśnienia dla użytkownika, właściwość reprezentuje.

- W kodzie wygenerowanym programu. Jeśli używasz urządzenia dokumentacji można wyodrębnić dokumentacji interfejsu API, pojawi się jako opis tej właściwości w interfejsie API.

  **Kategoria**. Kategoria jest pozycją w oknie dialogowym właściwości.

## <a name="exposing-style-features"></a>Udostępnianie stylu funkcji
 Niektóre funkcje dynamiczne elementy graficzne mogą być reprezentowane lub *udostępniane* jako właściwości domeny. Funkcja, która została udostępniona w ten sposób mogą być aktualizowane przez użytkownika, a więcej łatwo można zaktualizować przy użyciu kodu programu.

 Kliknij prawym przyciskiem myszy klasę kształtu w definicji DSL, wskaż opcję **Dodaj udostępniane**, a następnie wybierz funkcję.

 Kształtów można uwidocznić **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** i **FillGradientMode** właściwości. Łączników można uwidocznić **kolor**`,`**TextColor**, **DashStyle**, i **grubość** właściwości. Na diagramach należy udostępnić **FillColor** i **TextColor** właściwości.

## <a name="forwarding-displaying-properties-of-related-elements"></a>Przekazywanie: Wyświetlanie właściwości powiązanych elementów
 Gdy użytkownik DSL wybiera element modelu, właściwości tego elementu są wyświetlane w oknie dialogowym właściwości. Jednak również wyświetlić właściwości określonej powiązanych elementów. Jest to przydatne, jeśli zdefiniowano grupy elementów, które współpracują ze sobą. Na przykład można zdefiniować głównego elementu i elementem opcjonalnym wtyczki. Jeśli drugi nie jest głównym elementem jest mapowana na kształt, jest przydatne zobaczyć ich właściwości, tak jakby znajdowały się w jednym z elementów.

 Efekt ten nosi nazwę *właściwość przekazywania*, a jego odbywa się automatycznie w kilku przypadkach. W innych przypadkach można osiągnąć właściwość przekazywania, definiując deskryptor typu domeny.

### <a name="default-property-forwarding-cases"></a>Domyślna właściwość przekazywania przypadków
 Gdy użytkownik wybierze kształtu lub łącznika lub element w Eksploratorze, następujące właściwości są wyświetlane w oknie dialogowym właściwości:

-   Właściwości domeny, które są zdefiniowane dla klasy domeny elementu modelu, w tym te, które są zdefiniowane w klasach bazowych. Wyjątek stanowi właściwości domeny, dla których ustawiono **jest możliwa do przeglądania** do `False`.

-   Nazwy elementów, które są połączone za pośrednictwem relacje, które mają liczebność 0.. 1. To zapewnia wygodny sposób wyświetlania opcjonalnie połączone elementy, nawet jeśli nie zdefiniowano mapowanie łącznika dla relacji.

-   Właściwości domeny relacji osadzania, który jest przeznaczony dla elementu. Ponieważ relacji osadzania zwykle nie są wyświetlane jawnie, dzięki temu użytkownik widzi ich właściwości.

-   Właściwości domeny, które są zdefiniowane dla wybranego kształtu lub łącznika.

### <a name="adding-property-forwarding"></a>Dodawanie właściwości przekazywania
 Aby przesłać dalej właściwość, należy zdefiniować deskryptor typu domeny. Jeśli masz relacją domeny między dwoma klasami domeny, można użyć deskryptor typu domeny można ustawić właściwości domeny w pierwszej klasie do wartości właściwości domeny w drugim klasy domeny. Na przykład, jeśli mają relację między **książki** klasy domeny i **Autor** klasy domeny, można użyć deskryptor typu domeny się **nazwa** właściwość Książki **Autor** są wyświetlane w oknie dialogowym właściwości, gdy użytkownik wybierze książki.

> [!NOTE]
>  Przekazywanie własności ma wpływ na oknie dialogowym właściwości po użytkownik edytuje modelu. Odbieranie klasy nie definiuje właściwości domeny. Jeśli chcesz uzyskać dostęp właściwości domeny przekazywane w innych częściach definicji DSL lub w kodzie programu, możesz uzyskać dostęp elementu przekazywania.

 W poniższej procedurze przyjęto, że utworzono języka DSL. Pierwsze kroki kilka Podsumowanie wymagań wstępnych.

##### <a name="to-forward-a-property-from-another-element"></a>Aby przekazywać właściwości z innego elementu

1. Tworzenie [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] rozwiązanie, które zawiera co najmniej dwóch klas, które w tym przykładzie są nazywane **książki** i **Autor**. Powinna istnieć relacja dowolnego rodzaju między **książki** i **Autor**.

    Liczebność roli źródłowej (roli na **książki** po stronie) powinna być od 0 do 1 lub 1.. 1, dlatego każdy **książki** ma jeden **Autor**.

2. W **Eksplorator DSL**, kliknij prawym przyciskiem myszy **książki** klasy domeny, a następnie kliknij **Dodaj nowy element DomainTypeDescriptor**.

    Węzeł o nazwie **ścieżki niestandardowe deskryptorów właściwości** pojawia się w obszarze **deskryptorze typu niestandardowego** węzła.

3. Kliknij prawym przyciskiem myszy **deskryptorze typu niestandardowego** węzłem, a następnie kliknij przycisk **dodać nowy atrybut PropertyPath**.

    Nową ścieżkę właściwość pojawia się w obszarze **ścieżki niestandardowe deskryptorów właściwości** węzła.

4. Wybierz nową ścieżkę właściwości, a następnie w **właściwości** oknie **ścieżka do właściwości** do ścieżki elementu odpowiedniego modelu.

    Ścieżka w widoku drzewa można edytować, klikając strzałkę w dół po prawej stronie tej właściwości. Aby uzyskać więcej informacji na temat ścieżek domeny Zobacz [składnia ścieżki domeny](../modeling/domain-path-syntax.md). Po zakończeniu edycji go, ścieżka powinna przypominać przedstawioną **BookReferencesAuthor.Author/! Autor**.

5. Ustaw **właściwość** do **nazwa** właściwość domeny **Autor**.

6. Ustaw **nazwy wyświetlanej** do **nazwę autora**.

7. Transformuj wszystkie szablony, twórz i uruchamiaj język DSL.

8. Na diagramie modelu Tworzenie książki, autora i łączyć je przy użyciu relacji odwołania. Wybierz element książki, a następnie w oknie dialogowym właściwości powinien zostać wyświetlony nazwisko autora, oprócz właściwości książki. Zmień nazwę autora połączone lub link książki do innego autora i obserwować, że zmienia nazwę autora książki.

## <a name="custom-property-editors"></a>Edytory właściwości niestandardowej
 W oknie właściwości zawiera odpowiednią wartość domyślną edytowanie dla rodzaju właściwości każdej domeny. Na przykład dla typu wyliczeniowego, użytkownik zobaczy listy rozwijanej, a na właściwość numeryczną, użytkownik może wprowadzić cyfr. Ta zasada obowiązuje tylko dla typów wbudowanych. Jeśli określisz typ zewnętrzny, użytkownik będzie mógł wyświetlić wartości właściwości, ale nie można go edytować.

 Jednakże można określić następujące edytory i typy:

1. Inny edytor, który jest używany z typu Standardowy. Na przykład można określić ścieżkę edytora właściwości ciągu.

2. Typ zewnętrzny dla właściwości domeny i edytor dla niego.

3. Edytor technologii .NET, takich jak edytor ścieżkę pliku, lub można utworzyć edytora właściwości niestandardowej.

    Konwersja między typu zewnętrznego i typem, takie jak ciąg, który ma domyślny edytor.

   W języku DSL *typ zewnętrzny* jest dowolny typ, który nie jest jednym z typów prostych (na przykład atrybut typu wartość logiczna lub Int32) lub ciąg.

#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Aby zdefiniować właściwość domeny, który ma typ zewnętrzny

1. W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu (DLL), który zawiera typ zewnętrzny w **Dsl** projektu.

    Zestawu może być zestawem .NET lub zestawu podane przez użytkownika.

2. Dodaj typ **typy domen** listy, o ile nie zostało jeszcze to zrobione.

   1.  Otwórz DslDefinition.dsl, a następnie w **Eksplorator DSL**, kliknij prawym przyciskiem myszy węzeł główny, a następnie kliknij przycisk **dodać nowy typ zewnętrzny**.

        Nowy wpis, który pojawia się w obszarze **typy domen** węzła.

       > [!WARNING]
       >  Element menu jest w węźle głównym języka DSL **typy domen** węzła.

   2.  Ustaw nazwę i przestrzeń nazw nowego typu, w oknie dialogowym właściwości.

3. Dodaj właściwość domeny do klasy domeny w zwykły sposób.

    W oknie dialogowym właściwości wybierz typ zewnętrzny z listy rozwijanej w **typu** pola.

   Na tym etapie użytkownicy mogą wyświetlać wartości właściwości, ale nie mogą go edytować. Wyświetlane wartości są uzyskiwane z `ToString()` funkcji. Można napisać kod programu, który ustawia wartości właściwości, na przykład polecenie lub reguły.

### <a name="setting-a-property-editor"></a>Ustawienia edytora właściwości
 Dodaj atrybut CLR dla właściwości domeny, w następującej postaci:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

 Atrybut zostanie ustawiony we właściwości, za pomocą **atrybut niestandardowy** wpis w oknie dialogowym właściwości.

 Typ `AnEditor` musi pochodzić od typu określonego w drugi parametr. Drugi parametr powinien być jeden <xref:System.Drawing.Design.UITypeEditor> lub <xref:System.ComponentModel.ComponentEditor>. Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.EditorAttribute>.

 Można określić własnego edytora lub Edytor podane w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], takich jak <xref:System.Windows.Forms.Design.FileNameEditor> lub <xref:System.Drawing.Design.ImageEditor>. Na przykład użyj następującej procedury, aby właściwość, w którym użytkownik może wprowadzić nazwę pliku.

##### <a name="to-define-a-file-name-domain-property"></a>Aby zdefiniować właściwość domeny nazwa pliku

1.  Dodaj właściwość domeny do klasy domeny w definicji DSL.

2.  Wybierz nową właściwość. W **atrybut niestandardowy** pola w oknie dialogowym właściwości, należy wprowadzić następujący atrybut. Aby wprowadzić ten atrybut, kliknij przycisk wielokropka **[...]**  a następnie wprowadź nazwę i parametry oddzielnie:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3.  Pozostaw typ właściwości domeny jego domyślne ustawienie **ciąg**.

4.  Aby przetestować edytora, sprawdź, czy użytkownicy mogą otwierać Edytor nazwy plików, aby edytować właściwości usługi domeny.

    1.  Naciśnij kombinację klawiszy CTRL + F5 lub F5. W rozwiązaniu do debugowania Otwórz plik testu. Utwórz element klasy domeny i wybierz ją.

    2.  W oknie dialogowym właściwości wybierz właściwość domeny. Pole wartości pokazuje wielokropek **[...]** .

    3.  Kliknij przycisk wielokropka. Zostanie wyświetlone okno dialogowe pliku. Wybierz plik, a następnie zamknij okno dialogowe. Ścieżka pliku jest teraz wartość właściwości domeny.

### <a name="defining-your-own-property-editor"></a>Definiowanie własnych Edytor właściwości
 Można określić własnego edytora. Można byłoby to zrobić, aby zezwolić użytkownikowi, aby edytować typu, który został zdefiniowany lub edytować standardowego typu w specjalny sposób. Na przykład można zezwolić użytkownikowi wprowadź ciąg, który reprezentuje formuły.

 Zdefiniuj edytora, pisząc klasę, która jest pochodną <xref:System.Drawing.Design.UITypeEditor>. Przesłonięcie klasy:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, do interakcji z użytkownikiem i zaktualizować wartość właściwości.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, aby określić czy edytor będzie otworzyć okno dialogowe lub Zapewnij menu rozwijanego.

  Możesz też podać graficzną reprezentację wartości właściwości, która będzie wyświetlana w siatce właściwości. Aby to zrobić, należy zastąpić `GetPaintValueSupported`, i `PaintValue`.  Aby uzyskać więcej informacji, zobacz <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
>  Dodaj kod w osobnym pliku kodu w **Dsl** projektu.

 Na przykład:

```csharp
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}
```

 Aby użyć tego edytora, ustaw **atrybut niestandardowy** właściwości domeny:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

 Aby uzyskać więcej informacji, zobacz <xref:System.Drawing.Design.UITypeEditor>.

## <a name="providing-a-drop-down-list-of-values"></a>Dostarczanie listy rozwijanej wartości
 Możesz podać listę wartości, które użytkownik może wybrać.

> [!NOTE]
>  Ta technika zawiera listę wartości, które można zmienić w czasie wykonywania. Jeśli chcesz udostępnić listę, która nie zmienia, należy wziąć pod uwagę zamiast przy użyciu typu wyliczeniowego, jako typ właściwości domeny.

 Aby zdefiniować listę standardowe wartości, należy dodać do swojej właściwości domeny atrybutu CLR, który ma następującą postać:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

 Definiowanie klasy, która jest pochodną <xref:System.ComponentModel.TypeConverter>. Dodaj kod w oddzielnym pliku w **Dsl** projektu. Na przykład:

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}
```

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)