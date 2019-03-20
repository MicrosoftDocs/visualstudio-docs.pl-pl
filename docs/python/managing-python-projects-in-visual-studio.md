---
title: Zarządzaj projektami aplikacji języka Python
description: Projekty w programie Visual Studio Zarządzanie zależnościami między plikami i złożoność relacji w aplikacji.
ms.date: 03/18/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fb9682f46913aec0bfd7d91d5cd8d535410470bb
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194344"
---
# <a name="python-projects-in-visual-studio"></a>Projekty Python w programie Visual Studio

Aplikacje Python są zazwyczaj definiowane przy użyciu tylko pliki i foldery, ale ta struktura może stać się złożona jako aplikacji wydają się większe i być może obejmować automatycznego generowania plików JavaScript dla aplikacji sieci web i tak dalej. Projekt programu Visual Studio pomaga zarządzać taką złożonością. Projekt ( *.pyproj* pliku) identyfikuje źródła i plikami zawartości skojarzonymi z projektem, zawiera informacje o kompilacji dla każdego pliku, zachowuje informacje o integracji z systemami kontroli źródła i pomoże Ci organizowanie aplikacji do składników logicznych.

![Projektu w języku Python w Eksploratorze rozwiązań](media/projects-solution-explorer.png)

Ponadto projekty są zawsze zarządzane w ramach programu Visual Studio *rozwiązania*, która może zawierać dowolną liczbę projektów, które mogą odwoływać się do siebie nawzajem. Na przykład projektu języka Python może odwoływać się do projektu w języku C++, który implementuje modułu rozszerzenia. Za pomocą tej relacji programu Visual Studio automatycznie skompiluje projekt języka C++ (w razie potrzeby), po rozpoczęciu debugowania projektu w języku Python. (Aby uzyskać ogólne omówienie, zobacz [rozwiązań i projektów w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

Program Visual Studio udostępnia wiele szablonów projektu języka Python, aby szybko zdefiniować wiele struktur aplikacji, w tym szablonu, aby utworzyć projekt z istniejących drzewie folderów i szablon, aby utworzyć projekt zawsze przejrzyste i puste. Zobacz [szablony projektów](#project-templates) indeksu.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 obsługuje otwieranie folderu zawierającego kod Python i uruchamianie kodu bez tworzenia plików projektu i rozwiązania Visual Studio. Aby uzyskać więcej informacji, zobacz [Szybki Start: Otwórz i uruchamianie kodu języka Python w folderze](quickstart-05-python-visual-studio-open-folder.md). Istnieją jednak korzyści z korzystania z pliku projektu, zgodnie z opisem w tej sekcji.
::: moniker-end

> [!Tip]
> Bez projektu wszystkie wersje programu Visual Studio działać z kodu w języku Python. Można na przykład otwórz Python pliku przez siebie i korzystaj z automatycznego uzupełniania IntelliSense i debugowanie (klikając prawym przyciskiem myszy w edytorze i wybierając polecenie **rozpocząć debugowanie**). Ponieważ taki kod zawsze używa globalnego środowiska domyślnego, jednak mogą pojawić się błędy lub nieprawidłowe uzupełnienia Jeśli kod jest przeznaczona do innego środowiska. Ponadto program Visual Studio analizuje wszystkich plików i pakietów w folderze, z którego pojedynczy plik jest otwarty, może zużywać znaczną ilość czasu procesora CPU.
>
> Będzie polegać na utworzenie projektu programu Visual Studio z istniejącego kodu, zgodnie z opisem w [Tworzenie projektu z istniejących plików](#create-project-from-existing-files).

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Szczegółowe informacje: Korzystanie z kontroli źródła z projektów języka Python](https://youtu.be/Aq8eqApnugM) (witrynie youtube.com, 8 m 55s). |

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Dodaj pliki, Przypisz plik startowy i ustaw środowisk

Podczas opracowywania aplikacji, zazwyczaj konieczne dodanie nowych plików o różnych typach do projektu. Dodawanie takich plików jest wykonywane przez kliknięcie prawym przyciskiem myszy projekt i wybierając polecenie **Dodaj** > **istniejący element** za pomocą którego przeglądania w poszukiwaniu pliku do dodania, lub **Dodaj**  >  **Nowy element**, co spowoduje uruchomienie okna dialogowego za pomocą różnych szablonów elementów. Zgodnie z opisem na [elementu szablony](python-item-templates.md) odwołania, opcje obejmują pustych plików języka Python, klasa języka Python, testu jednostki i różne pliki powiązane z aplikacji sieci web. Możesz eksplorować tych opcji z projektem testowym, aby dowiedzieć się, co jest dostępne w używanej wersji programu Visual Studio.

Każdy projekt języka Python ma jeden plik startowy przypisane, wyświetlany czcionką pogrubioną w **Eksploratora rozwiązań**. Plik startowy jest plik który jest uruchamiany podczas uruchamiania debugowania (**F5** lub **debugowania** > **Rozpocznij debugowanie**) lub po uruchomieniu projektu **Interactive** okna (**Shift**+**Alt**+**F5** lub **debugowania**  >  **Wykonywania projektów w języku Python interaktywne**). Aby je zmienić, kliknij prawym przyciskiem myszy nowy plik i wybierz **Ustaw jako element startowy** (lub **Ustaw jako plik startowy** w starszych wersjach programu Visual Studio).

> [!Tip]
> Jeśli usuniesz plik startowy wybranego z projektu, a nie wybieraj nowe jednego, programu Visual Studio nie może ustalić, jakie plik w języku Python na początek z podczas próby uruchomienia projektu. W takim przypadku Visual Studio 2017 w wersji 15.6 i nowszych wskazuje błąd; wcześniejszych wersjach albo otworzyć okno danych wyjściowych z interpreter języka Python, uruchamiania lub zobacz okno dane wyjściowe są wyświetlane, ale zniknąć niemal natychmiast. Jeśli wystąpi dowolne z tych zachowań, sprawdź, czy plik startowy przypisane.
>
> Jeśli chcesz nie zamykaj okna dane wyjściowe jakiegokolwiek powodu, kliknij prawym przyciskiem myszy projekt, wybierz opcję **właściwości**, wybierz opcję **debugowania** kartę, a następnie dodaj `-i` do **Interpreter argumentów**  pola. Ten argument powoduje, że interpreter przejść do trybu interaktywnego, po zakończeniu działania programu, a tym samym utrzymywanie okna otwarte do momentu wprowadzenia **Ctrl**+**Z**  >  **Enter** aby wyjść.

::: moniker range="vs-2017"
Nowy projekt zawsze jest skojarzony z domyślnym środowisku Python globalnego. Aby skojarzyć projekt z innego środowiska (w tym środowisk wirtualnych), kliknij prawym przyciskiem myszy **środowiska Python** węzła projektu, wybierz opcję **środowiska Python Dodaj/Usuń**, i Wybierz te, które chcesz.
::: moniker-end
::: moniker range=">=vs-2019"
Nowy projekt zawsze jest skojarzony z domyślnym środowisku Python globalnego. Aby skojarzyć projekt z innego środowiska (w tym środowisk wirtualnych), kliknij prawym przyciskiem myszy **środowiska Python** węzła projektu, wybierz opcję **Dodaj środowiska...** i wybierz te, które mają. Można również użyć formantu listy rozwijanej środowisk na pasku narzędzi, aby wybrać i środowisko lub Dodaj do projektu.

![Dodaj polecenie środowiska na pasku narzędzi języka Python](media/environments/environments-toolbar-2019.png)
::: moniker-end

Zmiany aktywnego środowiska, kliknij prawym przyciskiem myszy żądany środowiska w **Eksploratora rozwiązań** i wybierz **aktywować środowisko** jak pokazano poniżej. Aby uzyskać więcej informacji, zobacz [wybierz środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

![Aktywowanie środowisko na potrzeby projektu języka Python](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Szablony projektów

Program Visual Studio zapewnia wiele sposobów konfigurowania projektu języka Python, od podstaw lub z istniejącego kodu. Aby użyć szablonu, wybierz **pliku** > **New** > **projektu** menu polecenie lub kliknij prawym przyciskiem myszy rozwiązanie w **rozwiązania Eksplorator** i wybierz **Dodaj** > **nowy projekt**, które przywołać **nowy projekt** poniższe okno dialogowe. Aby wyświetlić szablony specyficzne dla języka Python, wyszukaj "Python" lub wybierz **zainstalowane** > **Python** węzła:

![Okno dialogowe Nowy projekt z szablonami języka Python](media/projects-new-project-dialog.png)

Poniższa tabela zawiera podsumowanie szablonów dostępnych w programie Visual Studio 2017 (nie wszystkie szablony są dostępne we wszystkich poprzednich wersjach):

| Szablon | Opis |
| --- | --- |
| [**Z istniejącego kodu języka Python**](#create-project-from-existing-files) | Tworzy projekt programu Visual Studio na podstawie istniejącego kodu języka Python w strukturze folderu.  |
| **Aplikację w języku Python** | Struktura podstawowego projektu dla nowych aplikacji w języku Python z plikiem źródłowym pojedynczy, pusta. Domyślnie, projekt jest uruchamiany w interpretera konsoli w domyślnej globalnej środowisko, w którym można zmienić [przypisywanie innego środowiska](selecting-a-python-environment-for-a-project.md). |
| [**Usługa w chmurze platformy Azure**](python-azure-cloud-service-project-template.md) | Projekt służący do usługi w chmurze platformy Azure napisane w języku Python. |
| [**Projekty sieci Web**](python-web-application-project-templates.md) | Projekty dla aplikacji sieci web oparte na różnych platformach, takich jak Bottle, Django i Flask. |
| **Aplikace v Ironpythonu** | Podobne do szablonu aplikacji w języku Python, ale używa IronPython przez domyślne włączenie .NET międzyoperacyjności i trybu mieszanego debugowania za pomocą języków .NET. |
| **Aplikace WPF v Ironpythonu** | Struktury projektu, IronPython przy użyciu plików systemu Windows Presentation Foundation XAML dla interfejsu użytkownika aplikacji. Program Visual Studio udostępnia Projektant języka XAML, związanym z kodem może być napisana w języku Python, a aplikacja jest uruchamiana bez wyświetlania konsoli. |
| **Strony sieci Web w technologii Silverlight v Ironpythonu** | Projekt IronPython, który działa w przeglądarce, za pomocą programu Silverlight. Kod Python aplikacji znajduje się na stronie sieci web jako skrypt. Tag skryptu standardowy ściąga kodu JavaScript, która inicjuje IronPython działają w ramach programu Silverlight, z którego kodu w języku Python mogą wchodzić w interakcje z DOM. |
| **IronPython Windows Forms aplikacji** | Struktury projektu, IronPython przy użyciu interfejsu użytkownika tworzone za pomocą interfejsu Windows Forms przy użyciu kodu. Aplikacja jest uruchamiana bez wyświetlania konsoli. |
| **Tło w aplikacji (IoT)** | Obsługuje wdrażanie projektów języka Python do uruchamiania jako usługi w tle na urządzeniach. Odwiedź stronę [Centrum deweloperów systemu Windows IoT](https://dev.windows.com/en-us/iot) Aby uzyskać więcej informacji. |
| **Modułu rozszerzenia języka Python** | Ten szablon jest wyświetlany w obszarze Visual C++ Jeśli zainstalowałeś **Python natywne narzędzia programistyczne** z obciążeniem Python w programie Visual Studio 2017 (zobacz [instalacji](installing-python-support-in-visual-studio.md)). Zapewnia struktury podstawowe rozszerzenia C++ biblioteki DLL, podobnie jak opisane na [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md). |

> [!Note]
> Ponieważ interpretacji języka Python, projektów języka Python w programie Visual Studio nie generują autonomicznego pliku wykonywalnego, podobnie jak inne projekty skompilowanych języka (C#, na przykład). Aby uzyskać więcej informacji, zobacz [pytań i odpowiedzi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Utwórz projekt z istniejących plików

> [!Important]
> Proces opisany w tym miejscu nie Przenieś lub skopiuj oryginalnych plików źródłowych. Jeśli chcesz pracować z kopią, zduplikowane najpierw folder.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Połączone pliki

Połączone pliki są pliki, które są przenoszone do projektu, ale zazwyczaj znajdują się poza folderów projektu aplikacji. Pojawiają się na **Eksploratora rozwiązań** jako ikonę nałożone skrót normalnej plików: ![Ikona połączonego pliku](media/projects-linked-file-icon.png)

Połączone pliki są określone w *.pyproj* plików przy użyciu `<Compile Include="...">` elementu. Połączone pliki są użycie ścieżki względnej poza struktury katalogów, jawnych lub niejawnych użycie ścieżki w ramach **Eksploratora rozwiązań**:

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

Aby dodać istniejący element jako łącza, kliknij prawym przyciskiem myszy folderu w projekcie, w której chcesz dodać plik, a następnie wybierz **Dodaj** > **istniejący element**. W wyświetlonym oknie dialogowym Wybierz plik, a następnie wybierz **Dodaj jako Link** z listy rozwijanej na **Dodaj** przycisku. Pod warunkiem, że nie ma żadnych plików powodujące konflikt, to polecenie tworzy łącze w wybranym folderze. Jednak link nie zostanie dodane, jeśli istnieje już plik o takiej samej nazwie lub łącze do tego pliku już istnieje w projekcie.

Jeśli spróbujesz utworzyć link do pliku, który już istnieje w folderze projektu jest dodawany jako zwykłego pliku, a nie jako link. Aby przekonwertować plik łącza, wybierz polecenie **pliku** > **Zapisz jako** Aby zapisać plik do lokalizacji poza hierarchii projektu; Program Visual Studio automatycznie konwertuje go na łącze. Podobnie, można przekonwertować link ponownie za pomocą **pliku** > **Zapisz jako** można zapisać pliku gdzieś w hierarchii projektu.

Jeśli zostanie przeniesiony plik połączony **Eksploratora rozwiązań**, łącze jest przenoszony, ale nie wpływa na rzeczywisty plik. Podobnie usunięcie łącze spowoduje usunięcie linku bez wywierania wpływu na plik.

Nie można zmienić nazwy plików połączonych.

## <a name="references"></a>Odwołania

Program Visual Studio projektów pomocy technicznej, dodawanie odwołań do projektów i rozszerzenia, które są wyświetlane w obszarze **odwołania** w węźle **Eksploratora rozwiązań**:

![Odwołania do rozszerzenia w projektów języka Python](media/projects-extension-references.png)

Odwołania do rozszerzenia zazwyczaj wskazują współzależności między projektami i służą do zapewniania funkcji IntelliSense w czasie projektowania lub połączeń w czasie kompilacji. Projekty Python używać odwołań w podobny sposób, ale ze względu na dynamiczny charakter Python przede wszystkim wykorzystane w czasie projektowania zapewnienie ulepszona funkcja IntelliSense. One może również dla wdrożenia w systemie Microsoft Azure do zainstalowania dodatkowe zależności.

### <a name="extension-modules"></a>Modułów rozszerzeń

Odwołanie do *.pyd* plik umożliwia funkcji IntelliSense dla wygenerowanego modułu. Program Visual Studio ładuje *.pyd* mezzanine do interpretera języka Python i introspects jego typy i funkcje. Ponadto próbuje analizowanie ciągów dokumentacji funkcji w celu zapewnienia pomocy dotyczącej sygnatur.

Jeśli w dowolnym momencie modułu rozszerzenia zostaną zaktualizowane na dysku, Visual Studio zerwano modułu w tle. Ta akcja nie ma wpływu na zachowanie środowiska uruchomieniowego, ale niektóre ukończenia nie są dostępne do czasu ukończenia analizy.

Również może być konieczne dodanie [ścieżki wyszukiwania](search-paths.md) do folderu zawierającego modułu.

### <a name="net-projects"></a>Projekty .NET

Podczas pracy z IronPython, można dodać odwołania do zestawów .NET, aby włączyć technologię IntelliSense. Dla projektów platformy .NET w rozwiązaniu, kliknij prawym przyciskiem myszy **odwołania** węzeł w projekcie języka Python, wybierz opcję **Dodaj odwołanie**, wybierz opcję **projektów** , a następnie przejdź do żądany projekt. Dla bibliotek DLL pobrane oddzielnie, wybierz **Przeglądaj** zamiast kartę, a następnie przejdź do żądanego pliku DLL.

Ponieważ odwołań w IronPython nie są dostępne, dopóki wywołania `clr.AddReference('<AssemblyName>')` jest wprowadzone, musisz również dodać odpowiednią `clr.AddReference` wywołania do zestawu, zwykle na początku kodu. Na przykład, kod utworzony przez **Windows Forms v Ironpythonu** szablonu projektu w programie Visual Studio obejmuje dwa wywołań w górnej części pliku:

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

![Odwołania Instalatora WebPI](media/projects-webPI-components.png)
