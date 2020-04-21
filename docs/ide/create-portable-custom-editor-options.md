---
title: Ustawienia EditorConfig
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 5fdb0cc217062190e02e70b6361c8a3a2aa2f935
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81648524"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Tworzenie przenośnych, niestandardowych ustawień edytora za pomocą wtyczki EditorConfig

Można dodać [EditorConfig](https://editorconfig.org/) plik do projektu lub codebase wymuszanie spójne style kodowania dla wszystkich, który działa w codebase. Ustawienia EditorConfig mają pierwszeństwo przed globalnymi ustawieniami edytora tekstu programu Visual Studio. Oznacza to, że możesz dostosować każdą bazę kodu do używania ustawień edytora tekstów, które są specyficzne dla tego projektu. Nadal można ustawić własne preferencje edytora osobistego w oknie dialogowym **Opcje** programu Visual Studio. Te ustawienia mają zastosowanie za każdym razem, gdy pracujesz w bazie kodu bez pliku *.editorconfig* lub gdy plik *.editorconfig* nie zastępuje określonego ustawienia. Przykładem takiej preferencji są wcięcie kart stylu&mdash;lub spacji.

Ustawienia EditorConfig są obsługiwane przez wiele edytorów kodu i środowisk IDE, w tym programu Visual Studio. Jest to składnik przenośny, który przemieszcza się z kodem i może wymuszać style kodowania nawet poza programem Visual Studio.

::: moniker range=">=vs-2019"

Po dodaniu editorconfig pliku do projektu w programie Visual Studio, nowe wiersze kodu są formatowane zgodnie z Ustawienia EditorConfig. Formatowanie istniejącego kodu nie ulega zmianie, chyba że zostanie uruchomione jedno z następujących poleceń:

 - [Oczyszczanie kodu](../ide/code-styles-and-code-cleanup.md) **(Ctrl**+**K**, **Ctrl**+**E),** które stosuje wszystkie ustawienia odstępu, takie jak styl wcięcia i wybrane ustawienia stylu kodu, takie jak sposób sortowania `using` dyrektyw.
 - **Edytuj** > **dokument formatu** **zaawansowanego** > (lub **Ctrl**+**K**, **Ctrl**+**D** w profilu domyślnym), który stosuje tylko ustawienia odstępu, takie jak styl wcięcie.

 ::: moniker-end

::: moniker range="=vs-2017"

Po dodaniu editorconfig pliku do projektu w programie Visual Studio, nowe wiersze kodu są formatowane zgodnie z Ustawienia EditorConfig. Formatowanie istniejącego kodu nie ulega zmianie, chyba że dokument zostanie sformatowany, chyba że dokument zostanie sformatowany (**Edytuj** > **dokument formatu** **zaawansowanego** > lub **Ctrl**+**K**, **Ctrl**+**D** w profilu domyślnym). Formatowanie dokumentu ma wpływ tylko na ustawienia odstępu, takie jak styl wcięcia, chyba że skonfigurowano format dokumentu do [wykonywania dodatkowych oczyszczania kodu](../ide/code-styles-and-code-cleanup.md#apply-code-styles).

 ::: moniker-end

::: moniker range="vs-2017"

Można zdefiniować ustawienia EditorConfig, które mają być stosowane w **formacie dokumentu** na stronie Opcje [ **formatowania** ](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [EditorConfig w programie Visual Studio dla komputerów Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Spójność kodu

Ustawienia w plikach EditorConfig umożliwiają zachowanie spójnych stylów kodowania i ustawień w bazie kodu, takich jak styl wcięcie, szerokość karty, znaki końca wiersza, kodowanie i inne, niezależnie od używanego edytora lub IDE. Na przykład podczas kodowania w języku C#, jeśli codebase ma konwencję preferować, że wcięcie zawsze składać się z pięciu znaków spacji, dokumenty używają kodowania UTF-8, a każdy wiersz zawsze kończy się CR/LF, można skonfigurować plik *.editorconfig* to zrobić.

Konwencje kodowania używane w projektach osobistych mogą różnić się od konwencji używanych w projektach zespołu. Na przykład możesz preferować, że podczas kodowania wcięcie dodaje znak karty. Jednak twój zespół może preferować, że wcięcie dodaje cztery znaki spacji zamiast znaku karty. EditorConfig pliki rozwiązać ten problem, umożliwiając konfigurację dla każdego scenariusza.

Ponieważ ustawienia są zawarte w pliku w bazie kodu, podróżują wraz z tą bazą kodu. Tak długo, jak otworzyć plik kodu w EditorConfig zgodny edytor, ustawienia edytora tekstu są implementowane. Aby uzyskać więcej informacji na temat plików EditorConfig, zobacz [EditorConfig.org](https://editorconfig.org/) stronie internetowej.

> [!NOTE]
> Konwencje, które są ustawione w editorconfig pliku nie można obecnie wymuszać w potoku ciągłej integracji/ciągłego wdrażania jako błędy kompilacji lub ostrzeżenia. Wszelkie odchylenia stylu są wyświetlane tylko w edytorze programu Visual Studio i **na liście błędów**.

## <a name="supported-settings"></a>Obsługiwane ustawienia

Edytor w programie Visual Studio obsługuje podstawowy zestaw [właściwości EditorConfig:](https://editorconfig.org/#supported-properties)

- indent_style
- indent_size
- tab_width
- of_line\_końcowe
- Charset
- trailing_whitespace\_przycinanie
- wstaw final_newline\_
- root

Ustawienia edytora EditorConfig są obsługiwane we wszystkich językach obsługiwanych przez program Visual Studio z wyjątkiem pliku XML. Ponadto EditorConfig obsługuje konwencje [stylu kodu,](../ide/editorconfig-code-style-settings-reference.md) w tym [język,](../ide/editorconfig-language-conventions.md) [formatowanie](../ide/editorconfig-formatting-conventions.md)i konwencje [nazewnictwa](../ide/editorconfig-naming-conventions.md) dla języka C# i Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Dodawanie i usuwanie plików EditorConfig

Po dodaniu editorconfig pliku do projektu lub codebase, wszystkie nowe wiersze kodu, który piszesz są formatowane zgodnie z EditorConfig pliku. Jednak dodanie pliku EditorConfig nie konwertuje istniejących stylów na nowe, dopóki nie sformatujesz dokumentu lub nie uruchomisz [oczyszczania kodu](../ide/code-styles-and-code-cleanup.md). Na przykład, jeśli w pliku znajdują się wcięcie sformatowane za pomocą kart i dodasz plik EditorConfig, który wciąga spacjami, wcięcie znaków nie jest automatycznie konwertowane na spacje. Podczas formatowania dokumentu **(Edytuj** > **dokument formatu** **zaawansowanego** > lub **Ctrl**+**K**, **Ctrl**+**D)** ustawienia odstępu w pliku EditorConfig są stosowane do istniejących wierszy kodu.

Jeśli usuniesz plik EditorConfig z projektu lub bazy kodu i chcesz, aby nowe wiersze kodu były formatowane zgodnie z ustawieniami edytora globalnego, należy zamknąć i ponownie otworzyć wszystkie otwarte pliki kodu.

### <a name="add-an-editorconfig-file-to-a-project"></a>Dodawanie pliku EditorConfig do projektu

1. Otwórz projekt lub rozwiązanie w programie Visual Studio. Wybierz węzeł projektu lub rozwiązania, w zależności od tego, czy ustawienia *.editorconfig* powinny mieć zastosowanie do wszystkich projektów w rozwiązaniu, czy tylko jeden. Można również wybrać folder w projekcie lub rozwiązanie, aby dodać plik *.editorconfig* do.

1. Na pasku menu wybierz pozycję **Project** > **Add New Item**lub Klawisz **Ctrl**+**Shift**+**A**.

   Zostanie otwarte okno dialogowe **Dodawanie nowego elementu.**

1. W polu wyszukiwania wyszukaj **plik editorconfig**.

   W wynikach wyszukiwania wyświetlane są dwa szablony elementów **pliku editorconfig.**

   ![Szablony elementów pliku EditorConfig w programie Visual Studio](media/editorconfig-item-templates.png)

1. Wybierz szablon **editorconfig File (domyślny),** aby dodać plik EditorConfig wstępnie wypełniony dwoma podstawowymi opcjami EditorConfig dla stylu i rozmiaru wcięciem. Możesz też wybrać szablon **editorconfig File (.NET),** aby dodać plik EditorConfig wstępnie wypełniony domyślnym [stylem kodu .NET, formatowaniem i konwencjami nazewnictwa](../ide/editorconfig-code-style-settings-reference.md).

   Plik *.editorconfig* pojawia się w Eksploratorze rozwiązań i otwiera się w edytorze.

   ![.editorconfig w Eksploratorze rozwiązań i edytorze](media/editorconfig-dotnet.png)

1. Edytuj plik zgodnie z potrzebami.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Inne sposoby dodawania pliku EditorConfig

Istnieje kilka innych sposobów dodawania pliku EditorConfig do projektu:

- [Funkcja wnioskowania kodu](/visualstudio/intellicode/code-style-inference) IntelliCode for Visual Studio wywnioskować style kodu z istniejącego kodu. Następnie tworzy niepusty plik EditorConfig z preferencjami stylu kodu już zdefiniowane.

- Począwszy od programu Visual Studio 2019, można [wygenerować plik EditorConfig na podstawie ustawień stylu kodu](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) w**opcjach** **narzędzi** > .

## <a name="file-hierarchy-and-precedence"></a>Hierarchia plików i pierwszeństwo

Po dodaniu pliku *.editorconfig* do folderu w hierarchii plików jego ustawienia mają zastosowanie do wszystkich odpowiednich plików na tym poziomie i poniżej. Można również zastąpić ustawienia EditorConfig dla określonego projektu, bazy kodu lub części bazy kodu, tak aby używała ona innych konwencji niż inne części bazy kodu. Może to być przydatne, gdy dołączysz kod z innego miejsca i nie chcesz zmieniać jego konwencji.

Aby zastąpić niektóre lub wszystkie ustawienia EditorConfig, dodaj plik *.editorconfig* na poziomie hierarchii plików, który ma mieć zastosowanie do tych zastąpionych ustawień. Nowe ustawienia pliku EditorConfig mają zastosowanie do plików na tym samym poziomie i do wszystkich podkatalogów.

![Hierarchia EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Jeśli chcesz zastąpić niektóre, ale nie wszystkie ustawienia, określ tylko te ustawienia w pliku *.editorconfig.* Tylko te właściwości, które jawnie lista w pliku niższego poziomu są zastępowane. Inne ustawienia z plików *.editorconfig* wyższego poziomu nadal mają zastosowanie. Jeśli chcesz mieć pewność, że żadne ustawienia z _plików_ *.editorconfig* wyższego poziomu _nie_ są ```root=true``` stosowane do tej części bazy kodu, dodaj właściwość do pliku *.editorconfig* niższego poziomu:

```ini
# top-most EditorConfig file
root = true
```

EditorConfig pliki są odczytywane od góry do dołu. Jeśli istnieje wiele właściwości o tej samej nazwie, ostatnio znaleziona właściwość o tej nazwie ma pierwszeństwo.

## <a name="edit-editorconfig-files"></a>Edytuj pliki EditorConfig

Program Visual Studio pomaga edytować pliki *.editorconfig,* udostępniając listy uzupełnień IntelliSense.

![IntelliSense w pliku .editorconfig](media/editorconfig-intellisense-no-extension.png)

Po edycji pliku EditorConfig należy ponownie załadować pliki kodu, aby nowe ustawienia zostały zastosowane.

Jeśli edytujesz wiele plików *.editorconfig,* rozszerzenie [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) może okazać się pomocne. Niektóre funkcje tego rozszerzenia obejmują wyróżnianie składni, ulepszone intellisense, sprawdzanie poprawności i formatowanie kodu.

![IntelliSense z rozszerzeniem usługi editorConfig Language Service](media/editorconfig-intellisense.png)

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono stan wcięcie fragmentu kodu języka C# przed i po dodaniu pliku *.editorconfig* do projektu. Ustawienie **Karty** w oknie dialogowym **Opcje** edytora tekstu programu Visual Studio jest ustawione do tworzenia znaków spacji po naciśnięciu **klawisza Tab.**

![Ustawienie karty Edytor tekstu](../ide/media/vside_editorconfig_tabsetting.png)

Zgodnie z oczekiwaniami **naciśnięcie klawisza Tab** w następnym wierszu wcięcie wiersza przez dodanie czterech dodatkowych znaków odstępu.

![Kod przed użyciem EditorConfig](../ide/media/vside_editorconfig_before.png)

Dodaj nowy plik o nazwie *.editorconfig* do projektu, z następującą zawartością. Ustawienie `[*.cs]` oznacza, że ta zmiana dotyczy tylko plików kodu języka C# w projekcie.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Teraz po naciśnięciu **klawisza Tab** zamiast spacji są dostępne znaki tabulacji.

![Klawisz Tabulator dodaje znak karty](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Rozwiązywanie problemów z ustawieniami editorconfig

Jeśli istnieje EditorConfig plik w dowolnym miejscu w strukturze katalogów w lub powyżej lokalizacji projektu, Visual Studio stosuje ustawienia edytora w tym pliku do edytora. W takim przypadku na pasku stanu może zostać wyświetlony następujący komunikat:

   **"Preferencje użytkownika dla tego typu pliku są zastępowane przez konwencje kodowania tego projektu."**

Oznacza to, że jeśli dowolne ustawienia **edytora** > w**edytorze tekstu** **Opcje** > narzędzi (takie jak rozmiar i styl wcięcie, rozmiar karty lub konwencje kodowania) są określone w pliku EditorConfig w lub powyżej projektu w strukturze katalogów, konwencje w pliku EditorConfig zastępują ustawienia w **opcji**. To zachowanie można kontrolować, przełączanie opcji Postępuj zgodnie z **konwencjami kodowania projektu** w**Edytorze tekstu****Opcje** >  **narzędzi** > . Odznaczanie tej opcji powoduje wyłączenie obsługi editorconfig dla programu Visual Studio.

![Opcje narzędzi — postępuj zgodnie z konwencjami kodowania projektu](media/coding_conventions_option.png)

Wszystkie pliki *.editorconfig* można znaleźć w katalogach nadrzędnych, otwierając wiersz polecenia i uruchamiając następujące polecenie z katalogu głównego dysku zawierającego projekt:

```Shell
dir .editorconfig /s
```

Można kontrolować zakres konwencji EditorConfig, ustawiając ```root=true``` właściwość w pliku *.editorconfig* w katalogu głównym repozytorium lub w katalogu, w którego znajduje się projekt. Program Visual Studio wyszukuje plik o nazwie *.editorconfig* w katalogu otwartego pliku i w każdym katalogu nadrzędnym. Wyszukiwanie kończy się, gdy osiągnie ścieżkę pliku głównego lub jeśli ```root=true``` zostanie znaleziony plik *.editorconfig.*

## <a name="see-also"></a>Zobacz też

- [Konwencje stylu kodu .NET](../ide/editorconfig-code-style-settings-reference.md)
- [Obsługa EditorConfig dla usługi językowej](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Funkcje edytora kodu](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio dla komputerów Mac)](/visualstudio/mac/editorconfig)
