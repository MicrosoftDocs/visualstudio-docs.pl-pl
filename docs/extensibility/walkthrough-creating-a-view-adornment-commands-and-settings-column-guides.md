---
title: Tworzenie widoku zakończeń, poleceń i ustawień | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39d3385b56e35018093ceaaf26472d425847b100
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947418"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Przewodnik: Utwórz widok zakończeń, poleceń i ustawień (prowadnice kolumn)
Możesz rozszerzyć o edytorze tekstu/kodu programu Visual Studio z poleceniami i efekty widoku. W tym artykule pokazano, jak rozpocząć pracę z funkcją popularne rozszerzenie prowadnice kolumn. Prowadnice kolumn są wizualnie światła linii w widoku edytora tekstów w celu zarządzania swój kod, aby szerokości kolumn określonych. W szczególności sformatowany kod może być ważne dla przykładów dokumentów, wpisów w blogu lub raporty o błędach.

W tym przewodniku możesz:
- Create a VSIX project
- Dodaj zakończeń widoku edytora
- Dodano obsługę zapisywanie i pobieranie ustawień (w przypadku gdy w celu ich kolor i Rysuj prowadnice kolumn)
- Dodawanie poleceń (Dodawanie/usuwanie kolumn, zmienianie ich koloru)
- Umieść poleceń w menu Edycja i menu kontekstowe dokumentu tekstowego
- Dodano obsługę wywoływania poleceń w oknie polecenia programu Visual Studio  
  
  Możesz wypróbować wersję funkcji prowadnice kolumn z tej galerii Visual Studio[rozszerzenia](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines).  
  
  **UWAGA**: W tym przewodniku dużą ilość kodu Wklej kilka plików, generowane przez Szablony rozszerzenia programu Visual Studio. Ale wkrótce w tym przewodniku będzie odnosił się do ukończone rozwiązanie w witrynie GitHub wraz z innymi przykładami rozszerzenia. Kompletny kod jest nieco inne w zawierającym ikony poleceń rzeczywiste zamiast generictemplate ikony.

## <a name="get-started"></a>Wprowadzenie
Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Konfigurowanie rozwiązania
Najpierw utwórz projekt VSIX, Dodaj zakończeń widoku edytora, a następnie dodaj polecenie (które dodaje VSPackage, być właścicielem polecenie). Podstawowa architektura jest następująca:
- Masz odbiornik tworzenia widoku tekstu, który tworzy `ColumnGuideAdornment` obiekt widoku. Ten obiekt będzie nasłuchiwać pod kątem zdarzeń o zmienianiu widoku lub zmianę ustawienia, aktualizacji lub ponownego narysowania kolumna zawiera informacje na temat zgodnie z potrzebami.
- Brak `GuidesSettingsManager` obsługująca odczytu i zapisu z magazynu ustawień programu Visual Studio. Menedżer ustawień są również operacje aktualizowania ustawień, które obsługują polecenia użytkownika (Dodaj kolumnę, usunąć kolumny, zmienić kolor).
- Dostępny jest pakiet VSIP, które są niezbędne, jeśli masz poleceń użytkownika, ale jest po prostu standardowy kod, który inicjuje obiekt poleceń w implementacji.
- Brak `ColumnGuideCommands` obiekt, który użytkownik uruchamia polecenia i przechwytuje się programy obsługi poleceń dla polecenia zadeklarowanych w *vsct* pliku.  
  
  **VSIX**. Użyj **pliku &#124; nowy...**  polecenie, aby utworzyć projekt. Wybierz **rozszerzalności** węźle **C#** w okienku nawigacji po lewej stronie i wybierz polecenie **projekt VSIX** w okienku po prawej stronie. Wprowadź nazwę **ColumnGuides** i wybierz polecenie **OK** do tworzenia projektu.  
  
  **Wyświetl zakończeń**. Naciśnij przycisk prawo wskaźnika na węzeł projektu w Eksploratorze rozwiązań. Wybierz **Dodaj &#124; nowy element...**  polecenie, aby dodać nowy element zakończeń widoku. Wybierz **rozszerzalności &#124; edytora** w okienku nawigacji po lewej stronie i wybierz polecenie **zakończeń okienka ekranu edytora** w okienku po prawej stronie. Wprowadź nazwę **ColumnGuideAdornment** jako element nazwę, a następnie wybierz **Dodaj** ją dodać.  
  
  Widać, że ten szablon elementu dodane dwa pliki do projektu (także odwołania i tak dalej): **ColumnGuideAdornment.cs** i **ColumnGuideAdornmentTextViewCreationListener.cs**. Szablony narysuj prostokąt purpurowy w widoku. W poniższej sekcji, możesz zmienić kilka wierszy w widoku odbiornika tworzenia i Zastąp zawartość **ColumnGuideAdornment.cs**.  
  
  **Polecenia**. W **Eksploratora rozwiązań**, naciśnij przycisk prawo wskaźnika w węźle projektu. Wybierz **Dodaj &#124; nowy element...**  polecenie, aby dodać nowy element zakończeń widoku. Wybierz **rozszerzalności &#124; pakietu VSPackage** w okienku nawigacji po lewej stronie i wybierz polecenie **polecenia niestandardowego** w okienku po prawej stronie. Wprowadź nazwę **ColumnGuideCommands** jako element nazwę, a następnie wybierz **Dodaj**. Oprócz kilka odwołań, dodawanie poleceń i pakiet dodano także **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**, i **ColumnGuideCommandsPackage.vsct** . W poniższej sekcji można zastąpić zawartość plików imię i nazwisko, definiować ani implementować poleceń.

## <a name="set-up-the-text-view-creation-listener"></a>Konfigurowanie odbiornika tworzenia widoku tekstu
Otwórz *ColumnGuideAdornmentTextViewCreationListener.cs* w edytorze. Ten kod implementuje program obsługi, aby zawsze, gdy program Visual Studio tworzy widoki tekstowe. Brak atrybutów, które kontrolują, gdy program obsługi jest wywoływana w zależności od charakterystyki widoku.

Kod musi zadeklarować warstwy zakończeń. Gdy Edytor aktualizuje widoków, pobiera warstwy zakończeń widoku i przy jego użyciu pobiera elementy zakończeń. Można zadeklarować porządkowanie warstwą względem innych użytkowników za pomocą atrybutów. Zastąp następujący wiersz:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

za pomocą tych dwóch wierszy:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Wiersz, który został zastąpiony znajduje się w grupie atrybutów, które deklarują warstwy zakończeń. Pierwszy wiersz po zmianie tylko zmiany, w których występują linie prowadnic kolumny. Rysowanie linii "przed" tekst w widoku oznacza, że pojawiają się za zaporą lub pod tekstem. Drugi wiersz deklaruje, że zakończeń przewodnik kolumny mają zastosowanie do jednostek tekstu, spełniające Twoje notacji dokumentu, ale można zadeklarować zakończeń, na przykład, można używać tylko w przypadku tekst do edycji. Brak informacji [punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>Implementowanie Menedżera ustawień
Zastąp zawartość *GuidesSettingsManager.cs* następującym kodem (opisana poniżej):

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

Większość ten kod tworzy i analizuje format ustawień: "RGB (\<int >,\<int >,\<int >) \<int >, \<int >,...".  Liczby całkowite na końcu są liczonego od jednego kolumny, której chcesz prowadnice kolumn. Rozszerzenie prowadnice kolumn przechwytuje wszystkie jej ustawienia w ciągu wartości pojedynczego ustawienia.

Brak niektórych części kodu, które warto wyróżniania. Następujący wiersz kodu pobiera otoka zarządzana programu Visual Studio do przechowywania ustawień. W większości przypadków to przenosi w rejestrze systemu Windows, ale ten interfejs API jest niezależny od mechanizm magazynu.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Magazynu ustawienia programu Visual Studio używa identyfikatora kategorii i identyfikator ustawienia do unikatowego identyfikowania wszystkie ustawienia:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Nie trzeba używać `"Text Editor"` jako nazwę kategorii. Możesz wybrać coś, czego chcesz.

Pierwsze funkcje kilka są punkty wejścia, aby zmienić ustawienia. Wydasz ograniczeń wysokiego poziomu, takich jak maksymalna liczba przewodniki dozwolone.  Następnie wywołaj `WriteSettings`, który komponuje się ciąg ustawień i ustawia właściwość `GuideLinesConfiguration`. Ustawienie tej właściwości powoduje zapisanie wartości ustawienia z magazynu ustawień programu Visual Studio i generowane `SettingsChanged` zdarzenie, aby zaktualizować wszystkie `ColumnGuideAdornment` obiektów, każdy powiązany z widoku tekstu.

Istnieje kilka funkcji punktu wejścia, takich jak `CanAddGuideline`, które są używane do wykonania polecenia, które zmieniają ustawienia. Gdy program Visual Studio zawiera menu, wysyła zapytanie, implementacje polecenia, aby zobaczyć, jeśli polecenie jest aktualnie włączone, co to jest jego nazwa i tak dalej.  Poniżej zobaczysz, jak można dołączyć te punkty wejścia dla implementacji polecenia. Aby uzyskać więcej informacji na temat poleceń, zobacz [rozszerzenia menu i poleceń](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementowanie klasy ColumnGuideAdornment
`ColumnGuideAdornment` Utworzyć wystąpienia klasy dla każdego widoku tekstu, który może mieć zakończeń. Ta klasa nasłuchuje zdarzeń o zmiany widoku lub zmianę ustawień i prowadnice kolumn aktualizacji lub odświeżanie, zgodnie z potrzebami.

Zastąp zawartość *ColumnGuideAdornment.cs* następującym kodem (opisana poniżej):

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

Wystąpienia tej klasy przechowywania na skojarzonej <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> oraz listę `Line` obiekty rysowane w widoku.

Konstruktor (wywoływane z `ColumnGuideAdornmentTextViewCreationListener` gdy program Visual Studio tworzy nowe widoki) tworzy przewodnik kolumny `Line` obiektów.  Konstruktor również dodaje programy obsługi dla `SettingsChanged` zdarzeń (zdefiniowane w `GuidesSettingsManager`) i wyświetlanie zdarzeń `LayoutChanged` i `Closed`.

`LayoutChanged` Zdarzenia generowane z powodu kilka rodzajów zmian w widoku, łącznie z, gdy program Visual Studio tworzy widok. `OnViewLayoutChanged` Obsługi zdarzeń wywołuje `AddGuidelinesToAdornmentLayer` do wykonania. Kod w `OnViewLayoutChanged` Określa, czy wymagane można zaktualizować pozycje wiersza w oparciu o zmiany, takie jak zmiany rozmiaru czcionki, Wyświetl odstępy, przewijanie w poziomie i tak dalej. Kod w `UpdatePositions` powoduje, że linie prowadnic narysować między znakami lub zaraz po kolumnie tekst, który znajduje się w przesunięciu określonego znaku w wierszu tekstu.

Zawsze, gdy zmiana ustawień `SettingsChanged` funkcja po prostu odtwarza wszystkie `Line` obiektów są dowolnych nowych ustawień. Po ustawieniu pozycje wiersza, kod usuwa wszystkie poprzednie `Line` obiekty `ColumnGuideAdornment` zakończeń warstwy i dodaje nowe licencje.

## <a name="define-the-commands-menus-and-menu-placements"></a>Definiowanie polecenia menu i menu angażowania
Może istnieć wiele deklarowanie menu i poleceń, wprowadzenie do grup poleceń lub menu na różne inne menu i Podłączanie programy obsługi poleceń. Ten przewodnik opisuje, jak działają polecenia, w tym rozszerzeniu, ale w przypadku bardziej szczegółowych informacji, zobacz [rozszerzenia menu i poleceń](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Wprowadzenie do kodu
Rozszerzenie prowadnice kolumn pokazuje zadeklarowanie grupy poleceń, które ze sobą należą (Dodaj kolumnę, usunąć kolumny, zmienić kolor linii) i następnie wprowadzanie do tej grupy w podmenu z menu kontekstowym edytora.  Rozszerzenie prowadnice kolumn dodaje także polecenia do głównego **Edytuj** menu ale pozostaną niewidoczne, omówiony jako wspólny wzorzec poniżej.

Istnieją trzy części do wykonania polecenia: ColumnGuideCommandsPackage.cs ColumnGuideCommandsPackage.vsct i ColumnGuideCommands.cs. Kod wygenerowany przez Szablony umieszcza polecenie na **narzędzia** menu, które jest wyświetlane okno dialogowe jako implementacja. Możesz zapoznać się w jaki sposób jest zaimplementowana w *vsct* i *ColumnGuideCommands.cs* plików, ponieważ jest proste. Zastąp kod w tych plikach poniżej.

Kod pakietu zawiera deklaracje standardowy wymagane dla programu Visual Studio, aby dowiedzieć się, że rozszerzenie zapewnia polecenia, a także znalezienia gdzie umieścić polecenia. Inicjuje pakietu, tworzy wystąpienie klasy wykonania polecenia. Aby uzyskać więcej informacji na temat pakietów odnoszące się do poleceń, zobacz [rozszerzenia menu i poleceń](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Typowy wzorzec poleceń
Polecenia w rozszerzeniu prowadnice kolumn są przykładem bardzo typowy wzorzec w programie Visual Studio. Umieść powiązane polecenia w grupie, i umieścić tej grupy menu głównego, często za pomocą "`<CommandFlag>CommandWellOnly</CommandFlag>`" ustawiona na ukrywanie polecenia.  Umieszczenie poleceń w menu głównych (takie jak **Edytuj**) nadaje im nazwy nieuprzywilejowany (takie jak **Edit.AddColumnGuide**), które są przydatne do znajdowania poleceń podczas ponownego przypisywania klawiszy w **narzędzia Opcje**. Jest to również przydatne w celu uzyskania uzupełniania podczas wywoływania poleceń z **okna polecenia**.

Następnie dodaj grupę poleceń do menu kontekstowe lub sub menu, którego można spodziewać się użytkownika do użycia polecenia. Visual Studio traktuje `CommandWellOnly` jako flagi niewidoczności, tylko menu głównego. Po umieszczeniu tej samej grupie poleceń menu kontekstowego lub menu podrzędne polecenia są widoczne.

W ramach wspólny wzorzec rozszerzenie prowadnice kolumn tworzy drugiej grupy, zawierający pojedynczy podmenu. Pod menu z kolei zawiera pierwszą grupę za pomocą poleceń przewodnik cztery kolumny. Drugiej grupy, który przechowuje pod menu jest wielokrotnego użytku element zawartości, który można umieścić na różnych menu kontekstowe, która umieszcza menu podrzędne na tych menu kontekstowe.

### <a name="the-vsct-file"></a>Pliku vsct
*Vsct* pliku deklaruje poleceń i ich gdzie, wraz z ikon i tak dalej. Zastąp zawartość *vsct* pliku następującym kodem (opisana poniżej):

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

**GUIDS**. Dla programu Visual Studio można znaleźć inne programy obsługi polecenia i wywołaj je, należy upewnić się identyfikator GUID zadeklarowanych w pakietu *ColumnGuideCommandsPackage.cs* pakietu, identyfikator GUID jest zadeklarowana w pasuje do pliku (generowany na podstawie szablonu elementu projektu) *vsct* pliku (skopiowany z powyższych). Jeśli używasz ponownie tego przykładu kodu, należy się, że masz inny identyfikator GUID, tak aby nie powodują konfliktów z każdego, kto może skopiować ten kod.

Znajdź ten wiersz w *ColumnGuideCommandsPackage.cs* i skopiuj identyfikator GUID znajdujące znaki cudzysłowu:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Następnie wklej identyfikator GUID w *vsct* plików mają następujący wiersz w swojej `Symbols` deklaracje:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Ustaw identyfikatory GUID dla polecenia, a plik obrazu mapy bitowej powinna być unikatowa dla rozszerzeń, za:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Ale nie trzeba zmienić zestaw poleceń i mapy bitowej identyfikatorów GUID obrazu w tym przewodniku można pobrać kod do działania. Zestaw poleceń, identyfikator GUID musi pasować do deklaracji w *ColumnGuideCommands.cs* plik, ale Zastąp zawartość tego pliku, zbyt; dlatego identyfikatory GUID będą zgodne.

Inne identyfikatory GUID *vsct* pliku zidentyfikować istniejącego menu, do których zostaną dodane polecenia przewodnik kolumny, więc nigdy nie ulegną zmianie.

**Sekcje pliku**. *Vsct* będzie mieć trzy sekcje zewnętrzne: poleceń, rozmieszczaniu i symbole. W sekcji polecenia zdefiniowano grup poleceń, menu, przyciski lub elementy menu i mapy bitowej dla ikony. W sekcji angażowania deklaruje, dokąd grup w menu i angażowania dodatkowych do istniejącego menu. W sekcji symbole deklaruje identyfikatory używane w innych miejscach w *vsct* pliku, który sprawia, że *vsct* kod bardziej czytelne niż w przypadku identyfikatorów GUID i wartość szesnastkową liczby wszędzie.

**Sekcja polecenia, definicje grup**. Sekcja polecenia najpierw definiuje grup poleceń. Grupy poleceń są poleceniami, widoczne w menu nieznaczne wierszami szarego oddzielenie grup. Grupy mogą również wypełnić całe podmenu, jak w poniższym przykładzie, i szary, oddzielając wiersze, w tym przypadku nie są widoczne. *Vsct* pliki Zadeklaruj dwie grupy `GuidesMenuItemsGroup` który jest nadrzędny do `IDM_VS_MENU_EDIT` (główny **Edytuj** menu) i `GuidesContextMenuGroup` który jest nadrzędny do `IDM_VS_CTXT_CODEWIN` (kod menu kontekstowe edytora).

Deklaracja druga grupa ma `0x0600` priorytetu:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Chodzi o to, aby umieścić kolumna zawiera informacje na temat podmenu na końcu dowolnego menu kontekstowego, do którego należy dodać grupy menu podrzędne. Jednak nie należy zakładać, że najlepiej i wymusić podmenu do zawsze ostatniego przy użyciu priorytet `0xFFFF`. Masz do eksperymentowania z numerem, aby zobaczyć, gdzie Twoje podmenu znajduje się w menu kontekstowe, gdzie umieścić. W tym przypadku `0x0600` jest wystarczająco wysoka, umieść go na końcu menu, jeśli chodzi o widoczne, ale pozostawia miejsce dla innych osób do projektowania ich rozszerzenia są niższe niż rozszerzenie prowadnice kolumn, jeśli jest to pożądane.

**Polecenia menu definicji sekcji**. Następnie w sekcji polecenia zdefiniowano pod menu `GuidesSubMenu`, nadrzędnego do `GuidesContextMenuGroup`. `GuidesContextMenuGroup` Jest to grupa, możesz dodać do menu odpowiedniego kontekstu. W sekcji angażowania kod umieszcza grupy za pomocą poleceń przewodnik cztery kolumny, w tym menu podrzędne.

**Sekcja polecenia, przyciski definicje**. Sekcja polecenia następnie definiuje, menu i przycisków, które są poleceniami przewodniki cztery kolumny. `CommandWellOnly`, omówione powyżej, oznacza, że polecenia są niewidoczne, po umieszczeniu w menu głównym. Dwa polecenia menu przycisku deklaracje (Przewodnik Dodaj i Usuń przewodnik) również mieć `AllowParams` flagi:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Ta flaga umożliwia wraz z o rozmieszczaniu menu głównego, polecenie, aby otrzymywać argumenty, gdy program Visual Studio wywołuje program obsługi poleceń.  Jeśli użytkownik uruchamia polecenia w oknie polecenia, argument jest przekazywany do program obsługi poleceń w zdarzeniu argumentów.

**Polecenie części, definicje mapy bitowe**. Na koniec sekcji poleceń deklaruje, bitmap i ikon używanych dla poleceń. Ta sekcja dotyczy zwykłej deklaracji, która identyfikuje zasób projektu i wyświetla liczonego od jednego indeksy ikon używanych. Symbole części *vsct* pliku deklaruje wartości identyfikatory używane jako indeksy. W tym instruktażu wykorzystano paska mapy bitowej dostarczane z szablonem elementu polecenie niestandardowe, które są dodawane do projektu.

**Sekcja angażowania**. Po poleceniach sekcja jest sekcja angażowania. Pierwsze z nich polega na tym, gdzie ten kod dodaje pierwszej grupy omówione powyżej, które zawiera przewodnik cztery kolumny polecenia do menu podrzędne gdzie są wyświetlane polecenia:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Dodaj wszystkie inne angażowania `GuidesContextMenuGroup` (który zawiera `GuidesSubMenu`) do innych menu kontekstowe edytora. Kiedy kod zadeklarowana `GuidesContextMenuGroup`, został on nadrzędny do menu kontekstowego edytora kodu. Dlatego nie widzisz położenie menu kontekstowe edytora kodu.

**Symbole sekcji**. Jak już wspomniano w sekcji symbole deklaruje identyfikatory używane w innych miejscach w *vsct* pliku, który sprawia, że *vsct* kod bardziej czytelne niż w przypadku identyfikatorów GUID i wartość szesnastkową liczby wszędzie. Najważniejsze punkty w tej sekcji są na tym, że identyfikator GUID pakietu należy uzgodnić z deklaracji w klasie pakietu. I identyfikator GUID zestawu poleceń należy uzgodnić z deklaracji w klasie wykonania polecenia.

## <a name="implement-the-commands"></a>Implementowanie polecenia
*ColumnGuideCommands.cs* pliku implementuje poleceń i przechwytuje się programów obsługi. Gdy program Visual Studio ładuje pakiet i inicjuje ją, pakiet z kolei wywołuje `Initialize` klasy wykonania polecenia. Inicjowanie poleceń po prostu tworzy wystąpienie klasy i konstruktora przechwytuje się wszystkie programy obsługi poleceń.

Zastąp zawartość *ColumnGuideCommands.cs* pliku następującym kodem (opisana poniżej):

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

**Napraw odwołania**. W tym momencie masz brakuje odwołania. Naciśnij przycisk prawo wskaźnika na węźle odwołania w Eksploratorze rozwiązań. Wybierz **Dodaj...**  polecenia. **Dodaj odwołanie** okno dialogowe zawiera pole wyszukiwania w prawym górnym rogu. Wprowadź "editor" (bez cudzysłowów). Wybierz **Microsoft.VisualStudio.Editor** elementu (użytkownik musi pole wyboru na lewo od elementu, a nie po prostu wybierz pozycję elementu) i wybierz polecenie **OK** można dodać odwołania.

**Inicjowanie**.  Kiedy inicjuje klasie pakietu, wywołuje `Initialize` klasy wykonania polecenia. `ColumnGuideCommands` Inicjowanie tworzy wystąpienie klasy i zapisuje wystąpienie klasy i odwołania do pakietu w składowych klasy.

Przyjrzyjmy się jednej z obsługi polecenia w ups punktu zaczepienia w konstruktorze klasy:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Możesz utworzyć `OleMenuCommand`. Visual Studio używa programu Microsoft Office system polecenia. Kluczowych argumentów podczas tworzenia wystąpienia `OleMenuCommand` jest funkcją, która implementuje polecenie (`AddColumnGuideExecuted`), funkcja wywoływana, gdy program Visual Studio zawiera menu przy użyciu polecenia (`AddColumnGuideBeforeQueryStatus`), a identyfikator polecenia. Program Visual studio wywołuje funkcję stan zapytania przed pokazaniem polecenia menu, aby polecenia lub mogą być sam niewidoczne wyszarzonym dla konkretnego wyświetlanie menu (na przykład wyłączenie **kopiowania** Jeśli nie zaznaczono żadnego fragmentu), Zmień jej ikonę lub nawet zmienić jego nazwę (na przykład z dodać coś, co usunąć coś o nim) i tak dalej. Identyfikator polecenia musi odpowiadać identyfikator zadeklarowany w polecenia *vsct* pliku. Ciągi dla zestawu poleceń i prowadnice kolumn Dodaj polecenie musi odpowiadać między *vsct* pliku i *ColumnGuideCommands.cs*.

Następujący wiersz zawiera pomoc dla, gdy użytkownicy wywołać polecenie za pośrednictwem oknie wiersza polecenia (opisana poniżej):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Kwerenda o stan**. Funkcje stan zapytań `AddColumnGuideBeforeQueryStatus` i `RemoveColumnGuideBeforeQueryStatus` Sprawdź niektórych ustawień (np. Maksymalna liczba przewodniki lub kolumny max) lub jeśli jest to przewodnik kolumny do usunięcia. Umożliwiają one poleceń, jeśli warunki są odpowiednie.  Funkcje stan zapytań muszą być efektywne, ponieważ są one uruchamiane za każdym razem, gdy program Visual Studio zawiera menu i dla każdego polecenia w menu.

 **Funkcja AddColumnGuideExecuted**. Interesujących części Dodawanie przewodnika jest ustalenie bieżącej lokalizacji widoku i karetkę edytora.  Po pierwsze, ta funkcja wywołuje `GetApplicableColumn`, która sprawdza, czy istnieje argumentów dostarczone przez użytkownika w argumentach zdarzeń program obsługi poleceń, a w przypadku none, funkcja sprawdza, czy widok edytora:

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

`GetCurrentEditorColumn` ma się z materiałami niewiele przybliżają do <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> widoku kodu.  Jeśli śledzenie za pomocą `GetActiveTextView`, `GetActiveView`, i `GetTextViewFromVsTextView`, możesz dowiedzieć się, jak to zrobić. Poniższy kod jest odpowiedni kod, wyodrębnione, począwszy od bieżącego zaznaczenia, wprowadzenie ramki wyboru, a następnie wprowadzenie DocView ramki jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, następnie konfigurowania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> z IVsTextView, a następnie wprowadzenie hostem widoku i na koniec element IWpfTextView:

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

Gdy istnieje już element IWpfTextView, można uzyskać kolumny, w którym znajduje się daszek:

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

Za pomocą bieżącej kolumny w kasie w przypadku, gdy użytkownik kliknie, kod po prostu wywołuje funkcję w Menedżerze ustawień, aby dodać lub usunąć tę kolumnę. Menedżer ustawień wyzwala zdarzenie, na którym wszystkie `ColumnGuideAdornment` nasłuchiwania obiektów. Gdy zdarzenie zostanie wyzwolony, te obiekty zaktualizować swoje opinie skojarzony tekst z nowymi ustawieniami przewodnik kolumny.

## <a name="invoke-command-from-the-command-window"></a>Wywołaj polecenie w oknie polecenia
Przykładowe przewodniki kolumny umożliwia użytkownikom wywoływanie dwa polecenia w oknie polecenia jako formę rozszerzalności. Jeśli używasz **widoku &#124; Windows inne &#124; okna polecenia** polecenia, okno polecenia. Możesz wchodzić w interakcje z okna poleceń, wprowadzając "Edytuj", a dzięki uzupełnianie nazw poleceń i dostarczenie argument 120, masz następujące wyniki:

```csharp
> Edit.AddColumnGuide 120
>
```

Fragmenty przykładu, włączyć to zachowanie, które znajdują się w *vsct* plików deklaracji, `ColumnGuideCommands` konstruktora klasy po jej przechwytuje programy obsługi poleceń i implementacji programu obsługi poleceń, które Sprawdź, czy argumenty zdarzeń.

Pokazaliśmy, "`<CommandFlag>CommandWellOnly</CommandFlag>`" w *vsct* plik oraz angażowania w **Edytuj** nawet wtedy, gdy polecenia nie są wyświetlane w menu głównym **Edytuj** menu interfejsu użytkownika. Pozwól, aby w głównym **Edytuj** menu nadaje im nazwy, takie jak **Edit.AddColumnGuide**. Deklaracja grupy poleceń, która zawiera cztery polecenia umieszczone w grupie na **Edytuj** bezpośrednio menu:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Sekcja przyciski później zadeklarowana polecenia `CommandWellOnly` zachować niewidoczne w menu głównym i zadeklarować je za pomocą `AllowParams`:

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Pokazaliśmy, program obsługi poleceń podpiąć kodu w `ColumnGuideCommands` konstruktora klasy podano opis parametru dozwolonych:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Jak działa `GetApplicableColumn` funkcji kontroli `OleMenuCmdEventArgs` wartości przed sprawdzeniem widok edytora dla bieżącej kolumny:

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

## <a name="try-your-extension"></a>Spróbuj rozszerzenia
Teraz można nacisnąć klawisz **F5** można wykonać rozszerzenia prowadnice kolumn. Otwórz plik tekstowy i użyj menu kontekstowego edytora Dodaj linie prowadnic, usuń je i zmienić kolor. Kliknij w tekście (nie odstępu minięto koniec wiersza) aby dodać kolumnę przewodnika lub edytorze dodaje go do ostatniej kolumny w wierszu. Jeśli korzystanie z okna polecenia i wywołują polecenia z nieprawidłowym argumentem, możesz dodać prowadnice kolumn w dowolnym miejscu.

Jeśli chcesz spróbować innego polecenia angażowania, zmienianie nazwy, zmiana ikon i tak dalej, a masz problemy z programem Visual Studio przedstawiający najnowszy kod w menu, można zresetować eksperymentalne hive, w którym jest debugowany. Wyświetlenie **Windows Start Menu** i wpisz "Resetuj". Znajdź i uruchom polecenie **resetowania dalej doświadczalne wystąpienie programu Visual Studio**. To polecenie czyści gałęzi rejestru eksperymentalne wszystkich składników rozszerzenia. Nie ma czyszczenie się ustawienia ze składników, dlatego wszystkie prowadnice miał podczas zamykania hive eksperymentalne programu Visual Studio nadal istnieją Jeśli kod odczyta magazynu ustawień przy następnym uruchomieniu.

## <a name="finished-code-project"></a>Gotowy kod projektu
Wkrótce będą projektu GitHub, programu Visual Studio Extensibility przykłady i ukończonych projektu zostaną wyświetlone w. W tym artykule zostanie zaktualizowany w celu wskazania istnieje, jeśli tak się stanie. Ukończone przykładowy projekt może mieć różne identyfikatory GUID i będzie mieć paska różnych map bitowych, ikon polecenia.

Możesz wypróbować wersję funkcji prowadnice kolumn z tej galerii Visual Studio[rozszerzenia](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines).

## <a name="see-also"></a>Zobacz także
[Wewnątrz edytora](../extensibility/inside-the-editor.md)
[rozszerzanie usług edytora i języka](../extensibility/extending-the-editor-and-language-services.md) 
[punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md)  
 [Rozszerzenia menu i poleceń](../extensibility/extending-menus-and-commands.md)
[dodawanie podmenu do menu](../extensibility/adding-a-submenu-to-a-menu.md)
[Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)
