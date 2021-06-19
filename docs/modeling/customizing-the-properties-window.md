---
title: Dostosowywanie okna właściwości
description: Dowiedz się, jak dostosować wygląd i zachowanie okna właściwości w języku specyficznym dla domeny (DSL) w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e1bd54850264c33c5317a4395f219689a8e8634
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385802"
---
# <a name="customize-the-properties-window"></a>Dostosowywanie okno Właściwości

Możesz dostosować wygląd i zachowanie okna właściwości w języku specyficznym dla domeny (DSL) w Visual Studio. W definicji DSL należy zdefiniować właściwości domeny dla każdej klasy domeny. Domyślnie po wybraniu wystąpienia klasy na diagramie lub w Eksploratorze modelu każda właściwość domeny jest wymieniona w oknie właściwości. Dzięki temu można zobaczyć i edytować wartości właściwości domeny, nawet jeśli nie zostały one zamapowane do kształtowania pól na diagramie.

## <a name="names-descriptions-and-categories"></a>Nazwy, opisy i kategorie

**Nazwa i Nazwa wyświetlana**. W definicji właściwości domeny nazwa wyświetlana właściwości jest nazwą wyświetlaną w czasie uruchamiania w oknie właściwości. Z kolei nazwa jest używana podczas pisania kodu programu w celu zaktualizowania właściwości. Nazwa musi być poprawną nazwą alfanumeryczną CLR, ale nazwa wyświetlana może zawierać spacje.

Gdy ustawisz nazwę właściwości w definicji DSL, jej nazwa wyświetlana jest automatycznie ustawiana na kopię nazwy. W przypadku napisania nazwy z literami Pascal, takiej jak "FuelGauge", nazwa wyświetlana automatycznie będzie zawierać spację: "Miernik paliwa". Można jednak jawnie ustawić wartość Nazwa wyświetlana na inną wartość.

**Opis**. Opis właściwości domeny jest wyświetlany w dwóch miejscach:

- Gdy użytkownik wybierze właściwość, w dolnej części okna właściwości. Można go użyć, aby wyjaśnić użytkownikowi, co reprezentuje właściwość.

- W wygenerowanym kodzie programu. Jeśli do wyodrębnienia dokumentacji interfejsu API używasz funkcji dokumentacji, będzie ona wyświetlana jako opis tej właściwości w interfejsie API.

**Kategoria**. Kategoria jest nagłówkiem w okno Właściwości.

## <a name="expose-style-features"></a>Uwidocznij funkcje stylu

Niektóre dynamiczne funkcje elementów graficznych mogą być reprezentowane lub *udostępniane jako* właściwości domeny. Funkcja, która została ujawniona w ten sposób, może zostać zaktualizowana przez użytkownika i łatwiejsza do zaktualizowania za pomocą kodu programu.

Kliknij prawym przyciskiem myszy klasę kształtu w definicji DSL, wskaż polecenie **Dodaj ujawnione**, a następnie wybierz funkcję.

Na kształtach można uwidocznić właściwości **FillColor,** **OutlineColor,** **TextColor,** **OutlineDashStyle,** **OutlineThickness** **i FillGradientMode.** W łącznikach można uwidocznić właściwości `,` **Color TextColor,** **DashStyle** i **Thickness.** Na diagramach można uwidocznić właściwości **FillColor** i **TextColor.**

## <a name="forwarding-display-properties-of-related-elements"></a>Przekazywanie: wyświetlanie właściwości powiązanych elementów

Gdy użytkownik DSL wybierze element w modelu, właściwości tego elementu są wyświetlane w oknie właściwości. Można jednak również wyświetlić właściwości określonych powiązanych elementów. Jest to przydatne, jeśli zdefiniowano grupę elementów, które współpracują ze sobą. Można na przykład zdefiniować element main i opcjonalny element wtyczki. Jeśli główny element jest mapowany na kształt, a drugi nie, warto zobaczyć wszystkie jego właściwości tak, jakby były na jednym elemencie.

Ten efekt nosi nazwę *przekazywania właściwości* i występuje automatycznie w kilku przypadkach. W innych przypadkach można osiągnąć przekazywanie właściwości przez zdefiniowanie deskryptora typu domeny.

### <a name="default-property-forwarding-cases"></a>Domyślne przypadki przekazywania właściwości

Gdy użytkownik wybierze kształt, łącznik lub element w eksploratorze, w oknie okno Właściwości:

- Właściwości domeny, które są zdefiniowane w klasie domeny elementu modelu, w tym te, które są zdefiniowane w klasach bazowych. Wyjątkiem są właściwości domeny, dla których ustawiono dla właściwości **Można przeglądać** wartość `False` .

- Nazwy elementów połączonych za pośrednictwem relacji, które mają liczebność 0..1. Zapewnia to wygodną metodę wyświetlanie opcjonalnie połączonych elementów, nawet jeśli nie zdefiniowano mapowania łącznika dla relacji.

- Właściwości domeny relacji osadzania, która dotyczy elementu. Ponieważ osadzanie relacji zwykle nie jest jawnie wyświetlane, umożliwia to użytkownikowi wyświetlanie ich właściwości.

- Właściwości domeny zdefiniowane dla wybranego kształtu lub łącznika.

### <a name="add-property-forwarding"></a>Dodawanie przekazywania właściwości

Aby przesyłać dalej właściwość, należy zdefiniować deskryptor typu domeny. Jeśli masz relację domeny między dwiema klasami domeny, możesz użyć deskryptora typu domeny, aby ustawić właściwość domeny w pierwszej klasie na wartość właściwości domeny w drugiej klasie domeny. Jeśli na przykład masz relację  między klasą  domeny Książka a klasą domeny Autor, możesz użyć deskryptora  typu domeny, aby właściwość **Name** autora książki pojawiła się w skrypcie okno Właściwości gdy użytkownik wybierze książkę.

> [!NOTE]
> Przekazywanie właściwości ma wpływ tylko na okno Właściwości, gdy użytkownik edytuje model. Nie definiuje właściwości domeny w klasie odbieracej. Jeśli chcesz uzyskać dostęp do przekazanej właściwości domeny w innych częściach definicji DSL lub w kodzie programu, musisz uzyskać dostęp do elementu przekazywania.

W poniższej procedurze przyjęto założenie, że utworzono DSL. Kilka pierwszych kroków zawiera podsumowanie wymagań wstępnych.

#### <a name="forward-a-property-from-another-element"></a>Przekazywanie właściwości z innego elementu

1. Utwórz rozwiązanie zawierające co najmniej dwie klasy, które w [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] tym przykładzie mają nazwę Book **(Książka) i** Author **(Autor).** Między książkami i autorami powinna być relacja **tego** **rodzaju.**

    Liczebność roli źródłowej (roli  po stronie książki) powinna mieć 0..1 lub 1..1, tak aby każda książka zawierała jednego **autora.** 

2. W **Eksploratorze DSL** kliknij prawym przyciskiem myszy **klasę Domena** książki, a następnie kliknij polecenie Dodaj **nową domenęTypDescriptor.**

    Węzeł o nazwie **Ścieżki deskryptorów właściwości** niestandardowych jest wyświetlany w węźle **Deskryptor typu niestandardowego.**

3. Kliknij prawym przyciskiem myszy **węzeł Deskryptor typu** niestandardowego, a następnie kliknij polecenie **Dodaj nową właściwość PropertyPath**.

    Nowa ścieżka właściwości zostanie wyświetlona w **węźle Ścieżki deskryptorów właściwości niestandardowych.**

4. Wybierz nową ścieżkę właściwości, a następnie w **oknie** Właściwości ustaw opcję Ścieżka na **właściwość** na ścieżkę odpowiedniego elementu modelu.

    Możesz edytować ścieżkę w widoku drzewa, klikając strzałkę w dół po prawej stronie tej właściwości. Aby uzyskać więcej informacji na temat ścieżek domeny, zobacz [Składnia ścieżki domeny](../modeling/domain-path-syntax.md). Po edytowaniu ścieżka powinna przypominać **BookReferencesAuthor.Author/! Autor**.

5. Ustaw **właściwość** na **właściwość Nazwa** domeny author . 

6. Ustaw **wartość Nazwa wyświetlana** **na Nazwa autora.**

7. Przekształć wszystkie szablony, skompilować i uruchomić DSL.

8. Na diagramie modelu utwórz książkę, autora i połącz je przy użyciu relacji referencyjnej. Wybierz element książki, a na okno Właściwości obok właściwości książki powinna zostać wyświetlony element Author Name (Nazwisko autora). Zmień nazwę połączonego autora lub połącz książkę z innym autorem i zauważ, że zmienia się nazwa autora książki.

## <a name="custom-property-editors"></a>Edytory właściwości niestandardowych

Okno właściwości zapewnia odpowiednie domyślne środowisko edycji dla typu każdej właściwości domeny. Na przykład w przypadku typu wyliczeniowego użytkownik widzi listę rozwijaną, a w przypadku właściwości liczbowej może wprowadzić cyfry. Dotyczy to tylko typów wbudowanych. Jeśli określisz typ zewnętrzny, użytkownik będzie mógł zobaczyć wartości właściwości, ale nie będzie go edytować.

Można jednak określić następujące edytory i typy:

1. Inny edytor, który jest używany ze standardowym typem. Na przykład można określić edytor ścieżki pliku dla właściwości ciągu.

2. Typ zewnętrzny dla właściwości domeny i edytor dla tej właściwości.

3. Edytor .NET, taki jak edytor ścieżek plików, lub możesz utworzyć własny edytor właściwości niestandardowych.

   Konwersja między typem zewnętrznym i typem, takim jak Ciąg, który ma edytor domyślny.

   W DSL typ zewnętrzny *jest* dowolnym typem, który nie jest jednym z prostych typów (takich jak Wartość logiczna lub Int32) lub Ciąg.

### <a name="define-a-domain-property-that-has-an-external-type"></a>Definiowanie właściwości domeny, która ma typ zewnętrzny

1. W **Eksplorator rozwiązań** dodaj odwołanie do zestawu (DLL), który zawiera typ zewnętrzny, w **projekcie Dsl.**

    Zestaw może być zestawem .NET lub zestawem dostarczonym przez użytkownika.

2. Dodaj typ do **listy Typy domen,** chyba że zostało to już zrobione.

   1. Otwórz dslDefinition.dsl i w **Eksploratorze DSL** kliknij prawym przyciskiem myszy węzeł główny, a następnie kliknij polecenie **Dodaj nowy typ zewnętrzny.**

        Nowy wpis zostanie wyświetlony w **węźle Typy** domen.

       > [!WARNING]
       > Element menu znajduje się w węźle głównym DSL, a nie **w węźle Typy** domen.

   2. Ustaw nazwę i przestrzeń nazw nowego typu w okno Właściwości.

3. Dodaj właściwość domeny do klasy domeny w zwykły sposób.

    W okno Właściwości wybierz typ zewnętrzny z listy rozwijanej w **polu** Typ.

   Na tym etapie użytkownicy mogą wyświetlać wartości właściwości, ale nie mogą jej edytować. Wyświetlane wartości są uzyskiwane z `ToString()` funkcji . Możesz napisać kod programu, który ustawia wartość właściwości, na przykład w poleceniu lub regułę.

### <a name="set-a-property-editor"></a>Ustawianie edytora właściwości

Dodaj atrybut CLR do właściwości domain w następującej postaci:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

Atrybut dla właściwości można ustawić przy użyciu wpisu **Atrybut** niestandardowy w okno Właściwości.

Typ musi `AnEditor` pochodzić od typu określonego w drugim parametrze. Drugi parametr powinien mieć wartość <xref:System.Drawing.Design.UITypeEditor> lub <xref:System.ComponentModel.ComponentEditor> . Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.EditorAttribute>.

Możesz określić własny edytor lub edytor .NET, taki jak <xref:System.Windows.Forms.Design.FileNameEditor> lub <xref:System.Drawing.Design.ImageEditor> . Na przykład użyj poniższej procedury, aby mieć właściwość, w której użytkownik może wprowadzić nazwę pliku.

#### <a name="define-a-file-name-domain-property"></a>Definiowanie właściwości domeny nazwy pliku

1. Dodaj właściwość domeny do klasy domeny w definicji DSL.

2. Wybierz nową właściwość. W polu **Atrybut niestandardowy** w okno Właściwości wprowadź następujący atrybut. Aby wprowadzić ten atrybut, kliknij wielokropek **[...]** , a następnie wprowadź oddzielnie nazwę atrybutu i parametry:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Pozostaw wartość właściwości Type (Typ) domeny w domyślnym ustawieniu **String (Ciąg).**

4. Aby przetestować edytor, sprawdź, czy użytkownicy mogą otworzyć edytora nazw plików w celu edytowania właściwości domeny.

    1. Naciśnij klawisze CTRL+F5 lub F5. W rozwiązaniu debugowania otwórz plik testowy. Utwórz element klasy domeny i wybierz go.

    2. W okno Właściwości wybierz właściwość domeny. Pole wartości zawiera wielokropek **[...]**.

    3. Kliknij wielokropek. Zostanie wyświetlone okno dialogowe pliku. Wybierz plik i zamknij okno dialogowe. Ścieżka pliku jest teraz wartością właściwości domeny.

### <a name="define-your-own-property-editor"></a>Definiowanie własnego edytora właściwości

Możesz zdefiniować własny edytor. Można to zrobić, aby umożliwić użytkownikowi edytowanie zdefiniowanego typu lub edytowanie typu standardowego w specjalny sposób. Można na przykład zezwolić użytkownikowi na wprowadzenie ciągu reprezentującego formułę.

Edytor można zdefiniować, pisząc klasę pochodzącą od klasy <xref:System.Drawing.Design.UITypeEditor> . Klasa musi zastąpić:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, aby wchodzić w interakcje z użytkownikiem i aktualizować wartość właściwości.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, aby określić, czy edytor otworzy okno dialogowe, czy udostępni menu rozwijane.

Można również podać graficzną reprezentację wartości właściwości, która będzie wyświetlana w siatce właściwości. Aby to zrobić, zastąp `GetPaintValueSupported` wartości i `PaintValue` .  Aby uzyskać więcej informacji, zobacz <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
> Dodaj kod w oddzielnym pliku kodu w **projekcie Dsl.**

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

Aby użyć tego edytora, ustaw **atrybut niestandardowy** właściwości domeny na:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

Aby uzyskać więcej informacji, zobacz <xref:System.Drawing.Design.UITypeEditor>.

## <a name="provide-a-drop-down-list-of-values"></a>Podaj listę rozwijaną wartości

Możesz podać listę wartości do wyboru dla użytkownika.

> [!NOTE]
> Ta technika udostępnia listę wartości, które można zmieniać w czasie uruchamiania. Jeśli chcesz podać listę, która nie zmienia się, rozważ użycie typu wyliczeniowego jako typu właściwości domeny.

Aby zdefiniować listę wartości standardowych, należy dodać do właściwości domeny atrybut CLR o następującej postaci:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

Zdefiniuj klasę pochodzącą od <xref:System.ComponentModel.TypeConverter> klasy . Dodaj kod w oddzielnym pliku w **projekcie Dsl.** Na przykład:

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
