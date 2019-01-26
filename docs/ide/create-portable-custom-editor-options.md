---
title: Ustawienia pliku EditorConfig
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: f2043fb01a67a916ebf13fada7c03111c7a80510
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027116"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Tworzenie przenośnych, niestandardowych ustawień edytora za pomocą wtyczki EditorConfig

W programie Visual Studio 2017, można dodać [EditorConfig](http://editorconfig.org/) plik do projektu lub kodu, aby wymusić spójnej kodowania style dla wszystkich użytkowników, który działa w bazie kodu. Ustawienia polecenia EditorConfig pierwszeństwo tekstu Visual Studio globalnego ustawienia edytora. Oznacza to, że możesz dostosować każdą bazę kodu do używania ustawień edytora tekstów, które są specyficzne dla tego projektu. Nadal można ustawić preferencje edytora osobistych w programie Visual Studio **opcje** okno dialogowe. Te ustawienia są stosowane zawsze, gdy pracujesz w bazie kodu bez *.editorconfig* pliku, lub gdy *.editorconfig* pliku nie zastępuje danego ustawienia. Przykładem takich preferencji jest styl wcięcia&mdash;tabulatory lub spacje.

Polecenie EditorConfig ustawienia są obsługiwane przez wiele kodu edytorami i środowiskami IDE, w tym Visual Studio. Jest przenośny składnikiem przybliżone ilości tych danych przy użyciu kodu i mogą zostać wymuszone kodowania stylów nawet poza programem Visual Studio.

Po dodaniu pliku EditorConfig do projektu w programie Visual Studio, formatowanie istniejącego kodu nie jest zmieniany, chyba że formatowania dokumentu (**Edytuj** > **zaawansowane**  >  **Formatowania dokumentu** lub **Ctrl**+**K**, **Ctrl**+**D**w profilu domyślnym). Jednak wszelkie nowe wiersze kodu są sformatowane zgodnie z ustawieniami EditorConfig. Można zdefiniować ustawienia EditorConfig, które chcesz **Formatuj dokument** można zastosować [ **formatowanie** Strona opcji](reference/options-text-editor-csharp-formatting.md#format-document-settings).

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [polecenia EditorConfig w programie Visual Studio dla komputerów Mac](/visualstudio/mac/editorconfig).

## <a name="coding-consistency"></a>Kodowanie spójności

Ustawienia w plikach EditorConfig umożliwiają utrzymania spójnego style pisania kodu i ustawienia w bazie kodu, takie jak styl wcięcia, szerokość karty, znaki końca wiersza, kodowanie, i innych, niezależnie od tego, czy edytor lub w środowisku IDE możesz użycia. Na przykład podczas kodowania w języku C#, jeśli baza kodu ma Konwencji preferowanie, że wcięcia zawsze składa się z pięciu znaków spacji, dokumentów, użyj kodowania UTF-8, a każdy wiersz kończy się zawsze CR/LF, można skonfigurować *.editorconfig* plik, aby to zrobić.

Konwencje używanej w osobistych projektach kodowania może się różnić od tych używanych w projektach zespołu. Na przykład można wybrać, gdy masz kodowania, wcięcia dodaje znak tabulacji. Jednak Twój zespół preferować, że wcięcia dodaje czterech znaków spacji zamiast znak tabulacji. Plików EditorConfig rozwiązać ten problem, umożliwiając konfigurację dla każdego scenariusza.

Ponieważ ustawienia są przechowywane w pliku w bazie kodu, podróży wraz z tego kodu. Tak długo, jak możesz Otwórz plik kodu w edytorze EditorConfig zgodne, są implementowane ustawienia edytora tekstu. Aby uzyskać więcej informacji na temat plików EditorConfig zobacz [EditorConfig.org](http://editorconfig.org/) witryny sieci Web.

> [!NOTE]
> Konwencje, które są ustawione w pliku EditorConfig obecnie nie można wymusić w potoku ciągłej integracji/ciągłego wdrażania, jak tworzyć błędy lub ostrzeżenia. Wszelkie odchylenia style są wyświetlane tylko w edytorze programu Visual Studio i **lista błędów**.

## <a name="supported-settings"></a>Obsługiwane ustawienia

Edytor programu Visual Studio obsługuje podstawowy zestaw [właściwości EditorConfig](http://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- koniec\_of_line
- zestaw znaków
- TRIM\_trailing_whitespace
- Wstaw\_final_newline
- root

Ustawienia edytora EditorConfig są obsługiwane we wszystkich językach obsługiwanych przez program Visual Studio, z wyjątkiem XML. Ponadto obsługuje EditorConfig [styl kodu](../ide/editorconfig-code-style-settings-reference.md) i [nazewnictwa](../ide/editorconfig-naming-conventions.md) konwencje dotyczące języka C# i Visual Basic.

## <a name="adding-and-removing-editorconfig-files"></a>Dodawanie i usuwanie plików EditorConfig

Dodawanie polecenia EditorConfig plik do projektu lub codebase nie konwertuje istniejące style na nowe licencje. Na przykład jeśli masz wcięcia w pliku, które są formatowane przy użyciu kart i Dodaj plik wtyczki EditorConfig, który wcięcia ze spacjami, znaki wcięcia nie są automatycznie konwertowane na spacje. Jednak wszelkie nowe wiersze kodu są sformatowane zgodnie z plików EditorConfig. Ponadto jeśli formatowania dokumentu (**Edytuj** > **zaawansowane** > **Formatuj dokument** lub **Ctrl** + **K**, **Ctrl**+**D**), ustawienia w pliku EditorConfig są stosowane do istniejących wierszy kodu.

Usuwanie pliku EditorConfig z projektu lub bazie kodu, musisz zamknąć i ponownie otworzyć wszystkie pliki Otwórz kod, aby przywrócić ustawienia globalne edytora dla nowych wierszy kodu.

### <a name="to-add-an-editorconfig-file-to-a-project-or-solution"></a>Aby dodać plik wtyczki EditorConfig do projektu lub rozwiązania

1. Otwórz projekt lub rozwiązanie w programie Visual Studio. Wybierz węzeł projektu lub rozwiązania, w zależności od tego, czy Twoje *.editorconfig* ustawienia dotyczą wszystkich projektów w rozwiązaniu lub jedna z tych metod. Możesz również wybrać folder, w projekcie lub rozwiązaniu, aby dodać *.editorconfig* plik.

1. Na pasku menu wybierz **projektu** > **Dodaj nowy element**, lub naciśnij **Ctrl**+**Shift** + **A**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

1. W kategorii po lewej stronie, wybierz **ogólne**, a następnie wybierz **plik tekstowy** szablonu. W **nazwa** tekstu wprowadź `.editorconfig` , a następnie wybierz **Dodaj**.

   *.Editorconfig* plik pojawia się w Eksploratorze rozwiązań, a zostanie on otwarty w edytorze.

   ![pliku .editorconfig w Eksploratorze rozwiązań](media/editorconfig-in-solution-explorer.png)

1. Przeprowadź edycję pliku zgodnie z potrzebami, na przykład:

   ```EditorConfig
   root = true

   [*.{cs,vb}]
   indent_size = 4
   trim_trailing_whitespace = true

   [*.cs]
   csharp_new_line_before_open_brace = methods
   ```

### <a name="other-ways-to-add-an-editorconfig-file"></a>Inne sposoby dodawania pliku EditorConfig

Istnieje kilka innych sposobów, w pliku EditorConfig można dodać do projektu:

- Zainstaluj [rozszerzeń usługi językowej EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) można łatwo dodać pustą *.editorconfig* plik do projektu. Po zainstalowaniu tego rozszerzenia, po prostu wybierz **Dodaj** > **pliku .editorconfig** menu kontekście lub kliknij prawym przyciskiem myszy węzeł rozwiązania, węzeł projektu lub dowolnym folderze w usłudze  **Eksplorator rozwiązań**. To rozszerzenie również zwiększa doświadczenie w edytowaniu dla *.editorconfig* pliku.

   ![Dodawanie pliku .editorconfig z rozszerzeniem](media/editorconfig-extension-add.png)

- Wypróbuj [rozszerzenia IntelliCode](/visualstudio/intellicode/intellicode-visual-studio). To rozszerzenie eksperymentalne wnioskuje style kodu z istniejącego kodu, a następnie tworzy niepusty *.editorconfig* plików za pomocą preferencji stylu kodu już zdefiniowane.

## <a name="override-editorconfig-settings"></a>Przesłoń ustawienia wtyczki EditorConfig

Po dodaniu *.editorconfig* pliku do folderu w hierarchii plików, jego ustawienia mają zastosowanie do wszystkich odpowiednich plików na tym samym poziomie i poniżej. Możesz również zastąpić ustawienia EditorConfig dla konkretnego projektu, kodu lub część kodu, taki sposób, że używa różnych konwencji niż inne części bazy kodu. Może to być przydatne, gdy dołączyć kod z żadnym innym miejscu, a nie chcesz zmienić jego Konwencji.

Aby zastąpić niektóre lub wszystkie ustawienia EditorConfig, Dodaj *.editorconfig* pliku na poziomie hierarchii plików, które chcesz, aby te ustawienia zgodnym z przesłoniętą mają być stosowane. Nowe ustawienia pliku EditorConfig zostaną zastosowane do plików na tym samym poziomie i wszystkich podkatalogach.

![Hierarchia wtyczki EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Jeśli chcesz zastąpić niektóre, ale nie wszystkie ustawienia, określ tylko te ustawienia w *.editorconfig* pliku. Tylko te właściwości, które jawnie listy w pliku niższego poziomu zostaną zastąpione. Inne ustawienia z wyższego poziomu *.editorconfig* pliki w dalszym ciągu stosowane. Jeśli chcesz upewnić się, że _nie_ ustawienia z _wszelkie_ wyższego poziomu *.editorconfig* pliki są stosowane do tej części bazy kodu, Dodaj ```root=true``` właściwości niższego poziomu *.editorconfig* pliku:

```EditorConfig
# top-most EditorConfig file
root = true
```

Plików EditorConfig są odczytywane od góry do dołu i ostatniego odczytu najbliższego plików EditorConfig. Konwencje z pasujących sekcji EditorConfig są stosowane w kolejności, w których one zostały odczytane, dzięki czemu konwencje w plikach bliżej wyższy priorytet.

## <a name="editing-editorconfig-files"></a>Edytowanie plików EditorConfig

Program Visual Studio pozwala edytować *.editorconfig* plików, zapewniając listy uzupełniania IntelliSense.

![Funkcja IntelliSense w pliku .editorconfig](media/editorconfig-intellisense-no-extension.png)

Po zakończeniu edycji pliku EditorConfig, należy ponownie załadować plików kodu nowe ustawienia zaczęły obowiązywać.

Jeśli edytujesz liczne *.editorconfig* plików, może się okazać [rozszerzeń usługi językowej EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) pomocne. Niektóre funkcje tego rozszerzenia obejmują wyróżnianie składni, ulepszoną funkcję IntelliSense, weryfikacji i formatowania kodu.

![Funkcja IntelliSense z rozszerzeń usługi językowej EditorConfig](media/editorconfig-intellisense.png)

## <a name="example"></a>Przykład

Poniższy przykład pokazuje stan wcięcie fragment kodu języka C#, przed i po dodaniu *.editorconfig* pliku do projektu. **Karty** w **opcje** okno dialogowe Edytor tekstu Visual Studio jest ustawiony do produkcji znaków spacji po naciśnięciu klawisza **kartę** klucza.

![Edytor tekstu tabulatora](../ide/media/vside_editorconfig_tabsetting.png)

Zgodnie z oczekiwaniami, naciskając klawisz **kartę** klucza w następnym wierszu wcięcia linii, dodając cztery dodatkowe znaki odstępu.

![Kod przed rozpoczęciem korzystania z wtyczki EditorConfig](../ide/media/vside_editorconfig_before.png)

Dodaj nowy plik o nazwie *.editorconfig* do projektu, z następującą zawartością. `[*.cs]` Ustawienie oznacza, że ta zmiana ma zastosowanie tylko do plików kodu języka C# w projekcie.

```EditorConfig
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Teraz, gdy ponownie naciśniesz **kartę** klucza, możesz uzyskać znaki tabulacji zamiast spacji.

![Klawisz TAB dodaje znak tabulacji](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>Rozwiązywanie problemów z ustawieniami wtyczki EditorConfig

W przypadku plików EditorConfig dowolne miejsce w strukturze katalogów lub nowsza lokalizacji projektu, Visual Studio stosuje ustawienia edytora w tym pliku do edytora. W takim przypadku może zostać wyświetlony następujący komunikat na pasku stanu:

   **"Preferencje użytkownika dla tego typu pliku są przesłaniane przez konwencje kodowania tego projektu."**

Oznacza to, że jeśli wszystkie ustawienia edytora w **narzędzia** > **opcje** > **edytora tekstów** (np. rozmiar wcięcia i styl, Rozmiar tabulatora lub kodowania konwencje) są określone w pliku EditorConfig równą lub nowszą projektu w strukturze katalogów, w pliku EditorConfig Konwencji przesłonić ustawienia w **opcje**. Można kontrolować to zachowanie, przełączając **przestrzegaj Konwencji kodowania projektu** opcji **narzędzia** > **opcje**  >  **Edytora tekstów**. Anulowanie zaznaczenia opcji powoduje wyłączenie obsługi polecenia EditorConfig dla programu Visual Studio.

![Opcje narzędzia - przestrzegaj Konwencji kodowania projektu](media/coding_conventions_option.png)

Można znaleźć żadnego *.editorconfig* plików w katalogach nadrzędnych, otwierając wiersz polecenia i uruchom następujące polecenie w katalogu głównym dysku, który zawiera projekt:

```Shell
dir .editorconfig /s
```

Zakres usługi konwencje EditorConfig można kontrolować przez ustawienie ```root=true``` właściwości w *.editorconfig* pliku w katalogu głównym repozytorium lub w katalogu, w którym znajduje się projekt. Visual Studio szuka w pliku o nazwie *.editorconfig* w katalogu otwarty plik i w każdym katalogu nadrzędnego. Wyszukiwanie kończy się po osiągnięciu filepath głównego lub jeśli *.editorconfig* plik z ```root=true``` zostanie znaleziony.

## <a name="see-also"></a>Zobacz także

- [Konwencje stylu kodu .NET](../ide/editorconfig-code-style-settings-reference.md)
- [Konwencje nazewnictwa platformy .NET](../ide/editorconfig-naming-conventions.md)
- [Obsługa wtyczki EditorConfig dla usługi w języka](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](http://editorconfig.org/)
- [Funkcje edytora kodu](writing-code-in-the-code-and-text-editor.md)
- [Polecenie EditorConfig (Visual Studio dla komputerów Mac)](/visualstudio/mac/editorconfig)