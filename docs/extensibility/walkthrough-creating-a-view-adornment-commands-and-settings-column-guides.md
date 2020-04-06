---
title: Tworzenie ozdabiania widoku, poleceń i ustawień | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aab9e0ede95eebe6f8f54cc3f01e7e7d5f98d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697644"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Przewodnik: Tworzenie ozdabiania widoku, poleceń i ustawień (prowadnice kolumn)
Edytor tekstu/kodu programu Visual Studio można rozszerzyć za pomocą poleceń i efektów widoku. W tym artykule pokazano, jak rozpocząć korzystanie z popularnej funkcji rozszerzenia, przewodników kolumn. Prowadnice kolumn są wizualnie lekkimi liniami narysowanymi w widoku edytora tekstu, które ułatwiają zarządzanie kodem do określonych szerokości kolumn. W szczególności sformatowany kod może być ważny dla przykładów, które znajdują się w dokumentach, wpisach w blogu lub raportach o błędach.

W tym instruktażu:
- Tworzenie projektu VSIX
- Dodawanie ozdabiania widoku edytora
- Dodaj obsługę zapisywania i uzyskiwania ustawień (gdzie rysować prowadnice kolumn i ich kolor)
- Dodawanie poleceń (dodawanie/usuwanie prowadnic kolumn, zmienianie ich koloru)
- Umieszczanie poleceń w menu kontekstowym menu edycji i dokumentu tekstowego
- Dodawanie obsługi wywoływania poleceń z okna polecenia programu Visual Studio

  Możesz wypróbować wersję funkcji przewodników kolumn z tym[rozszerzeniem](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)Galerii programu Visual Studio .

  > [!NOTE]
  > W tym instruktażu wklejasz dużą ilość kodu do kilku plików generowanych przez szablony rozszerzeń programu Visual Studio. Ale wkrótce ten przewodnik będzie odnosić się do ukończonego rozwiązania w usłudze GitHub z innymi przykładami rozszerzenia. Ukończony kod jest nieco inny, ponieważ ma prawdziwe ikony poleceń zamiast ikon generictemplate.

## <a name="get-started"></a>Wprowadzenie
Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Konfigurowanie rozwiązania
Najpierw należy utworzyć projekt VSIX, dodać ozdoby widoku edytora, a następnie dodać polecenie (które dodaje VSPackage do posiadania polecenia). Podstawowa architektura jest następująca:
- Masz odbiornik tworzenia widoku tekstu, `ColumnGuideAdornment` który tworzy obiekt na widok. Ten obiekt nasłuchuje zdarzeń dotyczących zmiany widoku lub zmiany ustawień, aktualizacji lub ponownego rysowania prowadnic kolumn w razie potrzeby.
- `GuidesSettingsManager` Istnieje, który obsługuje odczytu i zapisu z magazynu ustawień programu Visual Studio. Menedżer ustawień ma również operacje aktualizacji ustawień, które obsługują polecenia użytkownika (dodaj kolumnę, usuń kolumnę, zmień kolor).
- Istnieje pakiet VSIP, który jest niezbędny, jeśli masz polecenia użytkownika, ale jest to tylko standardowy kod, który inicjuje obiekt implementacji poleceń.
- Istnieje `ColumnGuideCommands` obiekt, który uruchamia polecenia użytkownika i łączy programy obsługi poleceń dla poleceń zadeklarowanych w pliku *vsct.*

  **VSIX**. Użyj **polecenia File &#124; New ...** , aby utworzyć projekt. Wybierz węzeł **rozszerzalność** w obszarze **C#** w lewym okienku nawigacji i wybierz pozycję **Projekt VSIX** w prawym okienku. Wprowadź nazwę **ColumnGuides** i wybierz **przycisk OK,** aby utworzyć projekt.

  **Wyświetl ozdoby**. Naciśnij prawy przycisk wskaźnika w węźle projektu w Eksploratorze rozwiązań. Wybierz polecenie **Dodaj &#124; Nowy element ...** , aby dodać nowy element ozdoby widoku. Wybierz **pozycję Edytor &#124; rozszerzalności** w lewym okienku nawigacji i wybierz pozycję Edytor **Adornment** w prawym okienku. Wprowadź nazwę **ColumnGuideAdornment** jako nazwę elementu i wybierz pozycję **Dodaj,** aby ją dodać.

  Możesz zobaczyć ten szablon elementu dodał dwa pliki do projektu (a także odwołania i tak dalej): **ColumnGuideAdornment.cs** i **ColumnGuideAdornmentTextViewCreationListener.cs**. Szablony rysują fioletowy prostokąt w widoku. W poniższej sekcji można zmienić kilka wierszy w odbiorniku tworzenia widoku i zastąpić zawartość **ColumnGuideAdornment.cs**.

  **Polecenia**. W **Eksploratorze rozwiązań**naciśnij prawy przycisk wskaźnika w węźle projektu. Wybierz polecenie **Dodaj &#124; Nowy element ...** , aby dodać nowy element ozdoby widoku. Wybierz **pozycję Rozszerzalność &#124; programu VSPackage** w lewym okienku nawigacji i wybierz polecenie **Polecenie niestandardowe** w prawym okienku. Wprowadź nazwę **ColumnGuideCommands** jako nazwę elementu i wybierz pozycję **Dodaj**. Oprócz kilku odniesień, dodanie poleceń i pakietu dodano również **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**i **ColumnGuideCommandsPackage.vsct**. W poniższej sekcji należy zastąpić zawartość pierwszego i ostatniego pliku, aby zdefiniować i zaimplementować polecenia.

## <a name="set-up-the-text-view-creation-listener"></a>Konfigurowanie odbiornika tworzenia widoku tekstu
Otwórz *ColumnGuideAdornmentTextViewCreationListener.cs* w edytorze. Ten kod implementuje program obsługi za każdym razem, gdy program Visual Studio tworzy widoki tekstu. Istnieją atrybuty, które kontrolują, gdy program obsługi jest wywoływana w zależności od cech widoku.

Kod musi również zadeklarować warstwę ozdabiania. Gdy edytor aktualizuje widoki, pobiera warstwy ozdabiania dla widoku i od tego pobiera elementy ozdabiania. Można zadeklarować kolejność warstwy względem innych atrybutów. Zastąp następującą linię:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

z tymi dwoma liniami:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Zastąpiony wiersz znajduje się w grupie atrybutów, które deklarują warstwę ozdabiania. Zmieniony pierwszy wiersz zmienia się tylko w miejscu, w którym pojawiają się linie pomocnicze kolumn. Rysowanie linii "przed" tekstem w widoku oznacza, że pojawiają się one za lub pod tekstem. Drugi wiersz deklaruje, że ozdoby prowadnicy kolumn mają zastosowanie do jednostek tekstowych, które pasują do pojęcia dokumentu, ale można zadeklarować ozdoby, na przykład, aby pracować tylko dla edytowalny tekst. Więcej informacji znajduje się w [punktach rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>Zaimplementowanie menedżera ustawień
Zastąp zawartość *GuidesSettingsManager.cs* następującym kodem (wyjaśnionym poniżej):

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present.  Allow user to remove the last column
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

Większość tego kodu tworzy i analizuje format ustawień:\<"RGB( int\<>, int\<>, int \<>) int>, \<int>, ...".  Liczby całkowite na końcu to kolumny oparte na jednej kolumnie, w których mają być prowadnice kolumn. Rozszerzenie prowadnic kolumn przechwytuje wszystkie jego ustawienia w ciągu wartości pojedynczego ustawienia.

Istnieją niektóre części kodu warto wyróżnić. Poniższy wiersz kodu pobiera otokę zarządzana programu Visual Studio dla magazynu ustawień. W przeważającej części to streszczenia w rejestrze systemu Windows, ale ten interfejs API jest niezależny od mechanizmu magazynu.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Magazyn ustawień programu Visual Studio używa identyfikatora kategorii i identyfikatora ustawień, aby jednoznacznie zidentyfikować wszystkie ustawienia:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Nie trzeba używać `"Text Editor"` jako nazwy kategorii. Możesz wybrać wszystko, co chcesz.

Pierwsze kilka funkcji to punkty wejścia, aby zmienić ustawienia. Sprawdzają one ograniczenia wysokiego poziomu, takie jak maksymalna dozwolona liczba linii pomocniczych.  Następnie dzwonią `WriteSettings`, który tworzy ciąg ustawień i `GuideLinesConfiguration`ustawia właściwość . Ustawienie tej właściwości zapisuje wartość ustawień w magazynie `SettingsChanged` ustawień programu Visual `ColumnGuideAdornment` Studio i uruchamia zdarzenie, aby zaktualizować wszystkie obiekty, z których każdy jest skojarzony z widokiem tekstowym.

Istnieje kilka funkcji punktu wejścia, `CanAddGuideline`takich jak , które są używane do implementacji poleceń, które zmieniają ustawienia. Gdy program Visual Studio pokazuje menu, wysyła kwerendy implementacji poleceń, aby sprawdzić, czy polecenie jest aktualnie włączone, jaka jest jego nazwa i tak dalej.  Poniżej zobacz jak podłączyć te punkty wejścia dla implementacji poleceń. Aby uzyskać więcej informacji na temat poleceń, zobacz [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Zaimplementuj klasę ColumnGuideAdornment
Klasa `ColumnGuideAdornment` jest tworzone dla każdego widoku tekstu, który może mieć ozdoby. Ta klasa nasłuchuje zdarzeń dotyczących zmiany widoku lub zmiany ustawień oraz aktualizowania lub ponownego rysowania prowadnic kolumn w razie potrzeby.

Zastąp zawartość *ColumnGuideAdornment.cs* następującym kodem (wyjaśnionym poniżej):

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

Wystąpienia tej klasy przytrzymują <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> skojarzone `Line` i listę obiektów narysowanych w widoku.

Konstruktor (wywoływany od `ColumnGuideAdornmentTextViewCreationListener` momentu, gdy program `Line` Visual Studio tworzy nowe widoki) tworzy obiekty prowadnicy kolumn.  Konstruktor dodaje również programy `SettingsChanged` obsługi dla `GuidesSettingsManager`zdarzenia (zdefiniowane w ) i zdarzenia `LayoutChanged` widoku i `Closed`.

Zdarzenie `LayoutChanged` jest uruchamiane z powodu kilku rodzajów zmian w widoku, w tym podczas tworzenia widoku przez program Visual Studio. Program `OnViewLayoutChanged` obsługi `AddGuidelinesToAdornmentLayer` wywołuje do wykonania. Kod w `OnViewLayoutChanged` określa, czy musi zaktualizować pozycje wierszy na podstawie zmian, takich jak zmiany rozmiaru czcionki, wyświetlanie marginesów, przewijanie w poziomie i tak dalej. Kod w `UpdatePositions` powoduje, że linie pomocnicze rysować między znakami lub tuż po kolumnie tekstu, który jest w określonym znaku przesunięcie w wierszu tekstu.

Za każdym razem, gdy ustawienia zmienić `SettingsChanged` funkcję po prostu odtwarza wszystkie `Line` obiekty z niezależnie od nowych ustawień. Po ustawieniu pozycji linii kod usuwa `Line` wszystkie poprzednie `ColumnGuideAdornment` obiekty z warstwy ozdób i dodaje nowe.

## <a name="define-the-commands-menus-and-menu-placements"></a>Definiowanie poleceń, menu i miejsc docelowych menu
Może być wiele do deklarowania poleceń i menu, umieszczanie grup poleceń lub menu w różnych innych menu i podłączanie obsługi poleceń. W tym przewodniku przedstawiono sposób działania poleceń w tym rozszerzeniu, ale aby uzyskać więcej informacji, zobacz [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Wprowadzenie do kodu
Rozszerzenie Prowadnice kolumn pokazuje deklarowanie grupy poleceń, które należą do siebie (dodaj kolumnę, usuń kolumnę, zmień kolor linii), a następnie umieszczając tę grupę w podmenu menu kontekstowego edytora.  Rozszerzenie Prowadnice kolumn dodaje również polecenia do głównego menu **Edycja,** ale utrzymuje je niewidoczne, omówione jako wspólny wzorzec poniżej.

Istnieją trzy części do implementacji poleceń: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct i ColumnGuideCommands.cs. Kod wygenerowany przez szablony umieszcza polecenie w menu **Narzędzia,** które powoduje wyświetlenie okna dialogowego jako implementacja. Można sprawdzić, jak to jest implementowane w *plikach vsct* i *ColumnGuideCommands.cs,* ponieważ jest to proste. Możesz zastąpić kod w tych plikach poniżej.

Kod pakietu zawiera deklaracje standardowy wymagane dla programu Visual Studio, aby odkryć, że rozszerzenie oferuje polecenia i znaleźć, gdzie umieścić polecenia. Gdy pakiet inicjuje, to wystąpienia klasy implementacji poleceń. Aby uzyskać więcej informacji o pakietach związanych z poleceniami, zobacz [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Wzorzec typowych poleceń
Polecenia w rozszerzenie prowadnice kolumn są przykładem bardzo często wzorzec w programie Visual Studio. Pokrewne polecenia są umieszczane w grupie i umieszczane w`<CommandFlag>CommandWellOnly</CommandFlag>`menu głównym, często z " " ustawionym, aby polecenie było niewidoczne.  Umieszczanie poleceń w menu głównym (takich jak **Edycja)** nadaje im ładne nazwy (takie jak **Edit.AddColumnGuide**), które są przydatne do znajdowania poleceń podczas ponownego przypisywania powiązań klawiszy w **opcjach narzędzi.** Jest to również przydatne do uzyskiwania uzupełnienia podczas wywoływania poleceń z **okna polecenia**.

Następnie należy dodać grupę poleceń do menu kontekstowych lub podmenu, w którym użytkownik oczekuje użycia poleceń. Visual Studio `CommandWellOnly` traktuje jako flagę niewidzialności tylko dla menu głównego. Po umieszczeniu tej samej grupy poleceń w menu kontekstowym lub podmenu polecenia są widoczne.

Jako część wspólnego wzorca rozszerzenie Prowadnice kolumn tworzy drugą grupę zawierającą pojedyncze podmenu. Podmenu z kolei zawiera pierwszą grupę z poleceniami przewodnika czterokolumnowego. Druga grupa, która posiada podmenu jest zasobów wielokrotnegoużytnia, które można umieścić w różnych menu kontekstowych, który umieszcza podmenu w tych menu kontekstowych.

### <a name="the-vsct-file"></a>Plik .vsct
Plik *vsct* deklaruje polecenia i dokąd idą, wraz z ikonami i tak dalej. Zastąp zawartość pliku *vsct* następującym kodem (wyjaśnionym poniżej):

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**identyfikatory GUID**. Aby program Visual Studio znaleźć programy obsługi poleceń i wywołać je, należy upewnić się, że identyfikator GUID pakietu zadeklarowany w pliku *ColumnGuideCommandsPackage.cs* (wygenerowany z szablonu elementu projektu) pasuje do identyfikatora GUID pakietu zadeklarowanego w pliku *vsct* (skopiowany z góry). Jeśli ponownie użyjesz tego przykładowego kodu, upewnij się, że masz inny identyfikator GUID, aby nie kolidować z innymi osobami, które mogły skopiować ten kod.

Znajdź ten wiersz w *ColumnGuideCommandsPackage.cs* i skopiuj identyfikator GUID między cudzysłowami:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Następnie wklej identyfikator GUID w pliku *vsct,* aby w `Symbols` deklaracjach było następująco:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Identyfikatory GUID dla zestawu poleceń i pliku obrazu mapy bitowej powinny być unikatowe dla rozszerzeń:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Ale nie trzeba zmieniać zestaw poleceń i identyfikatory GUID obrazu bitmapy w tym instruktażu, aby uzyskać kod do pracy. Identyfikator GUID zestawu poleceń musi być zgodny z deklaracją w pliku *ColumnGuideCommands.cs,* ale także zawartość tego pliku zostanie zastąpiona; w związku z tym identyfikatory GUID będą zgodne.

Inne identyfikatory GUID w pliku *vsct* identyfikują istniejące wcześniej menu, do których dodawane są polecenia przewodnika kolumn, dzięki czemu nigdy się nie zmieniają.

**Sekcje plików**. *.vsct* ma trzy zewnętrzne sekcje: polecenia, miejsca docelowe i symbole. Sekcja Polecenia definiuje grupy poleceń, menu, przyciski lub elementy menu oraz mapy bitowe ikon. Sekcja Miejsca docelowe deklaruje, gdzie grupy przechodzą do menu lub dodatkowych miejsc docelowych w istniejących menu. Sekcja symboli deklaruje identyfikatory używane w innym miejscu w pliku *vsct,* co sprawia, że kod *.vsct* jest bardziej czytelny niż identyfikatory GUID i numery szesnastkowe wszędzie.

**Sekcja Polecenia, definicje grup**. Sekcja polecenia najpierw definiuje grupy poleceń. Grupy poleceń to polecenia widoczne w menu z niewielkimi szarymi liniami oddzielającymi grupy. Grupa może również wypełnić całe podmenu, jak w tym przykładzie, a w tym przypadku nie widać szarych linii oddzielających. Pliki *.vsct* deklarują dwie `GuidesMenuItemsGroup` grupy, która jest `IDM_VS_MENU_EDIT` nadrzędna do (główne `GuidesContextMenuGroup` menu **Edycja)** `IDM_VS_CTXT_CODEWIN` i który jest nadrzędny do (menu kontekstowego edytora kodu).

Druga deklaracja grupy `0x0600` ma priorytet:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Chodzi o to, aby umieścić podmenu prowadnic kolumn na końcu dowolnego menu kontekstowego, do którego dodasz grupę podmenu. Ale nie należy zakładać, że wiesz najlepiej i życie podmenu, `0xFFFF`aby zawsze być ostatni za pomocą priorytetu . Musisz poeksperymentować z numerem, aby zobaczyć, gdzie znajduje się twoje podmenu w menu kontekstowym, w którym go umieszczasz. W tym `0x0600` przypadku jest wystarczająco wysoki, aby umieścić go na końcu menu, o ile widać, ale pozostawia miejsce dla kogoś innego, aby zaprojektować ich rozszerzenie być niższe niż rozszerzenie prowadnic kolumn, jeśli jest to pożądane.

**Poleceń, definicja menu**. Następnie sekcja poleceń definiuje podmenu `GuidesSubMenu`, `GuidesContextMenuGroup`nadrzędnego do . Jest `GuidesContextMenuGroup` to grupa dodana do wszystkich odpowiednich menu kontekstowych. W sekcji miejsca docelowe kod umieszcza grupę z czterokolumnowymi poleceniami przewodnika w tym podmenu.

**Poleceń, definicji przycisków**. Następnie sekcja polecenia definiuje elementy menu lub przyciski, które są poleceniami linii pomocniczych czterokolumnowych. `CommandWellOnly`, omówione powyżej, oznacza, że polecenia są niewidoczne po umieszczeniu w menu głównym. Dwie deklaracje przycisków elementu menu (dodaj przewodnik i `AllowParams` usuń prowadnicę) również mają flagę:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Ta flaga umożliwia, wraz z o umieszczenia menu głównego, polecenie, aby odbierać argumenty, gdy visual studio wywołuje program obsługi poleceń.  Jeśli użytkownik uruchamia polecenie z okna polecenia, argument jest przekazywany do programu obsługi poleceń w argumentach zdarzenia.

**Sekcje poleceń, definicje map bitowych**. Wreszcie sekcja poleceń deklaruje mapy bitowe lub ikony używane dla poleceń. Ta sekcja jest prostą deklaracją, która identyfikuje zasób projektu i zawiera listę indeksów opartych na jednej ikonach używanych. Sekcja symboli pliku *vsct* deklaruje wartości identyfikatorów używanych jako indeksy. W tym instruktażu użyto paska mapy bitowej dostarczonego z szablonem elementu polecenia niestandardowego dodanym do projektu.

**Sekcja Miejsca docelowe**. Po sekcji poleceń jest sekcja miejsc docelowych. Pierwszy z nich jest, gdy kod dodaje pierwszą grupę omówione powyżej, która zawiera polecenia przewodnika czterokolumnowego do podmenu, w którym pojawiają się polecenia:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Wszystkie inne miejsca docelowe `GuidesContextMenuGroup` dodać (który zawiera `GuidesSubMenu`) do innych menu kontekstowych edytora. Gdy kod zadeklarowany `GuidesContextMenuGroup`, był nadrzędny do menu kontekstowego edytora kodu. Dlatego nie widzisz miejsca docelowego menu kontekstowego edytora kodu.

**Sekcja Symbole**. Jak wspomniano powyżej, sekcja symboli deklaruje identyfikatory używane w innym miejscu w pliku *vsct,* co sprawia, że kod *.vsct* jest bardziej czytelny niż identyfikatory GUID i numery szesnastkowe wszędzie. Ważne punkty w tej sekcji są, że identyfikator GUID pakietu musi zgadzać się z deklaracją w klasie pakietu. I zestaw poleceń GUID musi zgadzać się z deklaracją w klasie implementacji polecenia.

## <a name="implement-the-commands"></a>Implementowanie poleceń
Plik *ColumnGuideCommands.cs* implementuje polecenia i łączy programy obsługi. Gdy Visual Studio ładuje pakiet i inicjuje `Initialize` go, pakiet z kolei wywołuje klasy implementacji poleceń. Inicjowanie poleceń po prostu tworzy wystąpienia klasy, a konstruktor łączy wszystkie programy obsługi poleceń.

Zastąp zawartość pliku *ColumnGuideCommands.cs* następującym kodem (wyjaśnionym poniżej):

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**Napraw odwołania**. W tym momencie brakuje ci odwołania. Naciśnij prawy przycisk wskaźnika w węźle Odwołania w Eksploratorze rozwiązań. Wybierz polecenie **Dodaj ....** Okno dialogowe **Dodaj odwołanie** ma pole wyszukiwania w prawym górnym rogu. Wpisz "editor" (bez podwójnych cudzysłowów). Wybierz element **Microsoft.VisualStudio.Editor** (należy zaznaczyć pole po lewej stronie elementu, a nie tylko zaznaczyć element) i wybierz **przycisk OK,** aby dodać odwołanie.

**Inicjowanie**.  Gdy klasa pakietu inicjuje, wywołuje `Initialize` na polecenia klasy implementacji. Inicjowanie `ColumnGuideCommands` wystąpienia klasy i zapisuje wystąpienie klasy i odwołanie do pakietu w członkach klasy.

Przyjrzyjmy się jednej z obsługi poleceń hook-up z konstruktora klasy:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Tworzysz `OleMenuCommand`plik . Program Visual Studio używa systemu poleceń pakietu Microsoft Office. Kluczowe argumenty podczas tworzenia `OleMenuCommand` wystąpienia jest funkcja, która`AddColumnGuideExecuted`implementuje polecenie ( ), funkcja do wywołania, gdy visual studio pokazuje menu z poleceniem (`AddColumnGuideBeforeQueryStatus`), i identyfikator polecenia. Visual Studio wywołuje funkcję stanu kwerendy przed wyświetleniem polecenia w menu, dzięki czemu polecenie może uczynić się niewidocznym lub wyszarzonym dla określonego wyświetlania menu (na przykład wyłączenie **kopiowania,** jeśli nie ma zaznaczenia), zmienić jego ikonę, a nawet zmienić jego nazwę (na przykład z Dodaj coś, aby coś usunąć) i tak dalej. Identyfikator polecenia musi być zgodny z identyfikatorem polecenia zadeklarowanym w pliku *vsct.* Ciągi dla zestawu poleceń i prowadnice kolumn dodają polecenie muszą być zgodne między plikiem *vsct* a *ColumnGuideCommands.cs*.

Poniższy wiersz zapewnia pomoc, gdy użytkownicy wywołać polecenie za pośrednictwem okna polecenia (wyjaśnione poniżej):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Stan kwerendy**. Funkcje stanu `AddColumnGuideBeforeQueryStatus` `RemoveColumnGuideBeforeQueryStatus` kwerendy i sprawdź niektóre ustawienia (takie jak maksymalna liczba linii pomocniczych lub maksymalna kolumna) lub jeśli istnieje przewodnik po kolumnach do usunięcia. Włączają polecenia, jeśli warunki są odpowiednie.  Funkcje stanu kwerendy muszą być wydajne, ponieważ są uruchamiane za każdym razem, gdy program Visual Studio wyświetla menu i dla każdego polecenia w menu.

 **AddColumnGuideWyjęta funkcja**. Interesującą częścią dodawania przewodnika jest ustalenie bieżącego widoku edytora i lokalizacji opiekunki.  Najpierw ta funkcja `GetApplicableColumn`wywołuje , który sprawdza, czy istnieje argument dostarczony przez użytkownika w argumentach zdarzeń programu obsługi poleceń, a jeśli nie ma, funkcja sprawdza widok edytora:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn`musi trochę kopać, aby <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> uzyskać widok kodu.  Jeśli prześledzisz , `GetActiveTextView` `GetActiveView`i `GetTextViewFromVsTextView`, możesz zobaczyć, jak to zrobić. Poniższy kod jest odpowiedni kod abstrakcyjne, począwszy od bieżącego zaznaczenia, a następnie coraz zaznaczenia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>ramki, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> a następnie coraz ramki DocView jako , a następnie coraz z IVsTextView, a następnie coraz hosta widoku, a na koniec IWpfTextView:

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

Po uzyskaniu widoku IWpfTextView można uzyskać kolumnę, w której znajduje się karetka:

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

Z bieżącą kolumną w ręku, w której użytkownik kliknął, kod po prostu wywołuje menedżera ustawień, aby dodać lub usunąć kolumnę. Menedżer ustawień uruchamia zdarzenie, `ColumnGuideAdornment` do którego nasłuchują wszystkie obiekty. Po uruchomieniu zdarzenia obiekty te aktualizują skojarzone widoki tekstu o nowe ustawienia przewodnika kolumn.

## <a name="invoke-command-from-the-command-window"></a>Wywoływanie polecenia z okna polecenia
Przykład prowadnic kolumn umożliwia użytkownikom wywoływanie dwóch poleceń z okna polecenia jako formy rozszerzalności. Jeśli używasz polecenia Widok &#124; inne okno **polecenia systemu Windows &#124;,** możesz wyświetlić okno polecenia. Możesz wchodzić w interakcje z oknem polecenia, wprowadzając "edytuj.", a wraz z zakończeniem nazwy polecenia i dostarczeniem argumentu 120, masz następujący wynik:

```csharp
> Edit.AddColumnGuide 120
>
```

Fragmenty próbki, które włączają to zachowanie znajdują się w `ColumnGuideCommands` deklaracjach plików *vsct,* konstruktorze klasy, gdy łączy programy obsługi poleceń, oraz implementacje programu obsługi poleceń, które sprawdzają argumenty zdarzeń.

""`<CommandFlag>CommandWellOnly</CommandFlag>`" w pliku *vsct,* a także miejsca docelowe w menu głównym **edycja,** nawet jeśli polecenia nie są wyświetlane w interfejsie interfejsu menu **Edycja.** Mając je w głównym menu **Edycji** daje im nazwy, takie jak **Edit.AddColumnGuide**. Deklaracja grupy poleceń zawierająca cztery polecenia umieściła grupę bezpośrednio w menu **Edycja:**

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Sekcja przycisków później zadeklarowała `CommandWellOnly` polecenia, aby były niewidoczne `AllowParams`w menu głównym i zadeklarowała je za pomocą:

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Program obsługi poleceń podłącz kod `ColumnGuideCommands` w konstruktorze klasy pod warunkiem opis dozwolonego parametru:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Przed sprawdzeniem `GetApplicableColumn` `OleMenuCmdEventArgs` widoku edytora dla bieżącej kolumny została wyświetlona funkcja sprawdza wartość:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="try-your-extension"></a>Wypróbuj rozszerzenie
Teraz możesz nacisnąć **klawisz F5,** aby wykonać rozszerzenie Prowadnice kolumn. Otwórz plik tekstowy i użyj menu kontekstowego edytora, aby dodać linie pomocnicze, usunąć je i zmienić ich kolor. Kliknij tekst (nie odstępy minęły koniec wiersza), aby dodać prowadnicę kolumn lub edytor dodaje go do ostatniej kolumny w wierszu. Jeśli używasz okna polecenia i wywołujesz polecenia za pomocą argumentu, możesz dodać prowadnice kolumn w dowolnym miejscu.

Jeśli chcesz wypróbować różne miejsca docelowe poleceń, zmienić nazwy, zmienić ikony i tak dalej, a masz jakiekolwiek problemy z visual studio pokazujący najnowszy kod w menu, można zresetować gałęzi eksperymentalnej, w którym są debugowania. Wyjdź z **menu Start systemu Windows** i wpisz "reset". Poszukaj i uruchom polecenie **Resetuj następne wystąpienie eksperymentalne programu Visual Studio**. To polecenie czyści eksperymentalny gałąź rejestru wszystkich składników rozszerzenia. Nie czyści ustawienia ze składników, więc wszelkie przewodniki, które miały po zamknięciu eksperymentalnego gałąź programu Visual Studio są nadal tam, gdy kod odczytuje magazynu ustawień przy następnym uruchomieniu.

## <a name="finished-code-project"></a>Gotowy projekt kodu
Wkrótce pojawi się projekt GitHub z przykładami rozszerzalności programu Visual Studio i ukończony projekt będzie tam. Ten artykuł zostanie zaktualizowany, aby wskazać, kiedy to się stanie. Ukończony przykładowy projekt może mieć różne identyfikatory guids i będzie miał inny pasek map bitowych dla ikon poleceń.

Możesz wypróbować wersję funkcji przewodników kolumn z tym[rozszerzeniem](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)Galerii programu Visual Studio .

## <a name="see-also"></a>Zobacz też
- [Wewnątrz edytora](../extensibility/inside-the-editor.md)
- [Rozszerzanie usług edytora i języka](../extensibility/extending-the-editor-and-language-services.md)
- [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Dodawanie podmenu do menu](../extensibility/adding-a-submenu-to-a-menu.md)
- [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)
