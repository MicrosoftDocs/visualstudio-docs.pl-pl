---
title: Tworzenie zakończenia, poleceń i ustawień widoku Microsoft Docs
description: Dowiedz się, jak rozciągnąć Edytor kodu programu Visual Studio za pomocą prowadnic kolumn, korzystając z tego przewodnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e0a2111aeb3f0e23cb2c03feadda8accd4a93e1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080453"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Przewodnik: Tworzenie zakończenia, poleceń i ustawień widoku (prowadnice kolumn)
Można rozwinąć Edytor tekstu/kodu programu Visual Studio za pomocą poleceń i efektów wyświetlania. W tym artykule pokazano, jak zacząć korzystać z popularnej funkcji rozszerzenia, prowadnic kolumn. Prowadnice kolumn są wizualnie jasne linie rysowane w widoku edytora tekstów, aby ułatwić zarządzanie kodem do określonych szerokości kolumn. W odniesieniu do kodu sformatowanego można zwrócić uwagę na przykłady dołączone do dokumentów, wpisów w blogu lub raportów o błędach.

W tym instruktażu zawarto następujące instrukcje:
- Tworzenie projektu VSIX
- Dodaj zakończenia definiowania widoku edytora
- Dodawanie obsługi zapisywania i pobierania ustawień (gdzie rysować prowadnice kolumn i ich kolory)
- Dodawanie poleceń (Dodawanie/usuwanie prowadnic kolumn, zmiana ich koloru)
- Umieść polecenia w menu Edytuj i w menu kontekstowym dokumentu tekstowego
- Dodawanie obsługi wywoływania poleceń z okna poleceń programu Visual Studio

  Możesz wypróbować wersję funkcji prowadnic kolumn za pomocą tego[rozszerzenia](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)galerii programu Visual Studio.

  > [!NOTE]
  > W tym instruktażu wklejasz doskonałe ilości kodu do kilku plików generowanych przez szablony rozszerzeń programu Visual Studio. Jednak wkrótce ten Instruktaż będzie odnosił się do kompletnego rozwiązania w witrynie GitHub z innymi przykładami rozszerzenia. Ukończony kod jest nieco inny w przypadku, gdy ma rzeczywiste ikony poleceń zamiast używania ikon generictemplate.

## <a name="get-started"></a>Rozpoczęcie pracy
Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Skonfiguruj rozwiązanie
Najpierw należy utworzyć projekt VSIX, dodać zakończenia definiowania widoku edytora, a następnie dodać polecenie (które dodaje pakietu VSPackage do polecenia). Podstawowa architektura jest następująca:
- Masz odbiornik tworzenia widoku tekstu, który tworzy `ColumnGuideAdornment` obiekt na widok. Ten obiekt nasłuchuje zdarzeń związanych z zmianami lub zmianami ustawień, aktualizowaniem lub odtwarzaniem linii kolumn w razie potrzeby.
- Jest to temat obsługujący `GuidesSettingsManager` odczytywanie i zapisywanie z magazynu ustawień programu Visual Studio. Menedżer ustawień ma również operacje aktualizowania ustawień, które obsługują polecenia użytkownika (Dodawanie kolumny, usuwanie kolumny, zmiana koloru).
- Istnieje pakiet VSIP, który jest niezbędny, jeśli masz polecenia użytkownika, ale jest to tylko kod standardowy, który inicjuje obiekt implementacji poleceń.
- Istnieje `ColumnGuideCommands` obiekt, który uruchamia polecenia użytkownika i łączy procedury obsługi poleceń zadeklarowanych w pliku *. vsct* .

  **VSIX**. Użyj polecenia **File &#124; New...** , aby utworzyć projekt. Wybierz węzeł **rozszerzalności** w obszarze **C#** w lewym okienku nawigacji, a następnie wybierz **Projekt VSIX** w okienku po prawej stronie. Wprowadź nazwę **ColumnGuides** i wybierz **przycisk OK** , aby utworzyć projekt.

  **Wyświetl moduł definiowania** układu. Naciśnij przycisk prawy wskaźnik w węźle projektu w Eksplorator rozwiązań. Wybierz polecenie **dodaj &#124; nowy element...** , aby dodać nowy element zakończenia widoku. Wybierz pozycję **rozszerzalność &#124; Edytor** w lewym okienku nawigacji, a następnie wybierz pozycję **Edytor definiowania okienka ekranu edytora** w okienku po prawej stronie. Wprowadź nazwę **ColumnGuideAdornment** jako nazwę elementu, a następnie wybierz pozycję **Dodaj** , aby ją dodać.

  Można zobaczyć, że ten szablon elementu dodał dwa pliki do projektu (jak również odwołania i tak dalej): **ColumnGuideAdornment. cs** i **ColumnGuideAdornmentTextViewCreationListener. cs**. Szablony rysują purpurowy prostokąt w widoku. W poniższej sekcji zmienisz kilka wierszy w odbiorniku tworzenia widoku i zastąpisz zawartość **ColumnGuideAdornment. cs**.

  **Polecenia**. W **Eksplorator rozwiązań** naciśnij przycisk prawy wskaźnik w węźle projektu. Wybierz polecenie **dodaj &#124; nowy element...** , aby dodać nowy element zakończenia widoku. Wybierz pozycję **rozszerzalność &#124; pakietu VSPackage** w lewym okienku nawigacji, a następnie w okienku po prawej stronie wybierz **polecenie niestandardowe** . Wprowadź nazwę **ColumnGuideCommands** jako nazwę elementu, a następnie wybierz pozycję **Dodaj**. Oprócz kilku odwołań, dodanie poleceń i pakietu również dodaliśmy **ColumnGuideCommands. cs**, **ColumnGuideCommandsPackage. cs** i **ColumnGuideCommandsPackage. vsct**. W poniższej sekcji zastąpisz zawartość pierwszego i ostatniego pliku w celu zdefiniowania i zaimplementowania poleceń.

## <a name="set-up-the-text-view-creation-listener"></a>Konfigurowanie odbiornika tworzenia widoku tekstu
Otwórz *ColumnGuideAdornmentTextViewCreationListener. cs* w edytorze. Ten kod implementuje procedurę obsługi dla każdego programu Visual Studio tworzącego widoki tekstu. Istnieją atrybuty kontrolujące, kiedy program obsługi jest wywoływany w zależności od właściwości widoku.

Kod musi również deklarować warstwę definiowania układu. Gdy Edytor aktualizuje widoki, pobiera warstwy zakończenia dla widoku i Pobiera elementy z układu. Można zadeklarować porządkowanie warstwy względem innych atrybutów. Zastąp następujący wiersz:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

z tymi dwoma wierszami:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Zamieniony wiersz znajduje się w grupie atrybutów, która deklaruje warstwę definiowania układu. Pierwszy zmieniony wiersz jest zmieniany tylko wtedy, gdy pojawiają się linie prowadnic kolumn. Rysowanie linii przed tekstem w widoku oznacza, że są one wyświetlane w tle lub poniżej tekstu. Druga linia deklaruje, że elementy definiowania układu wiersza są stosowane do jednostek tekstowych, które pasują do Twojego charakteru dokumentu, ale można zadeklarować, aby na przykład, aby działał tylko do edycji tekstu. Więcej informacji znajduje się w [punktach rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>Implementowanie Menedżera ustawień
Zamień zawartość *GuidesSettingsManager. cs* na następujący kod (wyjaśniony poniżej):

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

Większość tego kodu tworzy i analizuje format ustawień: "RGB ( \<int> , \<int> , \<int> ) \<int> , \<int> ,...".  Liczby całkowite na końcu są kolumnami, w których mają być prowadnice kolumn. Rozszerzenie prowadnice kolumn przechwytuje wszystkie jego ustawienia w ciągu wartości pojedynczego ustawienia.

Niektóre części kodu są wyróżniane. Poniższy wiersz kodu pobiera otokę zarządzaną programu Visual Studio dla magazynu ustawień. W większości przypadków jest to streszczenie za pośrednictwem rejestru systemu Windows, ale ten interfejs API jest niezależny od mechanizmu magazynu.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Magazyn ustawień programu Visual Studio używa identyfikatora kategorii i identyfikatora ustawienia do unikatowego identyfikowania wszystkich ustawień:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Nie musisz używać `"Text Editor"` jako nazwy kategorii. Możesz wybrać dowolną zawartość.

Pierwsze kilka funkcji to punkty wejścia, które umożliwiają zmianę ustawień. Sprawdzają one ograniczenia wysokiego poziomu, takie jak maksymalną dozwoloną liczbę przewodników.  Następnie wywołuje `WriteSettings` , które tworzą ciąg ustawień i ustawia właściwość `GuideLinesConfiguration` . Ustawienie tej właściwości zapisuje wartość ustawienia w sklepie ustawień programu Visual Studio i wyzwala `SettingsChanged` zdarzenie, aby zaktualizować wszystkie `ColumnGuideAdornment` obiekty, z których każda jest skojarzona z widokiem tekstu.

Istnieje kilka funkcji punktu wejścia, takich jak `CanAddGuideline` , które są używane do implementowania poleceń zmieniających ustawienia. Gdy program Visual Studio Wyświetla menu, wykonuje zapytania dotyczące implementacji poleceń, aby sprawdzić, czy polecenie jest aktualnie włączone, jakie jego nazwy i tak dalej.  Poniżej widać, jak podłączyć te punkty wejścia dla implementacji poleceń. Aby uzyskać więcej informacji na temat poleceń, zobacz sekcję [poszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementowanie klasy ColumnGuideAdornment
`ColumnGuideAdornment`Klasa jest tworzona dla każdego widoku tekstu, który może mieć potrzeby definiowania układu. Ta klasa nasłuchuje zdarzeń dotyczących zmiany lub zmieniania widoku, a także do aktualizowania lub przerysowania w miarę potrzeb.

Zamień zawartość *ColumnGuideAdornment. cs* na następujący kod (wyjaśniony poniżej):

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

Wystąpienia tej klasy są przechowywane na skojarzonych <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> i listach `Line` obiektów rysowanych w widoku.

Konstruktor (wywoływany przez `ColumnGuideAdornmentTextViewCreationListener` program Visual Studio tworzy nowe widoki) tworzy obiekty prowadnic kolumn `Line` .  Konstruktor dodaje również procedury obsługi dla `SettingsChanged` zdarzenia (zdefiniowane w `GuidesSettingsManager` ) oraz Wyświetl zdarzenia `LayoutChanged` i `Closed` .

`LayoutChanged`Zdarzenie wyzwalane z powodu kilku rodzajów zmian w widoku, w tym gdy program Visual Studio tworzy widok. `OnViewLayoutChanged`Procedura obsługi wywołuje `AddGuidelinesToAdornmentLayer` do wykonania. Kod w programie `OnViewLayoutChanged` określa, czy musi zaktualizować pozycje wierszy na podstawie zmian, takich jak zmiany rozmiaru czcionki, wyświetlanie odstępów, przewijanie w poziomie itd. Kod w `UpdatePositions` powoduje, że linie prowadnic są rysowane między znakami lub tuż po kolumnie tekstu, która znajduje się w przesunięciu określonego znaku w wierszu tekstu.

Za każdym razem, gdy ustawienia zmienią się, `SettingsChanged` Funkcja po prostu ponownie tworzy wszystkie `Line` obiekty, niezależnie od tego, jakie są nowe ustawienia. Po ustawieniu pozycji wiersza kod usuwa wszystkie poprzednie `Line` obiekty z `ColumnGuideAdornment` warstwy zakończenia i dodaje nowe.

## <a name="define-the-commands-menus-and-menu-placements"></a>Definiowanie poleceń, menu i rozmieszczeń menu
Może istnieć wiele do deklarowania poleceń i menu, umieszczania grup poleceń lub menu w różnych innych menu i podłączania obsługi poleceń. W tym instruktażu przedstawiono sposób działania poleceń w tym rozszerzeniu, ale aby uzyskać bardziej szczegółowe informacje, zobacz [rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Wprowadzenie do kodu
Rozszerzenie prowadnice kolumn pokazuje deklarację grupy poleceń, które należą do siebie (Dodaj kolumnę, Usuń kolumnę, Zmień kolor linii), a następnie umieszczaj tę grupę w podmenu menu kontekstowego edytora.  Rozszerzenie prowadnice kolumn dodaje również polecenia do głównego menu **edycji** , ale utrzymuje je niewidoczne, omówione jako wspólny wzorzec poniżej.

Istnieją trzy części implementacji poleceń: ColumnGuideCommandsPackage. cs, ColumnGuideCommandsPackage. vsct i ColumnGuideCommands. cs. Kod generowany przez szablony umieszcza polecenie w menu **Narzędzia** , które jest podskakujące okna dialogowego jako implementacji. Możesz sprawdzić, jak to jest zaimplementowane w plikach *. vsct* i *ColumnGuideCommands. cs* , ponieważ jest to proste. Zastąp kod w poniższych plikach poniżej.

Kod pakietu zawiera zwyczajowe deklaracje wymagane przez program Visual Studio do odnajdowania, że rozszerzenie oferuje polecenia i aby znaleźć miejsce umieszczenia poleceń. Gdy pakiet inicjuje, tworzy wystąpienie klasy implementacji poleceń. Aby uzyskać więcej informacji na temat pakietów związanych z poleceniami, zobacz sekcję [rozszerzając menu i polecenia](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Wzorzec typowych poleceń
Polecenia w rozszerzeniu prowadnic kolumn są przykładem bardzo wspólnego wzorca w programie Visual Studio. Pokrewnych poleceń należy umieścić w grupie i umieścić tę grupę w menu głównym, często z " `<CommandFlag>CommandWellOnly</CommandFlag>` " ustawionym niewidocznym poleceniem.  Umieszczenie poleceń w menu głównym (na przykład **Edit**) daje im dobre nazwy (na przykład **Edit. AddColumnGuide**), które są przydatne do znajdowania poleceń podczas ponownego przypisywania powiązań kluczy w **opcjach narzędzi**. Jest on również przydatny do uzyskiwania zakończenia podczas wywoływania poleceń z **okna poleceń**.

Następnie można dodać grupę poleceń do menu kontekstowego lub podmenu, w których użytkownik będzie oczekiwał na korzystanie z poleceń. Program Visual Studio traktuje `CommandWellOnly` jako flagę niewidzialną tylko dla głównych menu. Po umieszczeniu tej samej grupy poleceń w menu kontekstowym lub podmenu polecenia są widoczne.

W ramach wspólnego wzorca rozszerzenie prowadnice kolumn tworzy drugą grupę, która zawiera pojedyncze podmenu. Podmenu z kolei zawiera pierwszą grupę z poleceniami z czterema kolumnami. Drugą grupą zawierającą podmenu jest zasób wielokrotnego użytku, który jest umieszczany w różnych menu kontekstowym, co powoduje umieszczenie podmenu w tych menu kontekstowym.

### <a name="the-vsct-file"></a>Plik. vsct
Plik *vsct* deklaruje polecenia i miejsce, w którym się znajdują, wraz z ikonami i tak dalej. Zastąp zawartość pliku *. vsct* następującym kodem (wyjaśnionym poniżej):

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

**Identyfikatory GUID**. Aby program Visual Studio mógł znaleźć programy obsługi poleceń i wywoływać je, należy upewnić się, że identyfikator GUID pakietu zadeklarowany w pliku *ColumnGuideCommandsPackage. cs* (wygenerowany na podstawie szablonu elementu projektu) jest zgodny z identyfikatorem GUID pakietu zadeklarowanym w pliku *. vsct* (skopiowany z powyżej). Jeśli ponownie używasz tego przykładowego kodu, upewnij się, że masz inny identyfikator GUID, aby nie powodować konfliktu z innymi osobami, które mogły skopiować ten kod.

Znajdź ten wiersz w *ColumnGuideCommandsPackage. cs* i skopiuj identyfikator GUID z między znakami cudzysłowu:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Następnie wklej identyfikator GUID w pliku *vsct* , tak aby zawierał następujący wiersz w `Symbols` deklaracjach:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Identyfikatory GUID dla zestawu poleceń i pliku obrazu mapy bitowej powinny być również unikatowe dla swoich rozszerzeń:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Jednak w tym instruktażu nie trzeba zmieniać identyfikatorów GUID zestawu poleceń i obrazów map bitowych, aby kod działał. Identyfikator GUID zestawu poleceń musi być zgodny z deklaracją w pliku *ColumnGuideCommands. cs* , ale jest również zastępowany zawartością tego pliku; w związku z tym identyfikatory GUID będą zgodne.

Inne identyfikatory GUID w pliku *. vsct* identyfikują istniejące wcześniej menu, do których dodawane są polecenia w przewodniku kolumny, więc nigdy nie ulegną zmianie.

**Sekcje plików**. *. Vsct* ma trzy sekcje zewnętrzne: polecenia, rozmieszczenia i symbole. Sekcja Commands definiuje grupy poleceń, menu, przyciski lub elementy menu oraz mapy bitowe dla ikon. Sekcja umieszczania deklaruje, gdzie grupy przechodzą do menu lub dodatkowe umieszczanie na istniejących menu. Sekcja symboli deklaruje identyfikatory używane w innym miejscu w pliku *. vsct* , co sprawia, że kod *vsct* jest bardziej czytelny niż identyfikatory GUID i numery szesnastkowe wszędzie.

**Sekcja poleceń, definicje grup**. Sekcja Commands najpierw definiuje grupy poleceń. Grupy poleceń są poleceniami wyświetlanymi w menu z niewielkimi szarymi liniami oddzielającymi grupy. Grupa może również wypełnić całe podmenu, jak w tym przykładzie, i w tym przypadku nie są widoczne szare linie oddzielające. Pliki *. vsct* deklarują dwie grupy, `GuidesMenuItemsGroup` które są nadrzędne dla `IDM_VS_MENU_EDIT` (głównego menu **edycji** ) i `GuidesContextMenuGroup` które są nadrzędne względem `IDM_VS_CTXT_CODEWIN` (menu kontekstowe edytora kodu).

Druga deklaracja grupy ma `0x0600` priorytet:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Pomysłem jest umieszczenie podmenu prowadnic kolumn na końcu dowolnego menu kontekstowego, do którego zostanie dodana grupa podmenu. Nie zaleca się jednak, aby wiadomo, że najlepiej i wymusić podmenu zawsze przy użyciu priorytetu `0xFFFF` . Musisz eksperymentować z liczbą, aby zobaczyć, gdzie Twoje menu podrzędne znajduje się w menu kontekstowym, w którym je umieścisz. W tym przypadku `0x0600` jest wystarczająco duży, aby umieścić go na końcu menu, o ile widzisz, ale pozostawia miejsce dla kogoś innego, że jego rozszerzenie jest niższe niż rozszerzenie prowadnic kolumn, jeśli jest to wymagane.

**Sekcja poleceń, definicja menu**. Następnie sekcja Command definiuje podmenu `GuidesSubMenu` , które jest nadrzędne względem `GuidesContextMenuGroup` . `GuidesContextMenuGroup`Jest to grupa dodawana do wszystkich odpowiednich menu kontekstowych. W sekcji umieszczania kod umieszcza grupę z poleceniami z czterema kolumnami w tym podmenu.

**Sekcja poleceń, definicje przycisków**. Sekcja Commands następnie definiuje elementy menu lub przyciski, które są poleceniami z czterema kolumnami. `CommandWellOnly`, omówione powyżej, oznacza, że polecenia są niewidoczne po umieszczeniu w menu głównym. Dwie deklaracje przycisków elementów menu (Dodawanie przewodnika i usuwanie przewodnika) również mają `AllowParams` flagę:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Ta flaga włącza, wraz z umieszczaniem menu głównego, polecenie do odbierania argumentów, gdy program Visual Studio wywołuje procedurę obsługi poleceń.  Jeśli użytkownik uruchamia polecenie z okna polecenia, argument jest przenoszona do procedury obsługi poleceń w argumentach zdarzeń.

**Sekcje poleceń, definicje map bitowych**. Na koniec sekcja Commands deklaruje mapy bitowe lub ikony używane dla poleceń. Ta sekcja jest prostą deklaracją, która identyfikuje zasób projektu i wyświetla na podstawie jednego indeksu używanych ikon. Sekcja symboli pliku *. vsct* deklaruje wartości identyfikatorów używanych jako indeksy. W tym instruktażu zostanie użyty pasek mapy bitowej dostarczony z szablonem elementu polecenia niestandardowego dodanym do projektu.

**Sekcja umieszczania**. Po sekcji poleceń znajduje się sekcja umieszczania. Pierwszy z nich to miejsce, w którym kod dodaje pierwszą grupę omówioną powyżej, która zawiera polecenia z czterema kolumnami w podmenu, w którym są wyświetlane polecenia:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Wszystkie inne rozmieszczenia Dodaj `GuidesContextMenuGroup` (który zawiera `GuidesSubMenu` ) do innych menu kontekstowych edytora. Gdy kod zadeklarowany `GuidesContextMenuGroup` , został on nadrzędny w menu kontekstowym edytora kodu. Dlatego nie widzisz położenia menu kontekstowego edytora kodu.

**Sekcja symboli**. Jak wspomniano powyżej, sekcja symboli deklaruje identyfikatory używane w innym miejscu w pliku *. vsct* , co sprawia, że kod *vsct* jest bardziej czytelny niż identyfikatory GUID i numery szesnastkowe wszędzie. Ważne punkty w tej sekcji, że identyfikator GUID pakietu musi zgadzać się z deklaracją w klasie pakietu. I, identyfikator GUID zestawu poleceń musi zgadzać się z deklaracją w klasie implementacji polecenia.

## <a name="implement-the-commands"></a>Implementowanie poleceń
Plik *ColumnGuideCommands. cs* implementuje polecenia i przechwytuje programy obsługi. Gdy program Visual Studio ładuje pakiet i inicjuje go, pakiet z kolei wywołuje wywołania `Initialize` klasy implementacji poleceń. Inicjowanie poleceń po prostu tworzy wystąpienie klasy, a Konstruktor łączy wszystkie programy obsługi poleceń.

Zastąp zawartość pliku *ColumnGuideCommands. cs* następującym kodem (wyjaśnioną poniżej):

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

**Napraw odwołania**. Brak odwołania w tym punkcie. Naciśnij przycisk prawy wskaźnik w węźle odwołania w Eksplorator rozwiązań. Wybierz polecenie **Dodaj...** . Okno dialogowe **Dodawanie odwołania** zawiera pole wyszukiwania w prawym górnym rogu. Wprowadź "Edytor" (bez cudzysłowów). Wybierz element **Microsoft. VisualStudio. Editor** (musisz zaznaczyć pole z lewej strony, a nie tylko zaznaczyć element) i wybierz **przycisk OK** , aby dodać odwołanie.

**Inicjowanie**.  Po zainicjowaniu klasy pakietu wywołuje ona `Initialize` klasy implementacji poleceń. `ColumnGuideCommands`Inicjalizacja tworzy wystąpienie klasy i zapisuje wystąpienie klasy oraz odwołanie do pakietu w elementach członkowskich klasy.

Przyjrzyjmy się jednemu z punktów zaczepienia procedury obsługi poleceń z konstruktora klasy:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Tworzysz `OleMenuCommand` . Program Visual Studio używa systemu poleceń Microsoft Office. Argumenty klucza podczas tworzenia wystąpienia elementu `OleMenuCommand` to funkcja implementująca polecenie ( `AddColumnGuideExecuted` ), funkcja wywoływana, gdy program Visual Studio wyświetli menu z poleceniem ( `AddColumnGuideBeforeQueryStatus` ) i identyfikatorem polecenia. Program Visual Studio wywołuje funkcję stanu zapytania przed wyświetleniem polecenia w menu, dzięki czemu polecenie może być niewidoczne lub wyszarzone dla określonego wyświetlenia menu (na przykład wyłączenie **kopiowania** , jeśli nie ma zaznaczenia), zmiana jego ikony lub zmiana jego nazwy (na przykład w celu usunięcia czegoś) itd. Identyfikator polecenia musi być zgodny z IDENTYFIKATORem polecenia zadeklarowanym w pliku *. vsct* . Ciągi dla zestawu poleceń i prowadnic kolumn Dodaj polecenie musi być zgodne między plikiem *. vsct* a *ColumnGuideCommands. cs*.

Poniższy wiersz zawiera pomoc w przypadku, gdy użytkownicy wywołują polecenie za pomocą okna polecenia (wyjaśniono poniżej):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Stan zapytania**. Stan zapytania działa `AddColumnGuideBeforeQueryStatus` i `RemoveColumnGuideBeforeQueryStatus` sprawdza niektóre ustawienia (na przykład maksymalną liczbę przewodników lub maks. kolumna) lub jeśli istnieje Przewodnik po kolumnie do usunięcia. Umożliwiają one włączenie poleceń, jeśli warunki są odpowiednie.  Funkcje stanu zapytań muszą być wydajne, ponieważ są uruchamiane za każdym razem, gdy program Visual Studio wyświetli menu i dla każdego polecenia w menu.

 **Funkcja AddColumnGuideExecuted**. Interesująca część dodawania przewodnika obejmuje bieżący widok edytora i lokalizację karetki.  Najpierw ta funkcja wywołuje funkcję `GetApplicableColumn` , która sprawdza, czy w argumentach zdarzeń programu obsługi poleceń znajduje się argument podany przez użytkownika, a w przypadku braku wartości funkcja sprawdza widok edytora:

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

`GetCurrentEditorColumn` musi Dig trochę, aby uzyskać <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> wgląd w kod.  W przypadku śledzenia przez `GetActiveTextView` , `GetActiveView` , i `GetTextViewFromVsTextView` , można zobaczyć, jak to zrobić. Poniższy kod jest podzielnym kodem, rozpoczynając od bieżącego zaznaczenia, a następnie pobierając ramkę zaznaczenia, a następnie pobierając DocView ramki jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , a następnie pobierając <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> z IVsTextView, a następnie pobierając hosta widoku i na końcu element iwpftextview:

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

Po utworzeniu elementu element iwpftextview można uzyskać kolumnę, w której znajduje się znak daszka:

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

Z bieżącą kolumną, w której kliknięto użytkownik, kod jest wywoływany przez Menedżera ustawień w celu dodania lub usunięcia kolumny. Menedżer ustawień uruchamia zdarzenie, do którego wszystkie `ColumnGuideAdornment` obiekty nasłuchują. Po wygenerowanej zdarzeniu te obiekty aktualizują skojarzone z nimi widoki tekstowe przy użyciu nowych ustawień prowadnic kolumn.

## <a name="invoke-command-from-the-command-window"></a>Invoke polecenie z okna polecenia
Przykładowa prowadnice kolumn umożliwia użytkownikom wywoływanie dwóch poleceń z okna poleceń jako formy rozszerzalności. Jeśli używasz **widoku &#124; inne polecenie okna polecenia systemu Windows &#124;** , zobaczysz okno polecenia. Można korzystać z okna polecenia, wprowadzając "Edytuj." i z uzupełnianiem nazwy polecenia i dostarczając argument 120, masz następujące wyniki:

```csharp
> Edit.AddColumnGuide 120
>
```

Fragmenty próbki, które umożliwiają włączenie tego zachowania, są w deklaracjach pliku *. vsct* , `ColumnGuideCommands` konstruktorze klasy po podłączaniu obsługi poleceń i implementacji obsługi poleceń, które sprawdzają argumenty zdarzeń.

Zobaczysz " `<CommandFlag>CommandWellOnly</CommandFlag>` " w pliku *. vsct* , a także umieszczamy w menu **Edytuj** główne, mimo że polecenia nie są wyświetlane w interfejsie użytkownika menu **Edycja** . Ich udostępnienie w głównym menu **edycji** daje im nazwy, takie jak **Edit. AddColumnGuide**. Deklaracja grupy poleceń, która przechowuje cztery polecenia umieszczane w grupie w menu **Edytuj** :

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Sekcja przyciski później deklaruje polecenia, `CommandWellOnly` aby nie były widoczne w menu głównym i zostały zadeklarowane przy użyciu `AllowParams` :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

W konstruktorze klasy został wystawiony kod podłączany przez procedurę obsługi poleceń `ColumnGuideCommands` :

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

`GetApplicableColumn`Funkcja sprawdza `OleMenuCmdEventArgs` wartość przed sprawdzeniem widoku edytora dla bieżącej kolumny:

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

## <a name="try-your-extension"></a>Wypróbuj swoje rozszerzenie
Teraz możesz nacisnąć klawisz **F5** , aby uruchomić rozszerzenie prowadnic kolumn. Otwórz plik tekstowy i użyj menu kontekstowego edytora, aby dodać linie prowadnicy, usunąć je i zmienić kolor. Kliknij tekst (nie przeszedł spacji do końca wiersza), aby dodać prowadnicę kolumny, lub Edytor dodaje go do ostatniej kolumny w wierszu. Jeśli używasz okna poleceń i wywołajesz polecenia z argumentem, możesz dodać prowadnice kolumn w dowolnym miejscu.

Jeśli chcesz wypróbować inne elementy poleceń, zmienić nazwy, zmienić ikony itd. i masz problemy z programem Visual Studio z wyświetlaniem najnowszego kodu w menu, możesz zresetować nieeksperymentalną gałąź, w której ma zostać wykonane debugowanie. Wyświetl **menu Start systemu Windows** i wpisz "reset". Wyszukaj i uruchom polecenie, **Zresetuj następne wystąpienie eksperymentalne programu Visual Studio**. To polecenie powoduje wyczyszczenie eksperymentalnej gałęzi rejestru wszystkich składników rozszerzenia. Nie czyści ustawień z składników, dlatego wszystkie prowadnice, które miały miejsce podczas zamykania eksperymentalnego programu Visual Studio, są nadal dostępne, gdy kod odczytuje magazyn ustawień przy następnym uruchomieniu.

## <a name="finished-code-project"></a>Zakończono projekt kodu
Wkrótce będzie dostępny projekt GitHub przykładów rozszerzalności programu Visual Studio i ukończony projekt będzie tam dostępny. Ten artykuł zostanie zaktualizowany w taki sposób, aby wskazywał. Ukończony przykładowy projekt może mieć różne identyfikatory GUID i będzie mieć inny pasek mapy bitowej dla ikon poleceń.

Możesz wypróbować wersję funkcji prowadnic kolumn za pomocą tego[rozszerzenia](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)galerii programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Wewnątrz edytora](../extensibility/inside-the-editor.md)
- [Poszerzanie edytora i usług językowych](../extensibility/extending-the-editor-and-language-services.md)
- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
- [Poszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Dodawanie podmenu do menu](../extensibility/adding-a-submenu-to-a-menu.md)
- [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)
