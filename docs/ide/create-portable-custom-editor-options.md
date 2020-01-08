---
title: Ustawienia pliku EditorConfig
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3aee4945b4a3b41a7f6ec532268c2c19f549d0a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589789"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Tworzenie przenośnych, niestandardowych ustawień edytora za pomocą wtyczki EditorConfig

Można dodać plik [EditorConfig](https://editorconfig.org/) do projektu lub bazy kodu w celu wymuszenia spójnych stylów kodowania dla wszystkich, które działają w bazie kodu. Ustawienia polecenia EditorConfig pierwszeństwo tekstu Visual Studio globalnego ustawienia edytora. Oznacza to, że możesz dostosować każdą bazę kodu do używania ustawień edytora tekstów, które są specyficzne dla tego projektu. Nadal można ustawić preferencje edytora osobistych w programie Visual Studio **opcje** okno dialogowe. Te ustawienia są stosowane zawsze, gdy pracujesz w bazie kodu bez *.editorconfig* pliku, lub gdy *.editorconfig* pliku nie zastępuje danego ustawienia. Przykładem takich preferencji jest styl wcięcia&mdash;tabulatory lub spacje.

Polecenie EditorConfig ustawienia są obsługiwane przez wiele kodu edytorami i środowiskami IDE, w tym Visual Studio. Jest przenośny składnikiem przybliżone ilości tych danych przy użyciu kodu i mogą zostać wymuszone kodowania stylów nawet poza programem Visual Studio.

::: moniker range=">=vs-2019"

Po dodaniu pliku EditorConfig do projektu w programie Visual Studio, nowe wiersze kodu są formatowane zgodnie z ustawieniami EditorConfig. Formatowanie istniejącego kodu nie jest zmieniane, chyba że zostanie uruchomione jedno z następujących poleceń:

 - [Czyszczenie kodu](../ide/code-styles-and-code-cleanup.md) (**Ctrl**+**K**, **Ctrl**+**E**), które dotyczy wszelkich białych ustawień, takich jak styl wcięcia i wybrane ustawienia stylu kodu, takie jak sortowanie `using` dyrektyw.
 - **Edytuj** **dokument w formacie** > **Advanced** > (lub **Ctrl**+**K**, **Ctrl**+**D** w profilu domyślnym), który stosuje tylko ustawienia białych znaków, na przykład styl wcięcia.

 ::: moniker-end

::: moniker range="=vs-2017"

Po dodaniu pliku EditorConfig do projektu w programie Visual Studio, nowe wiersze kodu są formatowane zgodnie z ustawieniami EditorConfig. Formatowanie istniejącego kodu nie jest zmieniane, chyba że zostanie uruchomione, chyba że użytkownik sformatuje dokument (**edytuj** > **Zaawansowany** > **Formatowanie dokumentu** lub **Ctrl**+**K**, **Ctrl**+**D** w domyślnym profilu). Formatowanie dokumentu ma wpływ tylko na ustawienia białych znaków, takie jak styl wcięcia, chyba że skonfigurowano dokument formatu w celu [przeprowadzenia dodatkowego czyszczenia kodu](../ide/code-styles-and-code-cleanup.md#apply-code-styles).

 ::: moniker-end

::: moniker range="vs-2017"

Można zdefiniować ustawienia EditorConfig, które chcesz **Formatuj dokument** można zastosować [ **formatowanie** Strona opcji](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [polecenia EditorConfig w programie Visual Studio dla komputerów Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Spójność kodu

Ustawienia w plikach EditorConfig umożliwiają utrzymania spójnego style pisania kodu i ustawienia w bazie kodu, takie jak styl wcięcia, szerokość karty, znaki końca wiersza, kodowanie, i innych, niezależnie od tego, czy edytor lub w środowisku IDE możesz użycia. Na przykład podczas kodowania w języku C#, jeśli baza kodu ma Konwencji preferowanie, że wcięcia zawsze składa się z pięciu znaków spacji, dokumentów, użyj kodowania UTF-8, a każdy wiersz kończy się zawsze CR/LF, można skonfigurować *.editorconfig* plik, aby to zrobić.

Konwencje używanej w osobistych projektach kodowania może się różnić od tych używanych w projektach zespołu. Na przykład można wybrać, gdy masz kodowania, wcięcia dodaje znak tabulacji. Jednak Twój zespół preferować, że wcięcia dodaje czterech znaków spacji zamiast znak tabulacji. Plików EditorConfig rozwiązać ten problem, umożliwiając konfigurację dla każdego scenariusza.

Ponieważ ustawienia są przechowywane w pliku w bazie kodu, podróży wraz z tego kodu. Tak długo, jak możesz Otwórz plik kodu w edytorze EditorConfig zgodne, są implementowane ustawienia edytora tekstu. Aby uzyskać więcej informacji na temat plików EditorConfig zobacz [EditorConfig.org](https://editorconfig.org/) witryny sieci Web.

> [!NOTE]
> Konwencje, które są ustawione w pliku EditorConfig obecnie nie można wymusić w potoku ciągłej integracji/ciągłego wdrażania, jak tworzyć błędy lub ostrzeżenia. Wszelkie odchylenia style są wyświetlane tylko w edytorze programu Visual Studio i **lista błędów**.

## <a name="supported-settings"></a>Obsługiwane ustawienia

Edytor programu Visual Studio obsługuje podstawowy zestaw [właściwości EditorConfig](https://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- koniec\_of_line
- zestaw znaków
- TRIM\_trailing_whitespace
- Wstaw\_final_newline
- root

Ustawienia edytora EditorConfig są obsługiwane we wszystkich językach obsługiwanych przez program Visual Studio, z wyjątkiem XML. Ponadto EditorConfig obsługuje konwencje [stylów kodu](../ide/editorconfig-code-style-settings-reference.md) , w tym [Język](../ide/editorconfig-language-conventions.md), [Formatowanie](../ide/editorconfig-formatting-conventions.md)i konwencje [nazewnictwa](../ide/editorconfig-naming-conventions.md) dla C# i Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Dodawanie i usuwanie plików EditorConfig

Po dodaniu pliku EditorConfig do projektu lub bazy kodu, wszelkie nowe wiersze napisanego kodu są formatowane według pliku EditorConfig. Jednak dodanie pliku EditorConfig nie konwertuje istniejących stylów do nowych, dopóki nie sformatujesz dokumentu lub uruchomisz [oczyszczanie kodu](../ide/code-styles-and-code-cleanup.md). Na przykład, jeśli w pliku znajdują się wcięcia, które są sformatowane przy użyciu kart i dodasz plik EditorConfig, który jest wcięty ze spacjami, znaki wcięcia nie są automatycznie konwertowane na spacje. Podczas formatowania dokumentu (**edytuj** >  > **dokumentu formatu** **zaawansowanego** lub **Ctrl**+**K**, **Ctrl**+**D**) ustawienia białych znaków w pliku EditorConfig są stosowane do istniejących wierszy kodu.

Jeśli usuniesz plik EditorConfig z projektu lub bazy kodu i chcesz, aby nowe wiersze kodu były sformatowane zgodnie z ustawieniami edytora globalnego, musisz zamknąć i ponownie otworzyć wszystkie otwarte pliki kodu.

### <a name="add-an-editorconfig-file-to-a-project"></a>Dodawanie pliku EditorConfig do projektu

1. Otwórz projekt lub rozwiązanie w programie Visual Studio. Wybierz węzeł projektu lub rozwiązania, w zależności od tego, czy Twoje *.editorconfig* ustawienia dotyczą wszystkich projektów w rozwiązaniu lub jedna z tych metod. Możesz również wybrać folder, w projekcie lub rozwiązaniu, aby dodać *.editorconfig* plik.

1. Na pasku menu wybierz **projektu** > **Dodaj nowy element**, lub naciśnij **Ctrl**+**Shift** + **A**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

1. W polu wyszukiwania Wyszukaj ciąg **editorconfig**.

   Dwa szablony elementów **plików editorconfig** są wyświetlane w wynikach wyszukiwania.

   ![Szablony elementów plików EditorConfig w programie Visual Studio](media/editorconfig-item-templates.png)

1. Wybierz szablon **plik editorconfig (domyślny)** , aby dodać wstępnie wypełniony plik editorconfig z dwoma podstawowymi opcjami editorconfig dla stylu i rozmiaru wcięcia. Lub wybierz szablon **plik editorconfig (.NET)** , aby dodać wstępnie wypełniony plik editorconfig z domyślnym [stylem kodu platformy .NET, formatowaniem i konwencjami nazewnictwa](../ide/editorconfig-code-style-settings-reference.md).

   *.Editorconfig* plik pojawia się w Eksploratorze rozwiązań, a zostanie on otwarty w edytorze.

   ![plik. editorconfig w Eksplorator rozwiązań i edytorze](media/editorconfig-dotnet.png)

1. Edytuj plik zgodnie z potrzebami.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Inne sposoby dodawania pliku EditorConfig

Istnieje kilka innych sposobów, w pliku EditorConfig można dodać do projektu:

- [Funkcja wnioskowania kodu](/visualstudio/intellicode/code-style-inference) rozszerzenia intellicode dla programu Visual Studio wnioskuje style kodu z istniejącego kodu. Następnie tworzy niepusty plik EditorConfig z preferencjami stylu kodu.

- Począwszy od programu Visual Studio 2019, można [wygenerować plik EditorConfig na podstawie ustawień stylu kodu](/visualstudio/ide/code-styles-and-code-cleanup#code-styles-in-editorconfig-files) w **narzędziu** > **Opcje**.

## <a name="file-hierarchy-and-precedence"></a>Hierarchia i pierwszeństwo plików

Po dodaniu *.editorconfig* pliku do folderu w hierarchii plików, jego ustawienia mają zastosowanie do wszystkich odpowiednich plików na tym samym poziomie i poniżej. Możesz również zastąpić ustawienia EditorConfig dla konkretnego projektu, kodu lub część kodu, taki sposób, że używa różnych konwencji niż inne części bazy kodu. Może to być przydatne, gdy dołączyć kod z żadnym innym miejscu, a nie chcesz zmienić jego Konwencji.

Aby zastąpić niektóre lub wszystkie ustawienia EditorConfig, Dodaj *.editorconfig* pliku na poziomie hierarchii plików, które chcesz, aby te ustawienia zgodnym z przesłoniętą mają być stosowane. Nowe ustawienia pliku EditorConfig zostaną zastosowane do plików na tym samym poziomie i wszystkich podkatalogach.

![Hierarchia wtyczki EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Jeśli chcesz zastąpić niektóre, ale nie wszystkie ustawienia, określ tylko te ustawienia w *.editorconfig* pliku. Tylko te właściwości, które jawnie listy w pliku niższego poziomu zostaną zastąpione. Inne ustawienia z wyższego poziomu *.editorconfig* pliki w dalszym ciągu stosowane. Jeśli chcesz upewnić się, że _nie_ ustawienia z _wszelkie_ wyższego poziomu *.editorconfig* pliki są stosowane do tej części bazy kodu, Dodaj ```root=true``` właściwości niższego poziomu *.editorconfig* pliku:

```ini
# top-most EditorConfig file
root = true
```

Pliki EditorConfig są odczytywane z góry do dołu. Jeśli istnieje wiele właściwości o tej samej nazwie, pierwszeństwo ma właściwość ostatnio znaleziona o tej nazwie.

## <a name="edit-editorconfig-files"></a>Edytuj pliki EditorConfig

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

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Teraz, gdy ponownie naciśniesz **kartę** klucza, możesz uzyskać znaki tabulacji zamiast spacji.

![Klawisz TAB dodaje znak tabulacji](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Rozwiązywanie problemów z ustawieniami EditorConfig

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
- [Obsługa wtyczki EditorConfig dla usługi w języka](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Funkcje edytora kodu](writing-code-in-the-code-and-text-editor.md)
- [Polecenie EditorConfig (Visual Studio dla komputerów Mac)](/visualstudio/mac/editorconfig)
