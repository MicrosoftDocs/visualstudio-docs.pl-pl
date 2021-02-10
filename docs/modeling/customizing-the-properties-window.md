---
title: Dostosowywanie okna właściwości
description: Dowiedz się, jak dostosować wygląd i zachowanie okna właściwości w języku specyficznym dla domeny (DSL) w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7ee201494ed849062458afdcd41c2aed1b83b42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935394"
---
# <a name="customize-the-properties-window"></a>Dostosowywanie okno Właściwości

Możesz dostosować wygląd i zachowanie okna właściwości w języku specyficznym dla domeny (DSL) w programie Visual Studio. W definicji DSL definiuje się właściwości domeny dla każdej klasy domeny. Domyślnie po wybraniu wystąpienia klasy na diagramie lub w Eksploratorze modelu Każda właściwość domeny zostanie wyświetlona w oknie właściwości. Pozwala to na wyświetlanie i edytowanie wartości właściwości domeny, nawet jeśli nie zostały one zamapowane na pola kształtu na diagramie.

## <a name="names-descriptions-and-categories"></a>Nazwy, opisy i kategorie

**Nazwa i nazwa wyświetlana**. W definicji domeny Właściwość Nazwa wyświetlana właściwości jest nazwą wyświetlaną w czasie wykonywania w oknie właściwości. Z kolei nazwa jest używana podczas pisania kodu programu w celu zaktualizowania właściwości. Nazwa musi być poprawną nazwą alfanumeryczną CLR, ale nazwa wyświetlana może zawierać spacje.

Po ustawieniu nazwy właściwości w definicji DSL, jej nazwa wyświetlana jest automatycznie ustawiana na kopię nazwy. Jeśli piszesz nazwę z wielkością liter w języku Pascal, taką jak "FuelGauge", nazwa wyświetlana automatycznie będzie zawierać spację: "Miernik paliwa". Można jednak ustawić nazwę wyświetlaną jawnie na inną wartość.

**Opis**. Opis właściwości domeny pojawia się w dwóch miejscach:

- W dolnej części okna właściwości, gdy użytkownik wybierze właściwość. Można jej użyć do wyjaśnienia użytkownikowi, co reprezentuje właściwość.

- W wygenerowanym kodzie programu. Jeśli do wyodrębnienia dokumentacji interfejsu API używane są materiały dokumentacji, będzie ona wyświetlana jako opis tej właściwości w interfejsie API.

**Kategoria**. Kategoria jest nagłówkiem w okno Właściwości.

## <a name="expose-style-features"></a>Uwidacznianie funkcji stylu

Niektóre funkcje dynamiczne elementów graficznych mogą być reprezentowane lub *uwidocznione* jako właściwości domeny. Funkcja, która została udostępniona w ten sposób, może być aktualizowana przez użytkownika i łatwiej ją aktualizować według kodu programu.

Kliknij prawym przyciskiem myszy klasę Shape w definicji DSL, wskaż polecenie **Dodaj uwidocznione**, a następnie wybierz funkcję.

Na kształtach można uwidocznić właściwości **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**, **OutlineThickness** i **FillGradientMode** . Na łącznikach można uwidocznić właściwości **Color** `,` , **DashStyle** i **grubość** . Na diagramach można uwidocznić właściwości **FillColor** i **TextColor** .

## <a name="forwarding-display-properties-of-related-elements"></a>Przekazywanie: właściwości wyświetlania powiązanych elementów

Gdy użytkownik DSL wybiera element w modelu, właściwości tego elementu są wyświetlane w oknie właściwości. Można jednak również wyświetlić właściwości określonych powiązanych elementów. Jest to przydatne, jeśli zdefiniowano grupę elementów, które współdziałają ze sobą. Na przykład można zdefiniować element główny i opcjonalny element wtyczki. Jeśli element główny jest mapowany do kształtu, a drugi nie jest, warto zobaczyć wszystkie jego właściwości, tak jakby znajdowały się one w jednym elemencie.

Ten efekt jest nazwany *przekazywaniem właściwości* i odbywa się automatycznie w kilku przypadkach. W innych przypadkach można osiągnąć przekazywanie właściwości przez zdefiniowanie deskryptora typu domeny.

### <a name="default-property-forwarding-cases"></a>Domyślne przypadki przekazywania właściwości

Gdy użytkownik wybierze kształt lub łącznik lub element w Eksploratorze, w okno Właściwości są wyświetlane następujące właściwości:

- Właściwości domeny, które są zdefiniowane w klasie domeny elementu modelu, łącznie z tymi, które są zdefiniowane w klasach bazowych. Wyjątkiem są właściwości domeny, dla których ustawiono **umożliwia przeglądania** `False` .

- Nazwy elementów, które są połączone za pomocą relacji, które mają liczebność 0.. 1. Zapewnia to wygodną metodę wyświetlania opcjonalnie połączonych elementów, nawet jeśli nie zdefiniowano mapowania łącznika dla relacji.

- Właściwości domeny relacji osadzania, która odwołuje się do elementu. Ponieważ relacje osadzania nie są zwykle wyświetlane jawnie, umożliwia to użytkownikowi wyświetlanie ich właściwości.

- Właściwości domeny, które są zdefiniowane dla wybranego kształtu lub łącznika.

### <a name="add-property-forwarding"></a>Dodaj przekazywanie właściwości

Aby przesłać dalej właściwość, należy zdefiniować deskryptor typu domeny. Jeśli istnieje relacja domeny między dwiema klasami domeny, można użyć deskryptora typu domeny, aby ustawić właściwość domeny w pierwszej klasie na wartość właściwości domeny w drugiej klasie domeny. Na przykład, jeśli istnieje relacja między klasą **domeny i** klasą **autora** , można użyć deskryptora typu domeny, aby właściwość **Nazwa** **autora** książki była wyświetlana w okno właściwości, gdy użytkownik wybierze książkę.

> [!NOTE]
> Przekazywanie właściwości ma wpływ tylko na okno Właściwości, gdy użytkownik edytuje model. Nie definiuje właściwości domeny dla klasy odbiorczej. Jeśli chcesz uzyskać dostęp do właściwości domeny przekazanej w innych częściach definicji DSL lub w kodzie programu, musisz uzyskać dostęp do elementu przekazującego.

W poniższej procedurze przyjęto założenie, że utworzono DSL. Pierwsze kilka kroków podsumowuje wymagania wstępne.

#### <a name="forward-a-property-from-another-element"></a>Przekazywanie właściwości z innego elementu

1. Utwórz [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] rozwiązanie, które zawiera co najmniej dwie klasy, które w tym przykładzie nazywa się **książką** i **autorem**. Między **książką** i **autorem** powinna istnieć relacja między nimi.

    Liczebność roli źródłowej (rola na stronie **książki** ) powinna mieć wartość 0.. 1 lub 1.. 1, tak aby każda **książka** miała jednego **autora**.

2. W **Eksploratorze DSL** kliknij prawym przyciskiem myszy klasę domena **książki** , a następnie kliknij polecenie **Dodaj nowe element DomainTypeDescriptor**.

    Węzeł o nazwie **ścieżki deskryptorów właściwości niestandardowych** jest wyświetlany w węźle **deskryptora typu niestandardowego** .

3. Kliknij prawym przyciskiem myszy węzeł **deskryptora typu niestandardowego** , a następnie kliknij pozycję **Dodaj nowe PropertyPath**.

    Nowa ścieżka właściwości jest wyświetlana pod **ścieżkami węzła deskryptorów właściwości niestandardowych** .

4. Wybierz nową ścieżkę właściwości, a następnie w oknie **Właściwości** Ustaw **ścieżkę do właściwości** na ścieżkę odpowiedniego elementu modelu.

    Ścieżkę można edytować w widoku drzewa, klikając strzałkę w dół znajdującą się po prawej stronie tej właściwości. Aby uzyskać więcej informacji na temat ścieżek domen, zobacz [Składnia path domeny](../modeling/domain-path-syntax.md). Podczas edytowania ścieżka powinna wyglądać podobnie do **BookReferencesAuthor. Author/! Autor**.

5. Ustaw **Właściwość** na Właściwość **Nazwa** domeny **autora**.

6. Ustaw **nazwę wyświetlaną** na **nazwę autora**.

7. Przekształć wszystkie szablony, Kompiluj i uruchamiaj DSL.

8. Na diagramie modelu Utwórz książkę, autora i połącz je przy użyciu relacji odwołania. Wybierz element Book i w okno Właściwości powinna zostać wyświetlona nazwa autora oprócz właściwości książki. Zmień nazwę połączonego autora lub Połącz książkę z innym autorem i sprawdź, czy nazwa autora zmiany książki.

## <a name="custom-property-editors"></a>Edytory właściwości niestandardowych

Okno właściwości zapewnia odpowiednie domyślne środowisko edytowania dla typu każdej właściwości domeny. Na przykład dla typu wyliczeniowego użytkownik widzi listę rozwijaną, a dla właściwości liczbowej użytkownik może wprowadzić cyfry. Ta wartość dotyczy tylko typów wbudowanych. W przypadku określenia typu zewnętrznego użytkownik będzie widział wartości właściwości, ale nie może go edytować.

Można jednak określić następujące edytory i typy:

1. Inny edytor używany z typem standardowym. Można na przykład określić Edytor ścieżki plików dla właściwości ciągu.

2. Typ zewnętrzny dla właściwości domeny i edytor dla niego.

3. Edytor .NET, taki jak edytor ścieżki plików, lub można utworzyć własny Edytor właściwości niestandardowych.

   Konwersja między typem zewnętrznym i typem takim jak ciąg, który ma domyślny edytor.

   W DSL, *typem zewnętrznym* jest dowolny typ, który nie jest jednym z typów prostych (takich jak Boolean lub Int32) lub ciąg.

### <a name="define-a-domain-property-that-has-an-external-type"></a>Zdefiniuj właściwość domeny z typem zewnętrznym

1. W **Eksplorator rozwiązań**, Dodaj odwołanie do zestawu (dll), który zawiera typ zewnętrzny, w projekcie **DSL** .

    Zestaw może być zestawem platformy .NET lub zestawem dostarczonym przez Ciebie.

2. Dodaj typ do listy **typów domen** , chyba że jeszcze nie zostało to zrobione.

   1. Otwórz DslDefinition. DSL i w **Eksploratorze DSL** kliknij prawym przyciskiem myszy węzeł główny, a następnie kliknij polecenie **Dodaj nowy typ zewnętrzny**.

        Nowy wpis zostanie wyświetlony w węźle **typy domen** .

       > [!WARNING]
       > Element menu znajduje się w węźle głównym DSL, a nie w węźle **typy domeny** .

   2. Ustaw nazwę i przestrzeń nazw nowego typu w okno Właściwości.

3. W zwykły sposób Dodaj właściwość domeny do klasy domeny.

    W okno Właściwości wybierz typ zewnętrzny z listy rozwijanej w polu **Typ** .

   Na tym etapie użytkownicy mogą wyświetlić wartości właściwości, ale nie mogą go edytować. Wyświetlone wartości są uzyskiwane z `ToString()` funkcji. Można napisać kod programu, który ustawia wartość właściwości, na przykład w poleceniu lub w regule.

### <a name="set-a-property-editor"></a>Ustawianie edytora właściwości

Dodaj atrybut CLR do właściwości Domain w następującej postaci:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

Można ustawić atrybut dla właściwości przy użyciu wpisu **atrybutu niestandardowego** w okno właściwości.

Typ musi pochodzić `AnEditor` od typu określonego w drugim parametrze. Drugi parametr powinien mieć wartość <xref:System.Drawing.Design.UITypeEditor> lub <xref:System.ComponentModel.ComponentEditor> . Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.EditorAttribute>.

Możesz określić własny edytor lub Edytor .NET, taki jak <xref:System.Windows.Forms.Design.FileNameEditor> lub <xref:System.Drawing.Design.ImageEditor> . Na przykład użyj poniższej procedury, aby określić właściwość, w której użytkownik może wprowadzić nazwę pliku.

#### <a name="define-a-file-name-domain-property"></a>Zdefiniuj nazwę pliku właściwość domeny

1. Dodaj właściwość domeny do klasy domeny w definicji DSL.

2. Wybierz nową właściwość. W polu **atrybut niestandardowy** w okno właściwości wprowadź następujący atrybut. Aby wprowadzić ten atrybut, kliknij przycisk wielokropka **[...]** , a następnie wprowadź osobno nazwę atrybutu i parametry:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Pozostaw Typ właściwości domena jako domyślne ustawienie **ciągu**.

4. Aby przetestować Edytor, należy sprawdzić, czy użytkownicy mogą otworzyć Edytor nazw plików, aby edytować właściwość domeny.

    1. Naciśnij klawisze CTRL + F5 lub F5. W rozwiązaniu debugowania Otwórz plik testowy. Utwórz element klasy domeny i wybierz go.

    2. W okno Właściwości wybierz właściwość domeny. Pole value zawiera wielokropek **[...]**.

    3. Kliknij wielokropek. Zostanie wyświetlone okno dialogowe plik. Wybierz plik i Zamknij okno dialogowe. Ścieżka pliku jest teraz wartością właściwości domeny.

### <a name="define-your-own-property-editor"></a>Definiowanie własnego edytora właściwości

Można zdefiniować własny edytor. Można to zrobić, aby zezwolić użytkownikowi na edytowanie typu zdefiniowanego przez użytkownika lub Edytowanie typu standardowego w specjalny sposób. Na przykład można zezwolić użytkownikowi na wprowadzanie ciągu, który reprezentuje formułę.

Można zdefiniować edytor, pisząc klasę, która pochodzi od <xref:System.Drawing.Design.UITypeEditor> . Klasa musi przesłonić:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, aby korzystać z użytkownika i aktualizować wartość właściwości.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, aby określić, czy edytor ma otworzyć okno dialogowe, czy udostępnić menu rozwijane.

Możesz również dostarczyć graficzną reprezentację wartości właściwości, która będzie wyświetlana w siatce właściwości. W tym celu Przesłoń `GetPaintValueSupported` i `PaintValue` .  Aby uzyskać więcej informacji, zobacz <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
> Dodaj kod w osobnym pliku kodu w projekcie **DSL** .

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

Aby użyć tego edytora, należy ustawić **atrybut niestandardowy** właściwości domeny na:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

Aby uzyskać więcej informacji, zobacz <xref:System.Drawing.Design.UITypeEditor>.

## <a name="provide-a-drop-down-list-of-values"></a>Podaj listę rozwijaną wartości

Można podać listę wartości, spośród których użytkownik chce wybrać.

> [!NOTE]
> Ta technika zawiera listę wartości, które można zmienić w czasie wykonywania. Jeśli chcesz podać listę, która nie zmienia się, rozważ użycie typu wyliczeniowego jako typu właściwości domeny.

Aby zdefiniować listę wartości standardowych, należy dodać do właściwości domeny atrybut CLR o następującej postaci:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

Zdefiniuj klasę, która dziedziczy z <xref:System.ComponentModel.TypeConverter> . Dodaj kod w osobnym pliku w projekcie **DSL** . Na przykład:

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
