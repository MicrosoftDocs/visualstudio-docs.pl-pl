---
title: Zarządzanie projektami aplikacji w języku Python
description: Projekty w Visual Studio zarządzać zależnościami między plikami i złożonością relacji w aplikacji.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c9a20ea3baee84657e26e2d98bb5726c20ceba9e
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254904"
---
# <a name="python-projects-in-visual-studio"></a>Projekty języka Python w programie Visual Studio

Aplikacje w języku Python są zwykle definiowane przy użyciu tylko folderów i plików, ale taka struktura może stać się złożona, gdy aplikacje stają się większe i mogą obejmować automatycznie generowane pliki, język JavaScript dla aplikacji internetowych i tak dalej. Projekt Visual Studio pomaga zarządzać tą złożonością. Projekt (plik *pyproj)* identyfikuje wszystkie pliki źródłowe i pliki zawartości skojarzone z projektem, zawiera informacje o kompilacji dla każdego pliku, przechowuje informacje w celu integracji z systemami kontroli źródła i ułatwia organizowanie aplikacji w składniki logiczne.

![Projekt języka Python w programie Eksplorator rozwiązań](media/projects-solution-explorer.png)

Ponadto projekty są zawsze zarządzane w ramach Visual Studio *rozwiązania*, które może zawierać dowolną liczbę projektów, które mogą odwoływać się do siebie nawzajem. Na przykład projekt języka Python może odwoływać się do projektu języka C++, który implementuje moduł rozszerzenia. W przypadku tej relacji Visual Studio automatycznie skompilować projekt języka C++ (w razie potrzeby) po rozpoczęciu debugowania projektu w języku Python. (Aby uzyskać ogólne omówienie, zobacz [Rozwiązania i projekty w Visual Studio).](../ide/solutions-and-projects-in-visual-studio.md)

Visual Studio udostępnia różne szablony projektów języka Python do szybkiego skonfigurowania wielu struktur aplikacji, w tym szablon do tworzenia projektu na podstawie istniejącego drzewa folderów i szablon do tworzenia czystego, pustego projektu. Zobacz [Szablony projektów,](#project-templates) aby uzyskać indeks.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 obsługuje otwieranie folderu zawierającego kod języka Python i uruchamianie tego kodu bez Visual Studio plików projektu i rozwiązania. Aby uzyskać więcej informacji, zobacz [Szybki start: otwieranie i uruchamianie kodu języka Python w folderze](quickstart-05-python-visual-studio-open-folder.md). Istnieją jednak korzyści z używania pliku projektu, jak wyjaśniono w tej sekcji.
::: moniker-end

> [!Tip]
> Bez projektu wszystkie wersje aplikacji Visual Studio dobrze działają z kodem języka Python. Na przykład możesz otworzyć plik w języku Python samodzielnie i korzystać z autouzupełniania, funkcji IntelliSense i debugowania (klikając prawym przyciskiem myszy w edytorze i wybierając pozycję **Rozpocznij od debugowania).** Ponieważ taki kod zawsze używa domyślnego środowiska globalnego, możesz jednak zobaczyć niepoprawne uzupełnienia lub błędy, jeśli kod jest przeznaczony dla innego środowiska. Ponadto Visual Studio analizuje wszystkie pliki i pakiety w folderze, z którego jest otwierany pojedynczy plik, co może zużywać znaczną ilość czasu procesora CPU.
>
> Proste jest utworzenie projektu na Visual Studio kodu, zgodnie z opisem w tece Create a project from existing files (Tworzenie projektu [na pomocą istniejących plików).](#create-project-from-existing-files)

![ikona aparatu filmowego dla wideo](../install/media/video-icon.png "Obejrzyj film") [Deep Dive: używanie kontroli źródła](https://youtu.be/Aq8eqApnugM) w projektach języka Python (youtube.com, 8 min 55 s).

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Dodawanie plików, przypisywanie pliku startowego i ustawianie środowisk

Podczas tworzenia aplikacji zwykle trzeba dodać do projektu nowe pliki różnych typów. Dodawanie takich plików odbywa się przez kliknięcie projektu prawym przyciskiem myszy i wybranie pozycji Dodaj istniejący element, za pomocą której można przeglądać plik do dodania, lub pozycji Dodaj nowy element, co pozwala na wyświetlone okno dialogowe z różnymi szablonami  >     >  elementów. Jak opisano w [odwołaniach do szablonów](python-item-templates.md) elementów, opcje obejmują puste pliki języka Python, klasę języka Python, test jednostkowy i różne pliki związane z aplikacjami internetowymi. Możesz eksplorować te opcje za pomocą projektu testowego, aby dowiedzieć się, co jest dostępne w Twojej wersji Visual Studio.

Każdy projekt w języku Python ma jeden przypisany plik startowy, który jest wyświetlany pogrubioną **czcionką w Eksplorator rozwiązań**. Plik startowy to plik uruchamiany po rozpoczęciu debugowania **(F5** lub **Debugowanie** rozpocznij debugowanie) lub po uruchomieniu projektu w oknie Interaktywny  >  **(Shift**  + **Alt** + **F5** lub   >  **Debuguj** projekt wykonania w interaktywnym języku Python). Aby go zmienić, kliknij prawym przyciskiem myszy nowy plik  i wybierz polecenie Ustaw jako element startowy **(lub** Ustaw jako plik startowy w starszych wersjach programu Visual Studio).

> [!Tip]
> Jeśli usuniesz wybrany plik startowy z projektu i nie wybierzesz nowego, program Visual Studio nie wie, od jakiego pliku języka Python zacząć podczas próby uruchomienia projektu. W takim przypadku w Visual Studio 2017 w wersji 15.6 lub nowszej jest wyświetlany błąd; Wcześniejsze wersje otwierają okno danych wyjściowych z uruchomionym interpreterem języka Python lub pojawia się okno danych wyjściowych, ale potem niemal natychmiast znika. Jeśli napotkasz dowolne z tych zachowań, sprawdź, czy masz przypisany plik startowy.
>
> Jeśli z jakiegoś powodu chcesz, aby okno danych wyjściowych było otwarte, kliknij prawym przyciskiem myszy projekt, wybierz pozycję **Właściwości,** wybierz kartę **Debugowanie,** a następnie dodaj do `-i` pola **Argumenty interpretera.** Ten argument powoduje, że interpreter przejść w tryb interaktywny po zakończeniu działania programu, dzięki czemu okno będzie otwarte do momentu wciśniętego **klawisza Ctrl** + **Z**  >  **Enter,** aby zakończyć działanie.

::: moniker range="vs-2017"
Nowy projekt jest zawsze kojarzony z domyślnym globalnym środowiskiem języka Python. Aby skojarzyć projekt z innym środowiskiem (w tym środowiskami wirtualnymi), kliknij prawym przyciskiem myszy węzeł Środowiska **Języka Python** w projekcie, wybierz pozycję **Dodaj/usuń** środowiska Python i wybierz odpowiednie środowiska.
::: moniker-end
::: moniker range=">=vs-2019"
Nowy projekt jest zawsze kojarzony z domyślnym globalnym środowiskiem języka Python. Aby skojarzyć projekt z innym środowiskiem (w tym środowiskami wirtualnymi), kliknij prawym przyciskiem myszy węzeł Środowiska **języka Python** w projekcie, wybierz pozycję Dodaj **środowisko..** i wybierz odpowiednie środowiska. Możesz również użyć kontrolki listy rozwijanej środowisk na pasku narzędzi, aby wybrać środowisko i dodać kolejne do projektu.

![Polecenie Dodaj środowisko na pasku narzędzi języka Python](media/environments/environments-toolbar-2019.png)
::: moniker-end

Aby zmienić aktywne środowisko, kliknij prawym przyciskiem myszy odpowiednie środowisko w Eksplorator rozwiązań **wybierz** pozycję Aktywuj **środowisko,** jak pokazano poniżej. Aby uzyskać więcej informacji, [zobacz Select an environment for a project (Wybieranie środowiska dla projektu).](selecting-a-python-environment-for-a-project.md)

![Aktywowanie środowiska dla projektu w języku Python](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Szablony projektów

Visual Studio udostępnia wiele sposobów na skonfigurowanie projektu w języku Python od podstaw lub z istniejącego kodu. Aby użyć szablonu, wybierz polecenie menu File New Project (Plik nowy projekt) lub kliknij prawym przyciskiem myszy rozwiązanie w programie Eksplorator rozwiązań i wybierz pozycję Add New Project (Dodaj nowy projekt). Oba te elementy są wyświetlane w oknie  >    >   dialogowym    >   **Nowy** projekt poniżej. Aby wyświetlić szablony specyficzne dla języka Python, wyszukaj pozycję "Python" lub wybierz węzeł **Zainstalowany**  >  **język Python:**

![Okno dialogowe Nowy projekt z szablonami języka Python](media/projects-new-project-dialog.png)

::: moniker range="<=vs-2017"

W poniższej tabeli podsumowano szablony dostępne w programie Visual Studio 2017 (nie wszystkie szablony są dostępne we wszystkich poprzednich wersjach):

| Template | Opis |
| --- | --- |
| [**Z istniejącego kodu w języku Python**](#create-project-from-existing-files) | Tworzy projekt Visual Studio na pomocą istniejącego kodu języka Python w strukturze folderów.  |
| **Aplikacja w języku Python** | Podstawowa struktura projektu dla nowej aplikacji w języku Python z pojedynczym, pustym plikiem źródłowym. Domyślnie projekt jest uruchamiany w interpreterze konsoli domyślnego środowiska globalnego, który można zmienić, [przypisując inne środowisko](selecting-a-python-environment-for-a-project.md). |
| [**Usługa w chmurze platformy Azure**](python-azure-cloud-service-project-template.md) | Projekt dla usługi w chmurze platformy Azure napisany w języku Python. |
| [**Projekty sieci Web**](python-web-application-project-templates.md) | Projekty aplikacji internetowych oparte na różnych platformach, takich jak Bottle, Django i Flask. |
| **Aplikacja IronPython** | Podobnie jak szablon aplikacji w języku Python, ale domyślnie używa oprogramowania IronPython, włączając międzyoptyk .NET i debugowanie w trybie mieszanym w językach .NET. |
| **Aplikacja IronPython WPF** | Struktura projektu korzystająca z ironPython Windows Presentation Foundation plikami XAML dla interfejsu użytkownika aplikacji. Visual Studio projektanta interfejsu użytkownika XAML, jego kod może być napisany w języku Python, a aplikacja działa bez wyświetlania konsoli. |
| **Strona internetowa programu IronPython Silverlight** | Projekt IronPython, który działa w przeglądarce przy użyciu programu Silverlight. Kod języka Python aplikacji jest uwzględniany na stronie internetowej jako skrypt. Tag pierwotnego skryptu ściąga kod JavaScript, który inicjuje środowisko IronPython uruchomione w programie Silverlight, z którego kod języka Python może wchodzić w interakcję z modelem DOM. |
| **IronPython Windows Forms Application** | Struktura projektu korzystająca z oprogramowania IronPython z interfejsem użytkownika utworzonym przy użyciu kodu Windows Forms. Aplikacja działa bez wyświetlania konsoli. |
| **Aplikacja w tle (IoT)** | Obsługuje wdrażanie projektów języka Python w celu uruchamiania ich jako usług w tle na urządzeniach. Odwiedź Centrum [deweloperów systemu Windows IoT,](https://dev.windows.com/en-us/iot) aby uzyskać więcej informacji. |
| **Moduł rozszerzenia języka Python** | Ten szablon jest wyświetlany w Visual C++ jeśli natywne narzędzia programskie języka **Python** zostały zainstalowane z obciążeniem języka Python w wersji Visual Studio 2017 lub nowszej (zobacz [Instalacja](installing-python-support-in-visual-studio.md)). Zapewnia podstawową strukturę biblioteki DLL rozszerzenia języka C++, podobną do opisanej w tece Create a C++ extension for Python (Tworzenie rozszerzenia [C++ dla języka Python).](working-with-c-cpp-python-in-visual-studio.md) |
::: moniker-end

::: moniker range=">=vs-2019"

W poniższej tabeli podsumowano szablony dostępne w programie Visual Studio 2019 (nie wszystkie szablony są dostępne we wszystkich poprzednich wersjach):

| Template | Opis |
| --- | --- |
| [**Z istniejącego kodu w języku Python**](#create-project-from-existing-files) | Tworzy projekt Visual Studio na pomocą istniejącego kodu języka Python w strukturze folderów.  |
| **Aplikacja w języku Python** | Podstawowa struktura projektu dla nowej aplikacji w języku Python z pojedynczym, pustym plikiem źródłowym. Domyślnie projekt jest uruchamiany w interpreterze konsoli domyślnego środowiska globalnego, który można zmienić, [przypisując inne środowisko](selecting-a-python-environment-for-a-project.md). |
| [**Projekty sieci Web**](python-web-application-project-templates.md) | Projekty aplikacji internetowych oparte na różnych platformach, takich jak Bottle, Django i Flask. |
| **Aplikacja IronPython** | Podobnie jak szablon aplikacji w języku Python, ale domyślnie używa oprogramowania IronPython, włączając międzyoptyk .NET i debugowanie w trybie mieszanym w językach .NET. |
| **Aplikacja IronPython WPF** | Struktura projektu korzystająca z ironPython Windows Presentation Foundation plikami XAML dla interfejsu użytkownika aplikacji. Visual Studio projektanta interfejsu użytkownika XAML, jego kod może być napisany w języku Python, a aplikacja działa bez wyświetlania konsoli. |
| **Strona internetowa programu IronPython Silverlight** | Projekt IronPython, który działa w przeglądarce przy użyciu programu Silverlight. Kod języka Python aplikacji jest uwzględniany na stronie internetowej jako skrypt. Tag pierwotnego skryptu ściąga kod JavaScript, który inicjuje środowisko IronPython uruchomione w programie Silverlight, z którego kod języka Python może wchodzić w interakcję z modelem DOM. |
| **IronPython Windows Forms Application** | Struktura projektu korzystająca z oprogramowania IronPython z interfejsem użytkownika utworzonym przy użyciu kodu Windows Forms. Aplikacja działa bez wyświetlania konsoli. |
| **Aplikacja w tle (IoT)** | Obsługuje wdrażanie projektów języka Python w celu uruchamiania ich jako usług w tle na urządzeniach. Odwiedź Centrum [deweloperów systemu Windows IoT,](https://dev.windows.com/en-us/iot) aby uzyskać więcej informacji. |
| **Moduł rozszerzenia języka Python** | Ten szablon jest wyświetlany w Visual C++ jeśli natywne narzędzia programskie języka **Python** zostały zainstalowane z obciążeniem języka Python w wersji Visual Studio 2017 lub nowszej (zobacz [Instalacja](installing-python-support-in-visual-studio.md)). Zapewnia podstawową strukturę biblioteki DLL rozszerzenia języka C++, podobną do opisanej w tece Create a C++ extension for Python (Tworzenie rozszerzenia [C++ dla języka Python).](working-with-c-cpp-python-in-visual-studio.md) |
::: moniker-end

> [!Note]
> Ponieważ Język Python jest językiem interpretowanym, projekty języka Python w języku Visual Studio nie tworzyć autonomicznego pliku wykonywalnego, tak jak inne skompilowane projekty językowe (na przykład C#). Aby uzyskać więcej informacji, zobacz [pytania i odpowiedzi.](overview-of-python-tools-for-visual-studio.md#questions-and-answers)

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Tworzenie projektu z istniejących plików

> [!Important]
> Opisany tutaj proces nie powoduje przeniesienia ani skopiowania oryginalnych plików źródłowych. Jeśli chcesz pracować z kopią, najpierw duplikuj folder.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Połączone pliki

Połączone pliki to pliki, które są przekazywane do projektu, ale zwykle znajdują się poza folderami projektu aplikacji. Są one wyświetlane **w Eksplorator rozwiązań** jako zwykłe pliki z nałogowoną ikoną skrótu: ![ Ikona połączonego pliku](media/projects-linked-file-icon.png)

Połączone pliki są określone w *pliku pyproj* przy użyciu `<Compile Include="...">` elementu . Połączone pliki są niejawne, jeśli używają ścieżki względnej poza strukturą katalogów, lub jawnie, jeśli używają ścieżek w **Eksplorator rozwiązań**:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Połączone pliki są ignorowane w dowolnym z następujących warunków:

- Połączony plik zawiera metadane linku i ścieżkę określoną w atrybutze Include znajduje się w katalogu projektu
- Połączony plik duplikuje plik, który istnieje w hierarchii projektu
- Połączony plik zawiera metadane linku, a ścieżka linku jest ścieżką względną poza hierarchią projektu
- Ścieżka linku ma dostęp do katalogu głównego

### <a name="work-with-linked-files"></a>Praca z połączonymi plikami

Aby dodać istniejący element jako link, kliknij prawym przyciskiem myszy folder w projekcie, w którym chcesz dodać plik, a następnie wybierz pozycję   >  **Dodaj istniejący element**. W wyświetlonym oknie dialogowym wybierz plik i wybierz pozycję Dodaj jako **link** z listy rozwijanej na **przycisku** Dodaj. Jeśli nie ma żadnych plików powodujące konflikt, to polecenie tworzy link w wybranym folderze. Jednak link nie jest dodawany, jeśli istnieje już plik o takiej samej nazwie lub link do tego pliku już istnieje w projekcie.

Próba połączenia z plikiem, który już istnieje w folderach projektu, zostanie dodana jako zwykły plik, a nie jako link. Aby przekonwertować plik na link, wybierz **pozycję** Plik Zapisz jako, aby zapisać plik w lokalizacji poza  >   hierarchią projektu. Visual Studio automatycznie konwertuje ją na link. Podobnie link można przekonwertować z powrotem przy użyciu funkcji **Zapisz** jako pliku w celu zapisania pliku w  >   hierarchii projektu.

Jeśli przeniesiesz połączony plik w **Eksplorator rozwiązań**, link zostanie przeniesiony, ale nie ma to wpływu na rzeczywisty plik. Podobnie usunięcie linku powoduje usunięcie linku bez wpływu na plik.

Nie można zmienić nazwy połączonych plików.

## <a name="references"></a>Odwołania

Visual Studio obsługują dodawanie odwołań do projektów i rozszerzeń, które są wyświetlane w węźle **Odwołania** w **programie Eksplorator rozwiązań**:

![Odwołania do rozszerzeń w projektach języka Python](media/projects-extension-references.png)

Odwołania do rozszerzeń zwykle wskazują zależności między projektami i są używane do zapewnienia funkcji IntelliSense w czasie projektowania lub łączenia w czasie kompilacji. W projektach języka Python odwołania są używane w podobny sposób, ale ze względu na dynamiczny charakter języka Python są one używane głównie w czasie projektowania w celu zapewnienia ulepszonej funkcji IntelliSense. Można ich również używać do wdrażania w Microsoft Azure instalacji dodatkowych zależności.

### <a name="extension-modules"></a>Moduły rozszerzeń

Odwołanie do pliku *PYD* umożliwia korzystanie z funkcji IntelliSense dla wygenerowanego modułu. Visual Studio ładuje plik *pyd* do interpretera języka Python i introspects jego typy i funkcje. Próbuje również analizowanie ciągów doc dla funkcji w celu zapewnienia pomocy dotyczącej sygnatur.

Jeśli w dowolnym momencie moduł rozszerzenia zostanie zaktualizowany na dysku, Visual Studio ponownie zanalizuje moduł w tle. Ta akcja nie ma wpływu na zachowanie w czasie działania, ale niektóre uzupełnienia nie są dostępne, dopóki analiza nie zostanie ukończona.

Może być również konieczne dodanie ścieżki [wyszukiwania](search-paths.md) do folderu zawierającego moduł .

### <a name="net-projects"></a>Projekty .NET

Podczas pracy z oprogramowaniem IronPython można dodawać odwołania do zestawów .NET, aby włączyć funkcję IntelliSense. W przypadku projektów .NET w rozwiązaniu kliknij prawym przyciskiem myszy węzeł Odwołania w projekcie języka Python, wybierz polecenie Dodaj **odwołanie,** wybierz **kartę Projekty** i przejdź do żądanego projektu.  W przypadku bibliotek DLL pobranych oddzielnie wybierz **kartę** Przeglądaj, a następnie przejdź do odpowiedniej biblioteki DLL.

Ponieważ odwołania w ironpython nie są dostępne, dopóki nie zostanie wykonane wywołanie , należy również dodać odpowiednie wywołanie do zestawu, zwykle na `clr.AddReference('<AssemblyName>')` `clr.AddReference` początku kodu. Na przykład kod utworzony przez szablon projektu **Aplikacji Windows Forms IronPython** w programie Visual Studio zawiera dwa wywołania na początku pliku:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Projekty WebPI

Możesz dodać odwołania do wpisów produktu WebPI na Microsoft Azure Cloud Services, w których można zainstalować dodatkowe składniki za pośrednictwem kanału informacyjnego webpi. Domyślnie wyświetlane źródło danych jest specyficzne dla języka Python i obejmuje django, CPython i inne podstawowe składniki. Możesz również wybrać własne źródło danych, jak pokazano poniżej. Podczas publikowania Microsoft Azure, zadanie instalacji instaluje wszystkie przywołyne produkty.

> [!IMPORTANT]
> Projekty WebPI nie są dostępne w programie Visual Studio 2017 lub Visual Studio 2019.

![Odwołania interfejsu WebPI](media/projects-webPI-components.png)
