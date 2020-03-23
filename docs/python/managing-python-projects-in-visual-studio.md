---
title: Zarządzanie projektami aplikacji języka Python
description: Projekty w programie Visual Studio zarządzają zależnościami między plikami i złożonością relacji w aplikacji.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302813"
---
# <a name="python-projects-in-visual-studio"></a>Projekty języka Python w programie Visual Studio

Aplikacje Języka Python są zazwyczaj definiowane przy użyciu tylko folderów i plików, ale ta struktura może stać się złożona, ponieważ aplikacje stają się większe i być może obejmują automatycznie generowane pliki, JavaScript dla aplikacji internetowych i tak dalej. Projekt programu Visual Studio pomaga zarządzać tą złożonością. Projekt (plik *pyproj)* identyfikuje wszystkie pliki źródłowe i zawartości skojarzone z projektem, zawiera informacje o kompilacji dla każdego pliku, przechowuje informacje do integracji z systemami kontroli źródła i pomaga zorganizować aplikację w składniki logiczne.

![Projekt Języka Python w Eksploratorze rozwiązań](media/projects-solution-explorer.png)

Ponadto projekty są zawsze zarządzane w ramach *rozwiązania*programu Visual Studio , które mogą zawierać dowolną liczbę projektów, które mogą odwoływać się do siebie nawzajem. Na przykład projekt języka Python może odwoływać się do projektu C++, który implementuje moduł rozszerzenia. Dzięki tej relacji visual studio automatycznie tworzy projekt C++ (jeśli to konieczne) po uruchomieniu debugowania projektu Języka Python. (Aby uzyskać ogólną dyskusję, zobacz [Rozwiązania i projekty w programie Visual Studio.](../ide/solutions-and-projects-in-visual-studio.md)

Visual Studio udostępnia wiele szablonów projektu języka Python, aby szybko skonfigurować szereg struktur aplikacji, w tym szablon do tworzenia projektu z istniejącego drzewa folderów i szablon, aby utworzyć czysty, pusty projekt. Zobacz [Szablony projektu](#project-templates) dla indeksu.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 obsługuje otwieranie folderu zawierającego kod języka Python i uruchamianie tego kodu bez tworzenia plików projektu i rozwiązania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Szybki start: Otwieranie i uruchamianie kodu języka Python w folderze](quickstart-05-python-visual-studio-open-folder.md). Istnieją jednak korzyści z używania pliku projektu, jak wyjaśniono w tej sekcji.
::: moniker-end

> [!Tip]
> Bez projektu wszystkie wersje programu Visual Studio działają dobrze z kodem języka Python. Na przykład można otworzyć plik Języka Python samodzielnie i cieszyć się autouzupełnianiem, IntelliSense i debugowaniem (klikając prawym przyciskiem myszy w edytorze i wybierając **polecenie Start with Debugging**). Ponieważ taki kod zawsze używa domyślnego środowiska globalnego, jednak może być widoczne niepoprawne uzupełnienia lub błędy, jeśli kod jest przeznaczony dla innego środowiska. Ponadto program Visual Studio analizuje wszystkie pliki i pakiety w folderze, z którego jest otwierany pojedynczy plik, co może zużywać dużo czasu procesora CPU.
>
> Tworzenie projektu programu Visual Studio na podstawie istniejącego kodu jest prostą sprawą, zgodnie z opisem w [polu Utwórz projekt z istniejących plików.](#create-project-from-existing-files)

|   |   |
|---|---|
| ![ikona kamery filmowa dla wideo](../install/media/video-icon.png "Obejrzyj film") | [Deep Dive: Użyj kontroli źródła w projektach Pythona](https://youtu.be/Aq8eqApnugM) (youtube.com, 8m 55s). |

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Dodawanie plików, przypisywanie pliku startowego i ustawianie środowisk

Podczas tworzenia aplikacji zazwyczaj należy dodać nowe pliki różnych typów do projektu. Dodawanie takich plików odbywa się przez kliknięcie prawym przyciskiem myszy projektu i wybranie opcji **Dodaj** > **istniejący element,** za pomocą którego można przeglądać plik w celu dodania, lub **dodaj** > **nowy element,** które powoduje wyświetlenie okna dialogowego z różnymi szablonami elementów. Zgodnie z opisem w odwołaj się do [szablonów elementów](python-item-templates.md) opcje obejmują puste pliki Języka Python, klasę Języka Python, test jednostkowy i różne pliki związane z aplikacjami internetowymi. Można eksplorować te opcje za pomocą projektu testowego, aby dowiedzieć się, co jest dostępne w wersji programu Visual Studio.

Każdy projekt języka Python ma jeden przypisany plik startowy, pokazany pogrubioną czcionką w **Eksploratorze rozwiązań.** Plik startowy jest plikiem uruchamianym po uruchomieniu debugowania **(F5** lub **Debug** > **Start Debugging**) lub po uruchomieniu projektu w oknie **Interaktywnym** **(Shift**+**Alt**+**F5** lub **Debug** > Execute Project w języku Python**Interactive**). Aby go zmienić, kliknij prawym przyciskiem myszy nowy plik i wybierz polecenie **Ustaw jako element startowy** (lub **Ustaw jako plik startowy** w starszych wersjach programu Visual Studio).

> [!Tip]
> Jeśli usuniesz wybrany plik startowy z projektu i nie wybierzesz nowego, program Visual Studio nie wie, z jakim plikiem języka Python należy rozpocząć podczas próby uruchomienia projektu. W takim przypadku visual studio 2017 w wersji 15.6 i nowszych pokazuje błąd; starsze wersje albo otworzyć okno wyjściowe z uruchomionym interpreterem Języka Python lub pojawi się okno wyjściowe, ale następnie znikają niemal natychmiast. Jeśli napotkasz którekolwiek z tych zachowań, sprawdź, czy masz przypisany plik startowy.
>
> Jeśli chcesz zachować otwarte okno danych wyjściowych z jakiegokolwiek powodu, kliknij prawym przyciskiem myszy `-i` projekt, wybierz polecenie **Właściwości**, wybierz kartę **Debugowanie,** a następnie dodaj do pola Argumenty **interpretera.** Ten argument powoduje, że interpreter przejść do trybu interaktywnego po zakończeniu programu, dzięki tym samym utrzymanie okna otwarte, dopóki nie zostanie wprowadzony **Ctrl**+**Z** > **Enter,** aby zakończyć.

::: moniker range="vs-2017"
Nowy projekt jest zawsze skojarzony z domyślnym globalnym środowiskiem Pythona. Aby skojarzyć projekt z innym środowiskiem (w tym środowiskami wirtualnymi), kliknij prawym przyciskiem myszy węzeł **Środowiska języka Python** w projekcie, wybierz pozycję **Dodaj/Usuń środowiska Języka Python**i wybierz odpowiednie środowiska.
::: moniker-end
::: moniker range=">=vs-2019"
Nowy projekt jest zawsze skojarzony z domyślnym globalnym środowiskiem Pythona. Aby skojarzyć projekt z innym środowiskiem (w tym środowiskami wirtualnymi), kliknij prawym przyciskiem myszy węzeł **Środowiska języka Python** w projekcie, wybierz pozycję Dodaj **środowisko..** i wybierz odpowiednie środowisko. Można również użyć formantu rozwijanej środowiska na pasku narzędzi, aby wybrać i środowiska lub dodać inny do projektu.

![Polecenie Dodaj środowisko na pasku narzędzi Pythona](media/environments/environments-toolbar-2019.png)
::: moniker-end

Aby zmienić aktywne środowisko, kliknij prawym przyciskiem myszy żądane środowisko w **Eksploratorze rozwiązań** i wybierz **pozycję Aktywuj środowisko,** jak pokazano poniżej. Aby uzyskać więcej informacji, zobacz [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

![Aktywowanie środowiska dla projektu języka Python](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Szablony projektów

Visual Studio oferuje wiele sposobów, aby skonfigurować projekt języka Python, od podstaw lub z istniejącego kodu. Aby użyć szablonu, zaznacz polecenie menu **Plik** > **nowy** > **projekt** lub kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**, z których oba są wyświetlane poniżej w oknie dialogowym Nowy **projekt.** Aby wyświetlić szablony specyficzne dla języka Python, wyszukaj w "Pythonie" lub wybierz węzeł **Zainstalowany** > **Język Python:**

![Nowe okno dialogowe projektu z szablonami języka Python](media/projects-new-project-dialog.png)

W poniższej tabeli podsumowano szablony dostępne w programie Visual Studio 2017 i nowszych wersjach (nie wszystkie szablony są dostępne we wszystkich poprzednich wersjach):

| Szablon | Opis |
| --- | --- |
| [**Z istniejącego kodu Pythona**](#create-project-from-existing-files) | Tworzy projekt programu Visual Studio z istniejącego kodu języka Python w strukturze folderów.  |
| **Aplikacja Python** | Podstawowa struktura projektu dla nowej aplikacji Języka Python z pojedynczym, pustym plikiem źródłowym. Domyślnie projekt jest uruchamiany w interpreterze konsoli domyślnego środowiska globalnego, które można zmienić, [przypisując inne środowisko](selecting-a-python-environment-for-a-project.md). |
| [**Usługa w chmurze platformy Azure**](python-azure-cloud-service-project-template.md) | Projekt usługi w chmurze platformy Azure napisany w języku Python. |
| [**Projekty internetowe**](python-web-application-project-templates.md) | Projekty dla aplikacji internetowych opartych na różnych strukturach, w tym Bottle, Django i Flask. |
| **IronPython Aplikacja** | Podobnie jak szablon aplikacji języka Python, ale domyślnie używa IronPython, włączając debugowanie .NET interop i mixed-mode za pomocą języków .NET. |
| **IronPython WPF Aplikacja** | Struktura projektu przy użyciu IronPython z windows presentation foundation plików XAML dla interfejsu użytkownika aplikacji. Visual Studio udostępnia projektanta interfejsu użytkownika XAML, posuwa się kodem może być napisany w języku Python, a aplikacja jest uruchamiana bez wyświetlania konsoli. |
| **Strona sieci Web IronPython Silverlight** | Projekt IronPython, który działa w przeglądarce przy użyciu programu Silverlight. Kod Pythona aplikacji znajduje się na stronie internetowej jako skrypt. Tag skryptu kotłowej ściąga w dół kod JavaScript, który inicjuje IronPython działa wewnątrz Silverlight, z którego kod Pythona może wchodzić w interakcje z DOM. |
| **IronPython Windows Formularze Aplikacji** | Struktura projektu przy użyciu IronPython z interfejsem użytkownika utworzony przy użyciu kodu z formularzy systemu Windows. Aplikacja działa bez wyświetlania konsoli. |
| **Aplikacja w tle (IoT)** | Obsługuje wdrażanie projektów języka Python do uruchamiania jako usługi w tle na urządzeniach. Więcej informacji można znaleźć w [Centrum deweloperów IoT systemu Windows.](https://dev.windows.com/en-us/iot) |
| **Moduł rozszerzenia Języka Python** | Ten szablon pojawia się w obszarze Visual C++, jeśli zainstalowano **narzędzia do tworzenia natywnych języka Python** z obciążeniem języka Python w programie Visual Studio 2017 lub nowszym (zobacz [Instalacja).](installing-python-support-in-visual-studio.md) Zapewnia podstawową strukturę biblioteki DLL rozszerzenia Języka C++, podobną do opisanej w [temacie Utwórz rozszerzenie C++ dla języka Python.](working-with-c-cpp-python-in-visual-studio.md) |

> [!Note]
> Ponieważ Python jest językiem interpretowanym, projekty języka Python w programie Visual Studio nie generują autonomicznego pliku wykonywalnego, takiego jak inne skompilowane projekty językowe (na przykład C#). Aby uzyskać więcej informacji, zobacz [pytania i odpowiedzi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Tworzenie projektu na podstawie istniejących plików

> [!Important]
> Proces opisany w tym miejscu nie przenosi ani nie kopiuje oryginalnych plików źródłowych. Jeśli chcesz pracować z kopią, najpierw zduplikuj folder.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Połączone pliki

Połączone pliki to pliki, które są wprowadzane do projektu, ale zazwyczaj znajdują się poza folderami projektu aplikacji. Pojawiają się one w **Eksploratorze rozwiązań** ![jako zwykłe pliki z nałożone ikoną skrótu: Ikona połączonego pliku](media/projects-linked-file-icon.png)

Połączone pliki są określone w pliku *pyproj* przy użyciu `<Compile Include="...">` elementu. Połączone pliki są niejawne, jeśli używają ścieżki względnej poza strukturą katalogów lub jawne, jeśli używają ścieżek w **Eksploratorze rozwiązań:**

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Połączone pliki są ignorowane w następujących warunkach:

- Połączony plik zawiera metadane łącza i ścieżkę określoną w programie Dołącz atrybut lives w katalogu projektu
- Połączony plik powiela plik, który istnieje w hierarchii projektu
- Połączony plik zawiera metadane łącza, a ścieżka łącza jest ścieżką względną poza hierarchią projektu
- Ścieżka łącza jest zakorzeniona

### <a name="work-with-linked-files"></a>Praca z połączonymi plikami

Aby dodać istniejący element jako łącze, kliknij prawym przyciskiem myszy folder w projekcie, w którym chcesz dodać plik, a następnie wybierz pozycję **Dodaj** > **istniejący element**. W wyświetlonym oknie dialogowym wybierz plik i wybierz pozycję **Dodaj jako łącze** z listy rozwijanej przycisku **Dodaj.** Pod warunkiem, że nie ma żadnych plików powodujących konflikt, to polecenie tworzy łącze w wybranym folderze. Jednak łącze nie jest dodawane, jeśli istnieje już plik o tej samej nazwie lub łącze do tego pliku już istnieje w projekcie.

Jeśli spróbujesz połączyć się z plikiem, który już istnieje w folderach projektu, zostanie on dodany jako zwykły plik, a nie jako łącze. Aby przekonwertować plik na łącze, wybierz **opcję Zapisz plik,** > **Save As** aby zapisać plik w lokalizacji poza hierarchią projektu; Visual Studio automatycznie konwertuje go na łącze. Podobnie łącze można przekonwertować z powrotem za pomocą funkcji Zapisz **plik** > **jako,** aby zapisać plik gdzieś w hierarchii projektu.

Jeśli przeniesiesz połączony plik w **Eksploratorze rozwiązań,** łącze zostanie przeniesione, ale rzeczywisty plik nie zostanie naruszony. Podobnie usunięcie łącza powoduje usunięcie łącza bez wpływu na plik.

Nie można zmienić nazwy połączonych plików.

## <a name="references"></a>Dokumentacja

Projekty programu Visual Studio obsługują dodawanie odwołań do projektów i rozszerzeń, które pojawiają się w węźle **Odwołania** w **Eksploratorze rozwiązań:**

![Odwołania do rozszerzeń w projektach języka Python](media/projects-extension-references.png)

Odwołania do rozszerzenia zazwyczaj wskazują zależności między projektami i są używane do zapewnienia IntelliSense w czasie projektowania lub łączenia w czasie kompilacji. Projekty Pythona używają odniesień w podobny sposób, ale ze względu na dynamiczny charakter Pythona są one używane głównie w czasie projektowania, aby zapewnić ulepszone IntelliSense. Mogą być również używane do wdrażania na platformie Microsoft Azure w celu zainstalowania dodatkowych zależności.

### <a name="extension-modules"></a>Moduły rozszerzeń

Odwołanie do pliku *pyd* umożliwia intellisense dla wygenerowanego modułu. Visual Studio ładuje plik *pyd* do interpretera języka Python i introspekcji jego typów i funkcji. Próbuje również przeanalizować ciągi doc dla funkcji, aby zapewnić pomoc podpisu.

Jeśli w dowolnym momencie moduł rozszerzenia jest aktualizowany na dysku, Visual Studio ponownieanalizuje moduł w tle. Ta akcja nie ma wpływu na zachowanie w czasie wykonywania, ale niektóre uzupełnienia nie są dostępne, dopóki analiza nie zostanie zakończona.

Może być również konieczne dodanie [ścieżki wyszukiwania](search-paths.md) do folderu zawierającego moduł.

### <a name="net-projects"></a>Projekty platformy .NET

Podczas pracy z IronPython, można dodać odwołania do zestawów .NET, aby włączyć IntelliSense. W przypadku projektów platformy .NET w rozwiązaniu kliknij prawym przyciskiem myszy węzeł **Odwołania** w projekcie języka Python, wybierz pozycję **Dodaj odwołanie**, wybierz kartę **Projekty** i przejdź do żądanego projektu. W przypadku bibliotek DLL pobranych oddzielnie wybierz kartę **Przeglądaj** i przejdź do żądanej biblioteki DLL.

Ponieważ odwołania w IronPython nie są `clr.AddReference('<AssemblyName>')` dostępne, dopóki nie zostanie wykonane `clr.AddReference` wywołanie, należy również dodać odpowiednie wywołanie do zestawu, zazwyczaj na początku kodu. Na przykład kod utworzony przez szablon projektu **aplikacji formularzy systemu Windows IronPython** w programie Visual Studio zawiera dwa wywołania u góry pliku:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Projekty WebPI

Można dodać odwołania do wpisów produktów WebPI do wdrożenia do usług Microsoft Azure Cloud Services, gdzie można zainstalować dodatkowe składniki za pośrednictwem kanału informacyjnego WebPI. Domyślnie wyświetlany plik danych jest specyficzny dla języka Python i zawiera Django, CPython i inne podstawowe składniki. Możesz również wybrać własny kanał, jak pokazano poniżej. Podczas publikowania na platformie Microsoft Azure zadanie instalacji instaluje wszystkie produkty, do których istnieje odwołanie.

> [!IMPORTANT]
> Projekty webpi nie są dostępne w programie Visual Studio 2017 ani w programie Visual Studio 2019.

![Odwołania do interfejsu WebPI](media/projects-webPI-components.png)
