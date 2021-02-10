---
title: Ustawienia EditorConfig
description: Dowiedz się, jak dodać plik EditorConfig do projektu lub bazy kodu w celu wymuszenia spójnych stylów kodowania dla wszystkich, które działają w bazie kodu.
ms.custom: SEO-VS-2020
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: mikadumont
ms.author: midumont
manager: jmartens
ms.openlocfilehash: 8ab90fda1f14521d59982ef7b5d20998cf61e505
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956844"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Tworzenie przenośnych, niestandardowych ustawień edytora za pomocą wtyczki EditorConfig

Można dodać plik EditorConfig do projektu lub bazy kodu w celu wymuszenia spójnych stylów kodowania dla wszystkich, które działają w bazie kodu. Ustawienia EditorConfig mają pierwszeństwo przed ustawieniami globalnego edytora tekstu programu Visual Studio. Oznacza to, że możesz dostosować każdą bazę kodu do używania ustawień edytora tekstów, które są specyficzne dla tego projektu. Nadal można ustawić własne preferencje edytora osobistego w oknie dialogowym **Opcje** programu Visual Studio. Te ustawienia są stosowane zawsze, gdy Pracujesz w bazie kodu bez pliku *. editorconfig* lub gdy plik *. editorconfig* nie przesłania określonego ustawienia. Przykładem takiego preferencja jest wcięcie &mdash; tabulatorów lub spacji.

Ustawienia EditorConfig są obsługiwane przez wiele edytorów kodu i środowisk IDE, w tym Visual Studio. Jest to składnik przenośny, który podróżuje z kodem i może wymuszać style kodowania nawet poza programem Visual Studio.

::: moniker range=">=vs-2019"

Po dodaniu pliku EditorConfig do projektu w programie Visual Studio, nowe wiersze kodu są formatowane zgodnie z ustawieniami EditorConfig. Formatowanie istniejącego kodu nie jest zmieniane, chyba że zostanie uruchomione jedno z następujących poleceń:

 - [Czyszczenie kodu](../ide/code-styles-and-code-cleanup.md) (**Ctrl** + **K**, **Ctrl** + **E**), które ma zastosowanie do wszystkich ustawień białych znaków, takich jak styl wcięcia i wybrane ustawienia stylu kodu, takie jak sortowanie `using` dyrektyw.
 - **Edytuj** > **Zaawansowane** > **Formatuj dokument** (lub **Ctrl** + **K**, **Ctrl** + **D** w profilu domyślnym), który stosuje tylko ustawienia białych znaków, na przykład styl wcięcia.

 ::: moniker-end

::: moniker range="=vs-2017"

Po dodaniu pliku EditorConfig do projektu w programie Visual Studio, nowe wiersze kodu są formatowane zgodnie z ustawieniami EditorConfig. Formatowanie istniejącego kodu nie jest zmieniane, chyba że użytkownik sformatuje dokument (**Edytuj**  >    >  **dokument formatu** zaawansowanego lub **Ctrl** + **K**, **Ctrl** + **D** w profilu domyślnym). Formatowanie dokumentu ma wpływ tylko na ustawienia białych znaków, takie jak styl wcięcia, chyba że skonfigurowano dokument formatu w celu [przeprowadzenia dodatkowego czyszczenia kodu](../ide/code-styles-and-code-cleanup.md#apply-code-styles).

 ::: moniker-end

::: moniker range="vs-2017"

Można zdefiniować, które ustawienia EditorConfig **mają być stosowane na** [stronie opcje **formatowania**](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [EditorConfig in Visual Studio dla komputerów Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Spójność kodu

Ustawienia w plikach EditorConfig umożliwiają przechowywanie spójnych stylów i ustawień kodowania w bazie kodu, takich jak styl wcięcia, Szerokość tabulacji, znaki końca wiersza, kodowanie i inne, niezależnie od używanego edytora lub środowiska IDE. Na przykład podczas kodowania w języku C#, jeśli baza kodu ma konwencję, aby zawsze zawierać pięć znaków spacji, dokumenty używają kodowania UTF-8, a każdy wiersz zawsze kończy się znakiem CR/LF, można skonfigurować plik *. editorconfig* .

Konwencje kodowania używane w Twoich projektach osobistych mogą różnić się od tych, które są używane w projektach Twojego zespołu. Na przykład, można wolisz, że podczas kodowania, wcięcie dodaje znak tabulacji. Jednak zespół może preferować, że wcięcie dodaje cztery znaki spacji zamiast znaku tabulacji. Pliki EditorConfig rozwiązują ten problem, umożliwiając konfigurację dla każdego scenariusza.

Ponieważ ustawienia są zawarte w pliku w bazie kodu, są one przesyłane razem z tą bazą kodu. Dopóki plik kodu zostanie otwarty w edytorze zgodnym z EditorConfig, zostaną zaimplementowane ustawienia edytora tekstu. Aby uzyskać więcej informacji na temat plików EditorConfig, zobacz witrynę sieci Web [EditorConfig.org](https://editorconfig.org/) .

> [!NOTE]
> Konwencji ustawionych w pliku EditorConfig nie można obecnie wymuszać w potoku ciągłej integracji/ciągłego dostarczania jako błędy kompilacji lub ostrzeżenia. Wszelkie odchylenia stylu są wyświetlane tylko w edytorze programu Visual Studio i **Lista błędów**.

## <a name="supported-settings"></a>Obsługiwane ustawienia

Edytor w programie Visual Studio obsługuje podstawowy zestaw [Właściwości EditorConfig](https://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- Zakończ \_ of_line
- zestaw
- Przycinanie \_ trailing_whitespace
- Wstaw \_ final_newline
- root

Ustawienia edytora EditorConfig są obsługiwane we wszystkich językach obsługiwanych przez program Visual Studio, z wyjątkiem języka XML. Ponadto EditorConfig obsługuje konwencje [stylów kodu](/dotnet/fundamentals/code-analysis/code-style-rule-options) , w tym [Język](/dotnet/fundamentals/code-analysis/style-rules/language-rules), [Formatowanie](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)i konwencje [nazewnictwa](/dotnet/fundamentals/code-analysis/style-rules/naming-rules) dla języków C# i Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Dodawanie i usuwanie plików EditorConfig

Po dodaniu pliku EditorConfig do projektu lub bazy kodu, wszelkie nowe wiersze napisanego kodu są formatowane według pliku EditorConfig. Jednak dodanie pliku EditorConfig nie konwertuje istniejących stylów do nowych, dopóki nie sformatujesz dokumentu lub uruchomisz [oczyszczanie kodu](../ide/code-styles-and-code-cleanup.md). Na przykład, jeśli w pliku znajdują się wcięcia, które są sformatowane przy użyciu kart i dodasz plik EditorConfig, który jest wcięty ze spacjami, znaki wcięcia nie są automatycznie konwertowane na spacje. Podczas formatowania dokumentu (**Edycja**  >  dokumentu w formacie **zaawansowanym**  >   lub **Ctrl** + **K**, **Ctrl** + **D**), ustawienia białych znaków w pliku EditorConfig są stosowane do istniejących wierszy kodu.

Jeśli usuniesz plik EditorConfig z projektu lub bazy kodu i chcesz, aby nowe wiersze kodu były sformatowane zgodnie z ustawieniami edytora globalnego, musisz zamknąć i ponownie otworzyć wszystkie otwarte pliki kodu.

### <a name="add-an-editorconfig-file-to-a-project"></a>Dodawanie pliku EditorConfig do projektu

1. Otwórz projekt lub rozwiązanie w programie Visual Studio. Wybierz węzeł projekt lub rozwiązanie, w zależności od tego, czy ustawienia *. editorconfig* mają być stosowane do wszystkich projektów w rozwiązaniu, czy tylko jeden. Możesz również wybrać folder w projekcie lub rozwiązaniu, aby dodać plik *. editorconfig* do programu.

1. Na pasku menu wybierz kolejno opcje **projekt**  >  **Dodaj nowy element** lub naciśnij **klawisze CTRL** + **SHIFT** + **A**.

   Zostanie otwarte okno dialogowe **Dodaj nowy element** .

1. W polu wyszukiwania Wyszukaj ciąg **editorconfig**.

   Dwa szablony elementów **plików editorconfig** są wyświetlane w wynikach wyszukiwania.

   ![Szablony elementów plików EditorConfig w programie Visual Studio](media/editorconfig-item-templates.png)

1. Wybierz szablon **plik editorconfig (domyślny)** , aby dodać wstępnie wypełniony plik editorconfig z dwoma podstawowymi opcjami editorconfig dla stylu i rozmiaru wcięcia. Lub wybierz szablon **plik editorconfig (.NET)** , aby dodać wstępnie wypełniony plik editorconfig z domyślnym [stylem kodu platformy .NET, formatowaniem i konwencjami nazewnictwa](/dotnet/fundamentals/code-analysis/code-style-rule-options).

   Plik *. editorconfig* pojawia się w Eksplorator rozwiązań i zostanie otwarty w edytorze.

   ![plik. editorconfig w Eksplorator rozwiązań i edytorze](media/editorconfig-dotnet.png)

1. Edytuj plik zgodnie z potrzebami.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Inne sposoby dodawania pliku EditorConfig

Istnieje kilka innych sposobów dodawania pliku EditorConfig do projektu:

- [Funkcja wnioskowania kodu](/visualstudio/intellicode/code-style-inference) rozszerzenia intellicode dla programu Visual Studio wnioskuje style kodu z istniejącego kodu. Następnie tworzy niepusty plik EditorConfig z preferencjami stylu kodu.

- Począwszy od programu Visual Studio 2019, można [wygenerować plik EditorConfig na podstawie ustawień stylu kodu](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) w   >  **opcji** narzędzia.

## <a name="file-hierarchy-and-precedence"></a>Hierarchia i pierwszeństwo plików

Po dodaniu pliku *. editorconfig* do folderu w hierarchii plików, jego ustawienia są stosowane do wszystkich odpowiednich plików na tym poziomie i poniżej. Możesz również zastąpić ustawienia EditorConfig dla określonego projektu, bazy kodu lub części bazy kodu, tak aby używały różnych konwencji niż inne części bazy kodu. Może to być przydatne w przypadku dołączania kodu z innych lokalizacji i nie należy zmieniać Konwencji.

Aby zastąpić niektóre lub wszystkie ustawienia EditorConfig, Dodaj plik *. EditorConfig* na poziomie hierarchii plików, do których mają być stosowane te ustawienia. Nowe ustawienia pliku EditorConfig mają zastosowanie do plików na tym samym poziomie i wszystkich podkatalogach.

![Hierarchia EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Jeśli chcesz przesłonić niektóre, ale nie wszystkie ustawienia, określ tylko te ustawienia w pliku *. editorconfig* . Tylko te właściwości, które zostały jawnie wymienione w pliku niższego poziomu, są zastępowane. Inne ustawienia z plików *editorconfig* wyższego poziomu są nadal stosowane. Jeśli chcesz upewnić się, że żadne ustawienia _z plików_ *editorconfig* wyższego poziomu _nie_ są stosowane do tej części bazy kodu, Dodaj ```root=true``` Właściwość do pliku niższego poziomu *. editorconfig* :

```ini
# top-most EditorConfig file
root = true
```

Pliki EditorConfig są odczytywane z góry do dołu. Jeśli istnieje wiele właściwości o tej samej nazwie, pierwszeństwo ma właściwość ostatnio znaleziona o tej nazwie.

## <a name="edit-editorconfig-files"></a>Edytuj pliki EditorConfig

Program Visual Studio ułatwia edytowanie plików *. editorconfig* , dostarczając listy uzupełniania IntelliSense.

![Technologia IntelliSense w pliku. editorconfig](media/editorconfig-intellisense-no-extension.png)

Po edytowaniu pliku EditorConfig należy ponownie załadować pliki kodu, aby nowe ustawienia zaczęły obowiązywać.

Jeśli edytujesz wiele plików *. editorconfig* , możesz znaleźć przydatne [rozszerzenie usługi językowej editorconfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) . Niektóre funkcje tego rozszerzenia obejmują wyróżnianie składni, ulepszone funkcje IntelliSense, walidacji i formatowanie kodu.

![IntelliSense z rozszerzeniem usługi języka EditorConfig](media/editorconfig-intellisense.png)

## <a name="example"></a>Przykład

Poniższy przykład przedstawia stan wcięcia fragmentu kodu w języku C# przed i po dodaniu pliku *. editorconfig* do projektu. Ustawienie **tabulatorów** w oknie dialogowym **Opcje** edytora tekstu programu Visual Studio jest ustawione na wygenerowanie znaków spacji po naciśnięciu klawisza **Tab** .

![Ustawienie karty Edytor tekstu](../ide/media/vside_editorconfig_tabsetting.png)

Zgodnie z oczekiwaniami naciśnięcie klawisza **Tab** w następnym wierszu wcięcie wiersza przez dodanie czterech dodatkowych znaków odstępu.

![Kod przed użyciem EditorConfig](../ide/media/vside_editorconfig_before.png)

Dodaj nowy plik o nazwie *. editorconfig* do projektu o następującej zawartości. `[*.cs]`To ustawienie oznacza, że ta zmiana dotyczy tylko plików kodu C# w projekcie.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Teraz po naciśnięciu klawisza **Tab** otrzymujesz znaki tabulacji zamiast spacji.

![Klawisz Tab dodaje znak tabulacji](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Rozwiązywanie problemów z ustawieniami EditorConfig

Jeśli istnieje plik EditorConfig gdziekolwiek w strukturze katalogów w lokalizacji projektu lub nowszej, program Visual Studio zastosuje ustawienia edytora w tym pliku do edytora. W takim przypadku na pasku stanu może zostać wyświetlony następujący komunikat:

   **"Preferencje użytkownika dla tego typu pliku są zastępowane przez konwencje kodowania tego projektu".**

Oznacza to, że jeśli dowolne ustawienia edytora w oknie Opcje **narzędzi**  >    >  **Edytor tekstu** (takie jak rozmiar i styl wcięcia, rozmiar karty lub konwencje kodowania) są określone w pliku EditorConfig na lub powyżej projektu w strukturze katalogów, konwencje w pliku EditorConfig zastępują ustawienia w **opcjach**. Możesz kontrolować to zachowanie, przełączając opcję **przestrzegaj konwencji kodowania projektu** w oknie Opcje **Narzędzia**  >    >  **Edytor tekstu**. Zaznaczenie opcji powoduje wyłączenie obsługi EditorConfig dla programu Visual Studio.

![Opcje narzędzi — przestrzeganie konwencji kodowania projektu](media/coding_conventions_option.png)

Pliki *. editorconfig* można znaleźć w katalogach nadrzędnych, otwierając wiersz polecenia i uruchamiając następujące polecenie z katalogu głównego dysku zawierającego projekt:

```Shell
dir .editorconfig /s
```

Zakres Konwencji EditorConfig można kontrolować przez ustawienie ```root=true``` właściwości w pliku *. EditorConfig* w katalogu głównym repozytorium lub w katalogu, w którym znajduje się Twój projekt. Program Visual Studio szuka pliku o nazwie *. editorconfig* w katalogu otwartego pliku i w każdym katalogu nadrzędnym. Wyszukiwanie kończy się po osiągnięciu ścieżki do katalogu głównego lub jeśli zostanie znaleziony plik *. editorconfig* ```root=true``` .

## <a name="see-also"></a>Zobacz też

- [Konwencje stylu kodu platformy .NET](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [Obsługa EditorConfig dla usługi językowej](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Funkcje edytora kodu](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio dla komputerów Mac)](/visualstudio/mac/editorconfig)
