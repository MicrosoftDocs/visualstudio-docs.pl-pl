---
title: Zarządzaj projektami aplikacji języka Python
description: Projekty w programie Visual Studio zarządzają zależnościami między plikami a złożonością relacji w aplikacji.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09203557fd9adcd6580dfafa981d6ed4f80eca16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936460"
---
# <a name="python-projects-in-visual-studio"></a>Projekty języka Python w programie Visual Studio

Aplikacje języka Python są zazwyczaj definiowane przy użyciu tylko folderów i plików, ale Ta struktura może stać się złożona, gdy aplikacje stają się coraz większe i mogą dotyczyć automatycznie generowanych plików, JavaScript dla aplikacji sieci Web i tak dalej. Projekt programu Visual Studio ułatwia zarządzanie tą złożonością. Projekt (plik *. pyproj* ) identyfikuje wszystkie pliki źródłowe i zawartości skojarzone z projektem, zawiera informacje o kompilacji każdego pliku, utrzymuje informacje do integracji z systemami kontroli źródła i pomaga organizować aplikację w składniki logiczne.

![Projekt w języku Python w Eksplorator rozwiązań](media/projects-solution-explorer.png)

Ponadto projekty są zawsze zarządzane w ramach *rozwiązania* programu Visual Studio, które może zawierać dowolną liczbę projektów, które mogą odwoływać się do siebie nawzajem. Na przykład projekt języka Python może odwoływać się do projektu C++, który implementuje moduł rozszerzenia. W przypadku tej relacji program Visual Studio automatycznie kompiluje projekt C++ (w razie potrzeby) po rozpoczęciu debugowania projektu języka Python. (W celu uzyskania ogólnej dyskusji zobacz [rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)).

Program Visual Studio oferuje różne szablony projektów języka Python umożliwiające szybkie konfigurowanie wielu struktur aplikacji, w tym szablonu do tworzenia projektu na podstawie istniejącego drzewa folderów i szablonu do tworzenia czystego, pustego projektu. Zobacz [Szablony projektów](#project-templates) dla indeksu.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Program Visual Studio 2019 obsługuje Otwieranie folderu zawierającego kod języka Python i uruchamianie tego kodu bez tworzenia plików projektu i rozwiązania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Szybki Start: otwieranie i uruchamianie kodu w języku Python w folderze](quickstart-05-python-visual-studio-open-folder.md). Istnieją jednak zalety korzystania z pliku projektu, zgodnie z opisem w tej sekcji.
::: moniker-end

> [!Tip]
> Bez projektu wszystkie wersje programu Visual Studio działają prawidłowo z kodem języka Python. Można na przykład otworzyć plik języka Python przez samego siebie i korzystać z funkcji autouzupełniania, IntelliSense i debugowania (klikając prawym przyciskiem myszy w edytorze i wybierając pozycję **Rozpocznij od debugowania**). Ponieważ kod ten zawsze używa domyślnego środowiska globalnego, jednak może być widoczne nieprawidłowe uzupełnianie lub błędy, jeśli kod jest przeznaczony dla innego środowiska. Ponadto program Visual Studio analizuje wszystkie pliki i pakiety w folderze, z którego jest otwierany pojedynczy plik, co może zużywać znaczny czas procesora CPU.
>
> Jest to prosta kwestia tworzenia projektu programu Visual Studio na podstawie istniejącego kodu, zgodnie z opisem w artykule [Tworzenie projektu z istniejących plików](#create-project-from-existing-files).

![ikona aparatu filmu wideo](../install/media/video-icon.png "Obejrzyj film") [głębokie szczegółowe: Użyj kontroli źródła z projektami języka Python](https://youtu.be/Aq8eqApnugM) (YouTube.com, 8 m 55s).

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Dodawanie plików, przypisywanie pliku startowego i Ustawianie środowisk

Podczas opracowywania aplikacji zwykle trzeba dodać do projektu nowe pliki różnych typów. Dodawanie takich plików odbywa się przez kliknięcie prawym przyciskiem myszy projektu i wybranie polecenia **Dodaj**  >  **istniejący element** , za pomocą którego można wyszukać plik do dodania lub **dodać**  >  **nowy element**, co spowoduje wyświetlenie okna dialogowego z różnymi szablonami elementów. Zgodnie z opisem w dokumentacji [szablonów elementu](python-item-templates.md) opcje obejmują puste pliki języka Python, klasę języka Python, test jednostkowy i różne pliki związane z aplikacjami sieci Web. Możesz zapoznać się z tymi opcjami przy użyciu projektu testowego, aby dowiedzieć się, co jest dostępne w używanej wersji programu Visual Studio.

Każdy projekt w języku Python ma jeden przypisany plik do uruchomienia przedstawiony pogrubiony w **Eksplorator rozwiązań**. Plik startowy to plik uruchamiany po rozpoczęciu debugowania (**F5** lub **Debug**  >  **Rozpocznij debugowanie**) lub po uruchomieniu projektu w oknie **interaktywnym** (**SHIFT** + **Alt** + **F5** lub **Debug**  >  **Execute Project w języku Python Interactive**). Aby to zmienić, kliknij prawym przyciskiem myszy nowy plik i wybierz polecenie **Ustaw jako element startowy** (lub **Ustaw jako plik startowy** we wcześniejszych wersjach programu Visual Studio).

> [!Tip]
> Jeśli wybrany plik startowy zostanie usunięty z projektu i nie wybierzesz nowego, program Visual Studio nie wie, w jakim pliku Python rozpoczyna się przy próbie uruchomienia projektu. W takim przypadku program Visual Studio 2017 w wersji 15,6 lub nowszej pokazuje błąd; wcześniejsze wersje otwierają okno danych wyjściowych z uruchomionym interpreterem języka Python lub pojawia się okno dane wyjściowe, ale następnie znika niemal natychmiast. Jeśli napotkasz dowolne z tych zachowań, sprawdź, czy masz przypisany plik startowy.
>
> Jeśli chcesz, aby okno dane wyjściowe było otwarte z dowolnego powodu, kliknij projekt prawym przyciskiem myszy, wybierz polecenie **Właściwości**, wybierz kartę **debugowanie** , a następnie Dodaj `-i` do pola **argumenty interpretera** . Ten argument powoduje, że interpreter przechodzi w tryb interaktywny po zakończeniu działania programu, dzięki czemu okno zostanie otwarte do momentu wprowadzenia **klawisza Ctrl** + **z**  >  **Enter** , aby wyjść.

::: moniker range="vs-2017"
Nowy projekt jest zawsze skojarzony z domyślnym globalnym środowiskiem Python. Aby skojarzyć projekt z innym środowiskiem (w tym środowiskami wirtualnymi), kliknij prawym przyciskiem myszy węzeł **środowiska Python** w projekcie, wybierz polecenie **Dodaj/Usuń środowiska Python** i wybierz żądane opcje.
::: moniker-end
::: moniker range=">=vs-2019"
Nowy projekt jest zawsze skojarzony z domyślnym globalnym środowiskiem Python. Aby skojarzyć projekt z innym środowiskiem (w tym środowiskami wirtualnymi), kliknij prawym przyciskiem myszy węzeł **środowiska Python** w projekcie, wybierz polecenie **Dodaj środowisko** i wybierz odpowiednie. Możesz również użyć kontrolki lista rozwijana środowiska na pasku narzędzi, aby wybrać środowisko i dodać kolejną do projektu.

![Polecenie Dodaj środowisko na pasku narzędzi języka Python](media/environments/environments-toolbar-2019.png)
::: moniker-end

Aby zmienić aktywne środowisko, kliknij prawym przyciskiem myszy odpowiednie środowisko w **Eksplorator rozwiązań** a następnie wybierz pozycję **Aktywuj środowisko** , jak pokazano poniżej. Aby uzyskać więcej informacji, zobacz [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

![Aktywowanie środowiska dla projektu języka Python](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Szablony projektów

Program Visual Studio oferuje kilka sposobów konfigurowania projektu języka Python — od podstaw lub z istniejącego kodu. Aby użyć szablonu, wybierz polecenie **plik**  >  **Nowy**  >  **projekt** menu, lub kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**, z którego korzystasz w oknie dialogowym **Nowy projekt** . Aby wyświetlić szablony dotyczące języka Python, Wyszukaj w języku Python lub wybierz zainstalowany węzeł języka   >  **Python** :

![Okno dialogowe nowego projektu z szablonami języka Python](media/projects-new-project-dialog.png)

Poniższa tabela zawiera podsumowanie szablonów dostępnych w programie Visual Studio 2017 i nowszych (nie wszystkie szablony są dostępne we wszystkich poprzednich wersjach):

| Template | Opis |
| --- | --- |
| [**Z istniejącego kodu języka Python**](#create-project-from-existing-files) | Tworzy projekt programu Visual Studio z istniejącego kodu w języku Python w strukturze folderów.  |
| **Aplikacja języka Python** | Podstawowa struktura projektu dla nowej aplikacji w języku Python z jednym pustym plikiem źródłowym. Domyślnie projekt jest uruchamiany w interpreterze konsoli domyślnego środowiska globalnego, które można zmienić, [przypisując inne środowisko](selecting-a-python-environment-for-a-project.md). |
| [**Usługa w chmurze platformy Azure**](python-azure-cloud-service-project-template.md) | Projekt usługi w chmurze platformy Azure zapisany w języku Python. |
| [**Projekty sieci Web**](python-web-application-project-templates.md) | Projekty dla aplikacji sieci Web na podstawie różnych platform, w tym butelek, Django i kolb. |
| **Aplikacja IronPython** | Podobnie jak szablon aplikacji w języku Python, ale używa IronPython domyślnie, włączając w to środowisko .NET Interop i debugowanie w trybie mieszanym z językami .NET. |
| **Aplikacja WPF IronPython** | Struktura projektu używająca IronPython Windows Presentation Foundation z plikami XAML dla interfejsu użytkownika aplikacji. Program Visual Studio udostępnia Projektant interfejsu użytkownika XAML, w którym kod można napisać w języku Python, a aplikacja jest uruchamiana bez wyświetlania konsoli programu. |
| **Strona sieci Web Silverlight IronPython** | Projekt IronPython, który działa w przeglądarce przy użyciu programu Silverlight. Kod języka Python aplikacji jest dołączany do strony sieci Web jako skrypt. Standardowy tag skryptu Pobiera kod JavaScript inicjujący IronPython działający w programie Silverlight, z którego kod języka Python może współdziałać z modelem DOM. |
| **IronPython Windows Forms aplikacji** | Struktura projektu używająca IronPython z interfejsem użytkownika utworzonym przy użyciu kodu z Windows Forms. Aplikacja jest uruchamiana bez wyświetlania konsoli programu. |
| **Aplikacja w tle (IoT)** | Obsługuje wdrażanie projektów języka Python do uruchamiania jako usługi w tle na urządzeniach. Aby uzyskać więcej informacji, odwiedź [Centrum deweloperów systemu Windows IoT](https://dev.windows.com/en-us/iot) . |
| **Moduł rozszerzenia języka Python** | Ten szablon jest wyświetlany w obszarze Visual C++, jeśli zainstalowano **natywne narzędzia programistyczne języka Python** z obciążeniem w języku Python w programie Visual Studio 2017 lub nowszym (zobacz [Instalacja](installing-python-support-in-visual-studio.md)). Zapewnia podstawową strukturę biblioteki DLL rozszerzenia C++, podobnie jak opisano w temacie [Tworzenie rozszerzenia c++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md). |

> [!Note]
> Ponieważ Python jest językiem interpretowanym, projekty języka Python w programie Visual Studio nie generują autonomicznego pliku wykonywalnego, takiego jak inne skompilowane projekty języka (na przykład w języku C#). Aby uzyskać więcej informacji, zobacz [pytania i odpowiedzi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Tworzenie projektu z istniejących plików

> [!Important]
> Opisany tutaj proces nie przenosi ani nie kopiuje oryginalnych plików źródłowych. Jeśli chcesz korzystać z kopii, najpierw należy zduplikować folder.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Połączone pliki

Pliki połączone są plikami, które są umieszczane w projekcie, ale zazwyczaj znajdują się poza folderami projektu aplikacji. Pojawiają się one w **Eksplorator rozwiązań** jako normalne pliki z zastąpioną ikoną skrótu: ![ ikona pliku połączonego](media/projects-linked-file-icon.png)

Pliki połączone są określone w pliku *pyproj* przy użyciu `<Compile Include="...">` elementu. Pliki połączone są niejawne, jeśli używają ścieżki względnej poza strukturą katalogów lub jawne, jeśli używają ścieżek w **Eksplorator rozwiązań**:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Pliki połączone są ignorowane w jednym z następujących warunków:

- Połączony plik zawiera metadane linku, a ścieżka określona w atrybucie include znajduje się w katalogu projektu
- Połączony plik duplikuje plik, który istnieje w hierarchii projektu.
- Połączony plik zawiera metadane łącza, a ścieżka linku jest ścieżką względną poza hierarchią projektu
- Ścieżka linku jest odblokowana

### <a name="work-with-linked-files"></a>Pracuj z połączonymi plikami

Aby dodać istniejący element jako link, kliknij prawym przyciskiem myszy folder w projekcie, w którym chcesz dodać plik, a następnie wybierz pozycję **Dodaj**  >  **istniejący element**. W wyświetlonym oknie dialogowym Wybierz plik, a następnie wybierz pozycję **Dodaj jako łącze** z listy rozwijanej na przycisku **Dodaj** . Pod warunkiem, że nie ma żadnych plików powodujących konflikt, to polecenie tworzy łącze w wybranym folderze. Łącze nie jest jednak dodawane, jeśli istnieje już plik o tej samej nazwie lub link do tego pliku już istnieje w projekcie.

Jeśli spróbujesz połączyć się z plikiem, który już istnieje w folderach projektu, jest on dodawany jako normalny plik, a nie jako link. Aby przekonwertować plik na link, wybierz pozycję **plik**  >  **Zapisz jako** , aby zapisać plik w lokalizacji poza hierarchią projektu; Program Visual Studio automatycznie konwertuje go na link. Analogicznie, link można przekonwertować z powrotem przy użyciu **pliku**  >  **Zapisz jako** , aby zapisać plik w obrębie hierarchii projektu.

W przypadku przenoszenia połączonego pliku w **Eksplorator rozwiązań** łącze jest przenoszone, ale nie ma to żadnego oddziaływania. Analogicznie, Usunięcie linku spowoduje usunięcie łącza bez wpływu na plik.

Nie można zmienić nazwy połączonych plików.

## <a name="references"></a>Odwołania

Projekty programu Visual Studio obsługują Dodawanie odwołań do projektów i rozszerzeń, które są wyświetlane w węźle **odwołania** w **Eksplorator rozwiązań**:

![Odwołania do rozszerzeń w projektach języka Python](media/projects-extension-references.png)

Odwołania do rozszerzeń zwykle wskazują zależności między projektami i służą do udostępniania technologii IntelliSense w czasie projektowania lub łączenia w czasie kompilacji. Projekty języka Python wykorzystują odwołania w podobny sposób, ale ze względu na dynamiczny charakter języka Python, głównie używane w czasie projektowania, aby zapewnić lepszą technologię IntelliSense. Mogą one również służyć do wdrażania Microsoft Azure w celu zainstalowania dodatkowych zależności.

### <a name="extension-modules"></a>Moduły rozszerzeń

Odwołanie do pliku *. PYD* włącza funkcję IntelliSense dla wygenerowanego modułu. Program Visual Studio ładuje plik *. PYD* do interpretera języka Python i introspects jego typy i funkcje. Próbuje również przeanalizować ciągi doc dla funkcji, aby zapewnić pomoc dotyczącą podpisu.

Jeśli w dowolnym momencie moduł rozszerzenia zostanie zaktualizowany na dysku, program Visual Studio ponownie przeanalizuje moduł w tle. Ta akcja nie ma wpływu na zachowanie w czasie wykonywania, ale niektóre uzupełniania nie są dostępne do czasu zakończenia analizy.

Może być również konieczne dodanie [ścieżki wyszukiwania](search-paths.md) do folderu zawierającego moduł.

### <a name="net-projects"></a>Projekty platformy .NET

Podczas pracy z usługą IronPython można dodać odwołania do zestawów .NET, aby włączyć funkcję IntelliSense. W przypadku projektów .NET w rozwiązaniu kliknij prawym przyciskiem myszy węzeł **odwołania** w projekcie języka Python, wybierz polecenie **Dodaj odwołanie**, wybierz kartę **projekty** i przejdź do odpowiedniego projektu. W przypadku bibliotek DLL, które zostały pobrane oddzielnie, wybierz kartę **Przeglądaj** , a następnie przejdź do odpowiedniej biblioteki DLL.

Ponieważ odwołania w IronPython nie są dostępne do momentu wywołania `clr.AddReference('<AssemblyName>')` , należy również dodać odpowiednie `clr.AddReference` wywołanie do zestawu, zazwyczaj na początku kodu. Na przykład kod utworzony przez szablon projektu **aplikacji IronPython Windows Forms** w programie Visual Studio zawiera dwa wywołania na początku pliku:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Instalatora WebPI projekty

Można dodać odwołania do wpisów produktów Instalatora WebPI na potrzeby wdrożenia, aby Microsoft Azure Cloud Services, gdzie można instalować dodatkowe składniki za pośrednictwem źródła danych Instalatora WebPI. Domyślnie wyświetlane źródło danych ma charakterystyczne dla języka Python i zawiera Django, CPython i inne podstawowe składniki. Możesz również wybrać własne źródło danych, jak pokazano poniżej. Podczas publikowania w Microsoft Azure, zadanie instalacji instaluje wszystkie produkty, do których istnieją odwołania.

> [!IMPORTANT]
> Projekty Instalatora WebPI nie są dostępne w programie Visual Studio 2017 lub Visual Studio 2019.

![Odwołania Instalatora WebPI](media/projects-webPI-components.png)
