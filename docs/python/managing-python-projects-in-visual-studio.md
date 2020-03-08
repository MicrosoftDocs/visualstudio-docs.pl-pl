---
title: Zarządzaj projektami aplikacji języka Python
description: Projekty w programie Visual Studio Zarządzanie zależnościami między plikami i złożoność relacji w aplikacji.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d50cbfbd517073544ebd172627d24bd7c3878fa5
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409051"
---
# <a name="python-projects-in-visual-studio"></a>Projekty Python w programie Visual Studio

Aplikacje Python są zazwyczaj definiowane przy użyciu tylko pliki i foldery, ale ta struktura może stać się złożona jako aplikacji wydają się większe i być może obejmować automatycznego generowania plików JavaScript dla aplikacji sieci web i tak dalej. Projekt programu Visual Studio pomaga zarządzać taką złożonością. Projekt (plik *. pyproj* ) identyfikuje wszystkie pliki źródłowe i zawartości skojarzone z projektem, zawiera informacje o kompilacji każdego pliku, utrzymuje informacje do integracji z systemami kontroli źródła i pomaga organizować aplikację w składniki logiczne.

![Projektu w języku Python w Eksploratorze rozwiązań](media/projects-solution-explorer.png)

Ponadto projekty są zawsze zarządzane w ramach *rozwiązania*programu Visual Studio, które może zawierać dowolną liczbę projektów, które mogą odwoływać się do siebie nawzajem. Na przykład projektu języka Python może odwoływać się do projektu w języku C++, który implementuje modułu rozszerzenia. Za pomocą tej relacji programu Visual Studio automatycznie skompiluje projekt języka C++ (w razie potrzeby), po rozpoczęciu debugowania projektu w języku Python. (W celu uzyskania ogólnej dyskusji zobacz [rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)).

Program Visual Studio udostępnia wiele szablonów projektu języka Python, aby szybko zdefiniować wiele struktur aplikacji, w tym szablonu, aby utworzyć projekt z istniejących drzewie folderów i szablon, aby utworzyć projekt zawsze przejrzyste i puste. Zobacz [Szablony projektów](#project-templates) dla indeksu.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Program Visual Studio 2019 obsługuje Otwieranie folderu zawierającego kod języka Python i uruchamianie tego kodu bez tworzenia plików projektu i rozwiązania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Szybki Start: otwieranie i uruchamianie kodu w języku Python w folderze](quickstart-05-python-visual-studio-open-folder.md). Istnieją jednak zalety korzystania z pliku projektu, zgodnie z opisem w tej sekcji.
::: moniker-end

> [!Tip]
> Bez projektu wszystkie wersje programu Visual Studio działają prawidłowo z kodem języka Python. Można na przykład otworzyć plik języka Python przez samego siebie i korzystać z funkcji autouzupełniania, IntelliSense i debugowania (klikając prawym przyciskiem myszy w edytorze i wybierając pozycję **Rozpocznij od debugowania**). Ponieważ taki kod zawsze używa globalnego środowiska domyślnego, jednak mogą pojawić się błędy lub nieprawidłowe uzupełnienia Jeśli kod jest przeznaczona do innego środowiska. Ponadto program Visual Studio analizuje wszystkich plików i pakietów w folderze, z którego pojedynczy plik jest otwarty, może zużywać znaczną ilość czasu procesora CPU.
>
> Jest to prosta kwestia tworzenia projektu programu Visual Studio na podstawie istniejącego kodu, zgodnie z opisem w artykule [Tworzenie projektu z istniejących plików](#create-project-from-existing-files).

|   |   |
|---|---|
| ![ikona aparatu filmu wideo](../install/media/video-icon.png "Obejrzyj wideo") | [Głębokie szczegółowe: Użyj kontroli źródła z projektami języka Python](https://youtu.be/Aq8eqApnugM) (YouTube.com, 8 m 55s). |

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Dodaj pliki, Przypisz plik startowy i ustaw środowisk

Podczas opracowywania aplikacji, zazwyczaj konieczne dodanie nowych plików o różnych typach do projektu. Dodawanie takich plików odbywa się przez kliknięcie prawym przyciskiem myszy projektu i wybranie polecenia **dodaj** > **istniejącego elementu** , za pomocą którego chcesz wyszukać plik do dodania, lub **Dodaj** > **nowy element**, który umożliwia wyświetlenie okna dialogowego z różnymi szablonami elementów. Zgodnie z opisem w dokumentacji [szablonów elementu](python-item-templates.md) opcje obejmują puste pliki języka Python, klasę języka Python, test jednostkowy i różne pliki związane z aplikacjami sieci Web. Możesz eksplorować tych opcji z projektem testowym, aby dowiedzieć się, co jest dostępne w używanej wersji programu Visual Studio.

Każdy projekt w języku Python ma jeden przypisany plik do uruchomienia przedstawiony pogrubiony w **Eksplorator rozwiązań**. Plik startowy to plik, który jest uruchamiany po rozpoczęciu debugowania (**F5** lub **Debug** > **Rozpocznij debugowanie**) lub po uruchomieniu projektu w oknie **interaktywnym** (**SHIFT**+**Alt**+**F5** lub **Debug** > **Execute Project w języku Python Interactive**). Aby to zmienić, kliknij prawym przyciskiem myszy nowy plik i wybierz polecenie **Ustaw jako element startowy** (lub **Ustaw jako plik startowy** we wcześniejszych wersjach programu Visual Studio).

> [!Tip]
> Jeśli wybrany plik startowy zostanie usunięty z projektu i nie wybierzesz nowego, program Visual Studio nie wie, w jakim pliku Python rozpoczyna się przy próbie uruchomienia projektu. W takim przypadku Visual Studio 2017 w wersji 15.6 i nowszych wskazuje błąd; wcześniejszych wersjach albo otworzyć okno danych wyjściowych z interpreter języka Python, uruchamiania lub zobacz okno dane wyjściowe są wyświetlane, ale zniknąć niemal natychmiast. Jeśli wystąpi dowolne z tych zachowań, sprawdź, czy plik startowy przypisane.
>
> Jeśli chcesz, aby okno dane wyjściowe było otwarte z dowolnego powodu, kliknij projekt prawym przyciskiem myszy, wybierz polecenie **Właściwości**, wybierz kartę **debugowanie** , a następnie Dodaj `-i` do pola **argumenty interpretera** . Ten argument powoduje, że interpreter przechodzi w tryb interaktywny po zakończeniu działania programu, dzięki czemu okno zostanie otwarte do momentu wprowadzenia **klawisza Ctrl**+**Z** > **Enter** , aby wyjść.

::: moniker range="vs-2017"
Nowy projekt zawsze jest skojarzony z domyślnym środowisku Python globalnego. Aby skojarzyć projekt z innym środowiskiem (w tym środowiskami wirtualnymi), kliknij prawym przyciskiem myszy węzeł **środowiska Python** w projekcie, wybierz polecenie **Dodaj/Usuń środowiska Python**i wybierz żądane opcje.
::: moniker-end
::: moniker range=">=vs-2019"
Nowy projekt zawsze jest skojarzony z domyślnym środowisku Python globalnego. Aby skojarzyć projekt z innym środowiskiem (w tym środowiskami wirtualnymi), kliknij prawym przyciskiem myszy węzeł **środowiska Python** w projekcie, wybierz polecenie **Dodaj środowisko**i wybierz odpowiednie. Możesz również użyć kontrolki lista rozwijana środowiska na pasku narzędzi, aby wybrać środowisko i dodać kolejną do projektu.

![Polecenie Dodaj środowisko na pasku narzędzi języka Python](media/environments/environments-toolbar-2019.png)
::: moniker-end

Aby zmienić aktywne środowisko, kliknij prawym przyciskiem myszy odpowiednie środowisko w **Eksplorator rozwiązań** a następnie wybierz pozycję **Aktywuj środowisko** , jak pokazano poniżej. Aby uzyskać więcej informacji, zobacz [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

![Aktywowanie środowisko na potrzeby projektu języka Python](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Szablony projektów

Program Visual Studio zapewnia wiele sposobów konfigurowania projektu języka Python, od podstaw lub z istniejącego kodu. Aby użyć szablonu, wybierz polecenie **plik** > **nowe** > **projektu** menu, lub kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **Nowy projekt**, z którego korzystasz w oknie dialogowym **Nowy projekt** . Aby wyświetlić szablony dotyczące języka Python, Wyszukaj w języku Python lub wybierz **zainstalowany** > węzeł języka **Python** :

![Okno dialogowe Nowy projekt z szablonami języka Python](media/projects-new-project-dialog.png)

Poniższa tabela zawiera podsumowanie szablonów dostępnych w programie Visual Studio 2017 i nowszych (nie wszystkie szablony są dostępne we wszystkich poprzednich wersjach):

| Szablon | Opis |
| --- | --- |
| [**Z istniejącego kodu języka Python**](#create-project-from-existing-files) | Tworzy projekt programu Visual Studio na podstawie istniejącego kodu języka Python w strukturze folderu.  |
| **Aplikacja języka Python** | Struktura podstawowego projektu dla nowych aplikacji w języku Python z plikiem źródłowym pojedynczy, pusta. Domyślnie projekt jest uruchamiany w interpreterze konsoli domyślnego środowiska globalnego, które można zmienić, [przypisując inne środowisko](selecting-a-python-environment-for-a-project.md). |
| [**Usługa w chmurze platformy Azure**](python-azure-cloud-service-project-template.md) | Projekt służący do usługi w chmurze platformy Azure napisane w języku Python. |
| [**Projekty sieci Web**](python-web-application-project-templates.md) | Projekty dla aplikacji sieci web oparte na różnych platformach, takich jak Bottle, Django i Flask. |
| **Aplikacja IronPython** | Podobne do szablonu aplikacji w języku Python, ale używa IronPython przez domyślne włączenie .NET międzyoperacyjności i trybu mieszanego debugowania za pomocą języków .NET. |
| **Aplikacja WPF IronPython** | Struktury projektu, IronPython przy użyciu plików systemu Windows Presentation Foundation XAML dla interfejsu użytkownika aplikacji. Program Visual Studio udostępnia Projektant języka XAML, związanym z kodem może być napisana w języku Python, a aplikacja jest uruchamiana bez wyświetlania konsoli. |
| **Strona sieci Web Silverlight IronPython** | Projekt IronPython, który działa w przeglądarce, za pomocą programu Silverlight. Kod Python aplikacji znajduje się na stronie sieci web jako skrypt. Tag skryptu standardowy ściąga kodu JavaScript, która inicjuje IronPython działają w ramach programu Silverlight, z którego kodu w języku Python mogą wchodzić w interakcje z DOM. |
| **IronPython Windows Forms aplikacji** | Struktury projektu, IronPython przy użyciu interfejsu użytkownika tworzone za pomocą interfejsu Windows Forms przy użyciu kodu. Aplikacja jest uruchamiana bez wyświetlania konsoli. |
| **Aplikacja w tle (IoT)** | Obsługuje wdrażanie projektów języka Python do uruchamiania jako usługi w tle na urządzeniach. Aby uzyskać więcej informacji, odwiedź [Centrum deweloperów systemu Windows IoT](https://dev.windows.com/en-us/iot) . |
| **Moduł rozszerzenia języka Python** | Ten szablon jest wyświetlany w C++ obszarze Wizualizacja, jeśli zainstalowano **natywne narzędzia programistyczne** języka Python z obciążeniem w języku Python w programie Visual Studio 2017 lub nowszym (zobacz [Instalacja](installing-python-support-in-visual-studio.md)). Zapewnia ona strukturę podstawową dla C++ rozszerzenia dll, podobnie jak opisano w temacie [Tworzenie C++ rozszerzenia dla języka Python](working-with-c-cpp-python-in-visual-studio.md). |

> [!Note]
> Ponieważ interpretacji języka Python, projektów języka Python w programie Visual Studio nie generują autonomicznego pliku wykonywalnego, podobnie jak inne projekty skompilowanych języka (C#, na przykład). Aby uzyskać więcej informacji, zobacz [pytania i odpowiedzi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Utwórz projekt z istniejących plików

> [!Important]
> Proces opisany w tym miejscu nie Przenieś lub skopiuj oryginalnych plików źródłowych. Jeśli chcesz pracować z kopią, zduplikowane najpierw folder.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Połączone pliki

Połączone pliki są pliki, które są przenoszone do projektu, ale zazwyczaj znajdują się poza folderów projektu aplikacji. Są one wyświetlane w **Eksplorator rozwiązań** jako normalne pliki ze zastąpioną ikoną skrótu: ![ikoną połączonego pliku](media/projects-linked-file-icon.png)

Pliki połączone są określone w pliku *pyproj* przy użyciu elementu `<Compile Include="...">`. Pliki połączone są niejawne, jeśli używają ścieżki względnej poza strukturą katalogów lub jawne, jeśli używają ścieżek w **Eksplorator rozwiązań**:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Połączone pliki są ignorowane w żadnej z następujących warunków:

- Połączony plik zawiera metadane łącze i ścieżce określonej w życie atrybut dołączenia w katalogu projektu
- Połączony plik duplikuje pliku, który istnieje w hierarchii projektu
- Połączony plik zawiera metadane łącze i ścieżka łącza jest ścieżką względną poza hierarchii projektu
- Dostęp do konta root ścieżka łącza

### <a name="work-with-linked-files"></a>Praca z plikami połączone

Aby dodać istniejący element jako link, kliknij prawym przyciskiem myszy folder w projekcie, w którym chcesz dodać plik, a następnie wybierz pozycję **dodaj** > **istniejący element**. W wyświetlonym oknie dialogowym Wybierz plik, a następnie wybierz pozycję **Dodaj jako łącze** z listy rozwijanej na przycisku **Dodaj** . Pod warunkiem, że nie ma żadnych plików powodujące konflikt, to polecenie tworzy łącze w wybranym folderze. Jednak link nie zostanie dodane, jeśli istnieje już plik o takiej samej nazwie lub łącze do tego pliku już istnieje w projekcie.

Jeśli spróbujesz utworzyć link do pliku, który już istnieje w folderze projektu jest dodawany jako zwykłego pliku, a nie jako link. Aby przekonwertować plik na link, wybierz pozycję **plik** > **Zapisz jako** , aby zapisać plik w lokalizacji poza hierarchią projektu; Program Visual Studio automatycznie konwertuje go na link. Analogicznie, link można przekonwertować z powrotem przy użyciu **pliku** > **Zapisz jako** , aby zapisać plik w obrębie hierarchii projektu.

W przypadku przenoszenia połączonego pliku w **Eksplorator rozwiązań**łącze jest przenoszone, ale nie ma to żadnego oddziaływania. Podobnie usunięcie łącze spowoduje usunięcie linku bez wywierania wpływu na plik.

Nie można zmienić nazwy plików połączonych.

## <a name="references"></a>Dokumentacja

Projekty programu Visual Studio obsługują Dodawanie odwołań do projektów i rozszerzeń, które są wyświetlane w węźle **odwołania** w **Eksplorator rozwiązań**:

![Odwołania do rozszerzenia w projektów języka Python](media/projects-extension-references.png)

Odwołania do rozszerzenia zazwyczaj wskazują współzależności między projektami i służą do zapewniania funkcji IntelliSense w czasie projektowania lub połączeń w czasie kompilacji. Projekty Python używać odwołań w podobny sposób, ale ze względu na dynamiczny charakter Python przede wszystkim wykorzystane w czasie projektowania zapewnienie ulepszona funkcja IntelliSense. One może również dla wdrożenia w systemie Microsoft Azure do zainstalowania dodatkowe zależności.

### <a name="extension-modules"></a>Modułów rozszerzeń

Odwołanie do pliku *. PYD* włącza funkcję IntelliSense dla wygenerowanego modułu. Program Visual Studio ładuje plik *. PYD* do interpretera języka Python i introspects jego typy i funkcje. Ponadto próbuje analizowanie ciągów dokumentacji funkcji w celu zapewnienia pomocy dotyczącej sygnatur.

Jeśli w dowolnym momencie modułu rozszerzenia zostaną zaktualizowane na dysku, Visual Studio zerwano modułu w tle. Ta akcja nie ma wpływu na zachowanie w czasie wykonywania, ale niektóre uzupełniania nie są dostępne do czasu zakończenia analizy.

Może być również konieczne dodanie [ścieżki wyszukiwania](search-paths.md) do folderu zawierającego moduł.

### <a name="net-projects"></a>Projekty .NET

Podczas pracy z IronPython, można dodać odwołania do zestawów .NET, aby włączyć technologię IntelliSense. W przypadku projektów .NET w rozwiązaniu kliknij prawym przyciskiem myszy węzeł **odwołania** w projekcie języka Python, wybierz polecenie **Dodaj odwołanie**, wybierz kartę **projekty** i przejdź do odpowiedniego projektu. W przypadku bibliotek DLL, które zostały pobrane oddzielnie, wybierz kartę **Przeglądaj** , a następnie przejdź do odpowiedniej biblioteki DLL.

Ponieważ odwołania w IronPython nie są dostępne do momentu wywołania `clr.AddReference('<AssemblyName>')`, należy również dodać odpowiednie wywołanie `clr.AddReference` do zestawu, zazwyczaj na początku kodu. Na przykład kod utworzony przez szablon projektu **aplikacji IronPython Windows Forms** w programie Visual Studio zawiera dwa wywołania na początku pliku:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Projekty Instalatora WebPI

Możesz dodać odwołania do wpisów dotyczących produktu Instalatora WebPI wdrożenia na Microsoft Azure Cloud Services, na którym można zainstalować dodatkowe składniki za pośrednictwem źródle danych Instalatora WebPI. Domyślnie wyświetlane źródło danych jest specyficzny dla języka Python i obejmuje Django, języka CPython i inne podstawowe składniki. Możesz wybrać własne źródło danych również, jak pokazano poniżej. Podczas publikowania w systemie Microsoft Azure, zadanie instalacji instaluje wszystkie produkty której dotyczy odwołanie.

> [!IMPORTANT]
> Projekty Instalatora WebPI nie są dostępne w programie Visual Studio 2017 lub Visual Studio 2019.

![Odwołania Instalatora WebPI](media/projects-webPI-components.png)
