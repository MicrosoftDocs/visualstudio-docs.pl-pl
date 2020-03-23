---
title: Wskazówki dotyczące poprawy wydajności
ms.date: 08/14/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3cd7fe9781048f6612ff6bd81c0bf0cbc00a30b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303023"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Porady i wskazówki dotyczące wydajności programu Visual Studio

Zalecenia dotyczące wydajności programu Visual Studio są przeznaczone do sytuacji braku pamięci, które mogą wystąpić w rzadkich przypadkach. W takich sytuacjach można zoptymalizować niektóre funkcje programu Visual Studio, które mogą nie być używane. Poniższe wskazówki nie są przeznaczone jako zalecenia ogólne.

> [!NOTE]
> Jeśli masz problemy z korzystaniem z produktu z powodu problemów z pamięcią, poinformuj nas o tym za pośrednictwem [narzędzia opinii.](../ide/how-to-report-a-problem-with-visual-studio.md)

## <a name="use-a-64-bit-os"></a>Korzystanie z 64-bitowego systemu operacyjnego

W przypadku uaktualnienia systemu z 32-bitowej wersji systemu Windows do wersji 64-bitowej można rozszerzyć ilość pamięci wirtualnej dostępnej w programie Visual Studio z 2 GB do 4 GB. Dzięki temu visual studio do obsługi znacznie większe obciążenia, nawet jeśli jest to proces 32-bitowy.

Aby uzyskać więcej informacji, zobacz [Limity pamięci](/windows/desktop/Memory/memory-limits-for-windows-releases) i [Użyj /LARGEADDRESSAWARE w 64-bitowym systemie Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Wyłącz automatyczne przywracanie plików

Visual Studio automatycznie ponownie otwiera dokumenty, które pozostały otwarte w poprzedniej sesji. Może to wydłużyć czas ładowania rozwiązania o maksymalnie 30% lub więcej, w zależności od typu projektu i otwieranych dokumentów. Projektanci, tacy jak Windows Forms i XAML, a także niektóre pliki JavaScript i typescript, mogą być powolne.

Visual Studio powiadamia użytkownika na żółtym pasku, gdy automatyczne przywracanie dokumentu powoduje, że rozwiązanie jest znacznie wolniejsze. Automatyczne ponowne otwieranie plików można wyłączyć, wykonując następujące czynności:

1. Wybierz**pozycję Opcje** **narzędzi,** > aby otworzyć okno dialogowe **Opcje.**

1. Na**stronie** Ogólne projekty **i rozwiązania** > usuń zaznaczenie opcji **Otwórz dokumenty przy obciążeniu rozwiązania**.

Jeśli wyłączysz automatyczne przywracanie plików, szybki sposób przechodzenia do plików, które chcesz otworzyć, jest użycie jednego z poleceń [Przejdź do:](../ide/go-to.md)

- Aby uzyskać ogólną funkcję **Przejdź do,** wybierz **pozycję Edytuj** > **przejdź do** > **wszystkich**lub naciśnij klawisz **Ctrl**+**T**.

- Przechodzenie do ostatniej lokalizacji edycji w rozwiązaniu za pomocą **funkcji Edytuj** > **przejdź do** > **ostatniej lokalizacji edycji**lub naciskając **klawisze Ctrl**+**Shift**+**Backspace**.

- Użyj **funkcji Przejdź do ostatniego pliku,** aby wyświetlić listę ostatnio odwiedzonych plików w rozwiązaniu. Wybierz **pozycję Edytuj** > **przejdź do** > **ostatniego pliku**lub naciśnij **klawisze Ctrl**+**1**, **Ctrl**+**R**.

## <a name="configure-debugging-options"></a>Konfigurowanie opcji debugowania

Jeśli zazwyczaj brakuje pamięci podczas sesji debugowania, można zoptymalizować wydajność, wykonując jedną lub więcej zmian konfiguracji.

- **Włącz tylko mój kod**

    Najprostszą optymalizacją jest włączenie funkcji **Just My Code,** która ładuje tylko symbole dla projektu. Włączenie tej funkcji może spowodować znaczne zapisanie pamięci do debugowania zarządzanych aplikacji (.NET). Ta opcja jest już domyślnie włączona w niektórych typach projektów.

    Aby włączyć **opcję Tylko mój kod**, wybierz pozycję**Opcje** >  **narzędzi** > **Debugowania** > **ogólnego,** a następnie wybierz pozycję Włącz tylko mój **kod**.

- **Określanie symboli do załadowania**

    W przypadku debugowania natywnego ładowanie plików symboli (*pdb*) jest kosztowne pod względem zasobów pamięci. Ustawienia symbolu debugera można skonfigurować w celu oszczędzania pamięci. Zazwyczaj można skonfigurować rozwiązanie, aby załadować tylko moduły z projektu.

    Aby określić ładowanie symboli, wybierz pozycję**Opcje** >  **narzędzi** > **Debugowania** > **symboli**.

    Ustaw opcje **tylko określone moduły** zamiast **wszystkie moduły,** a następnie określ, które moduły chcesz załadować. Podczas debugowania można również kliknąć prawym przyciskiem myszy określone moduły w oknie **Moduły,** aby jawnie uwzględnić moduł w obciążeniu symbolu. (Aby otworzyć okno podczas debugowania, wybierz pozycję **Debugowanie** > **modułów****systemu Windows).** > 

    Aby uzyskać więcej informacji, zobacz [Rozumienie plików symboli](/visualstudio/ide/visual-studio-performance-tips-and-tricks?view=vs-2019).

- **Wyłączanie narzędzi diagnostycznych**

    Zaleca się wyłączenie profilowania procesora po użyciu. Ta funkcja może zużywać duże ilości zasobów. Po włączeniu profilowania procesora CPU ten stan jest utrwalony w kolejnych sesjach debugowania, więc warto jawnie wyłączyć go po zakończeniu. Można zaoszczędzić niektóre zasoby, wyłączając narzędzia diagnostyczne podczas debugowania, jeśli nie są potrzebne podane funkcje.

    Aby wyłączyć **narzędzia diagnostyczne**, rozpocznij sesję debugowania, wybierz pozycję**Opcje** >  **narzędzi** > **Włącz narzędzia diagnostyczne**i usuń zaznaczenie tej opcji.

    Aby uzyskać więcej informacji, zobacz [Narzędzia profilowania](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Wyłączanie narzędzi i rozszerzeń

Niektóre narzędzia lub rozszerzenia można wyłączyć, aby zwiększyć wydajność.

> [!TIP]
> Często można wyizolować problemy z wydajnością, wyłączając rozszerzenia po jednym na raz i ponownie sprawdzając wydajność.

### <a name="managed-language-service-roslyn"></a>Usługa języka zarządzanego (Roslyn)

Aby uzyskać informacje na temat zagadnień dotyczących wydajności platformy kompilatora platformy .NET ("Roslyn"), zobacz [Zagadnienia dotyczące wydajności dla dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Wyłącz pełną analizę rozwiązania**

    Visual Studio wykonuje analizę całego rozwiązania w celu zapewnienia bogate środowisko dotyczące błędów przed wywołaniem kompilacji. Ta funkcja jest przydatna do identyfikowania błędów tak szybko, jak to możliwe. Jednak w przypadku dużych rozwiązań ta funkcja może zużywać znaczne zasoby pamięci. Jeśli występują ciśnienia pamięci lub podobne problemy, można wyłączyć to środowisko, aby zwolnić te zasoby. Domyślnie ta opcja jest włączona dla języka Visual Basic i wyłączona dla języka C#.

    Aby wyłączyć **pełną analizę rozwiązania,** wybierz pozycję**Edytor tekstu****Opcje** >  **narzędzi,** > a następnie wybierz opcję **Visual Basic** lub **C#**. Wybierz pozycję **Zaawansowane** i usuń **zaznaczenie opcji Włącz pełną analizę rozwiązania**.

- **Wyłączanie funkcji CodeLens**

    Visual Studio wykonuje zadanie **Znajdź wszystkie odwołania** dla każdej metody, jak jest wyświetlany. CodeLens udostępnia funkcje, takie jak wbudowane wyświetlanie liczby odwołań. Praca jest wykonywana w oddzielnym procesie, takim jak *ServiceHub.RoslynCodeAnalysisService32*. W dużych rozwiązaniach lub w systemach o ograniczonych zasobach ta funkcja może mieć znaczący wpływ na wydajność. Jeśli występują problemy z pamięcią, na przykład podczas ładowania dużego rozwiązania na komputerze 4 GB lub wysokie użycie procesora CPU dla tego procesu, można wyłączyć CodeLens, aby zwolnić zasoby.

    Aby wyłączyć funkcję **CodeLens**, wybierz pozycję Opcje **narzędzi** > **Options** > **Edytor** > tekstu Wszystkie pliki**CodeLens****All Languages** > i usuń zaznaczenie tej funkcji.

    > [!NOTE]
    > Funkcja CodeLens jest dostępna w wersjach programu Visual Studio dla profesjonalistów i przedsiębiorstw.

### <a name="other-tools-and-extensions"></a>Inne narzędzia i rozszerzenia

- **Wyłącz rozszerzenia**

    Rozszerzenia są dodatkowe składniki oprogramowania dodane do programu Visual Studio, które zapewniają nowe funkcje lub rozszerzyć istniejące funkcje. Rozszerzenia często mogą być źródłem problemów z zasobami pamięci. Jeśli występują problemy z zasobami pamięci, spróbuj wyłączać rozszerzenia po jednym na raz, aby zobaczyć, jak wpływa na scenariusz lub przepływ pracy.

   ::: moniker range="vs-2017"

    Aby wyłączyć rozszerzenia, przejdź do **rozszerzenia i aktualizacje** **narzędzi** > i wyłącz określone rozszerzenie.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Aby wyłączyć rozszerzenia, przejdź do **rozszerzenia zarządzaj** > **rozszerzeniami**i wyłącz określone rozszerzenie.

   ::: moniker-end

- **Wyłączanie projektanta XAML**

    Projektant XAML jest domyślnie włączony, ale zużywa zasoby tylko po otwarciu pliku *xaml.* Jeśli pracujesz z plikami XAML, ale nie chcesz korzystać z funkcji projektanta, wyłącz tę funkcję, aby zwolnić trochę pamięci.

    Aby wyłączyć **Projektanta XAML,** przejdź do **pozycji** > **Opcje** > narzędzi**XAML Designer** > **Enable XAML Designer**i usuń zaznaczenie tej opcji.

- **Usuwanie obciążeń**

    Instalator programu Visual Studio służy do usuwania obciążeń, które nie są już używane. Ta akcja może usprawnić koszty uruchamiania i środowiska uruchomieniowego, pomijając pakiety i zestawy, które nie są już potrzebne.

## <a name="force-a-garbage-collection"></a>Wymuszanie wyrzucania elementów bezużytecznych

Clr używa systemu zarządzania pamięcią wyrzucania elementów bezużytecznych. W tym systemie czasami pamięć jest używana przez obiekty, które nie są już potrzebne. Ten stan jest tymczasowy; moduł zbierający elementy bezużyteczne wyda tę pamięć na podstawie jego heurystyki użycia wydajności i zasobów. Można wymusić CLR do zbierania nieużywanych pamięci przy użyciu skrótu klawiszowego w programie Visual Studio. Jeśli istnieje znaczna ilość śmieci oczekujących na odbiór i wymusić wyrzucanie elementów bezużytecznych, powinien zostać wyświetlony użycie pamięci *devenv.exe* spadek procesu w **Menedżerze zadań**. Rzadko jest to konieczne, aby użyć tej metody. Jednak po zakończeniu kosztownej operacji (na przykład pełnej kompilacji, sesji debugowania lub zdarzenia otwartego rozwiązania), może pomóc określić, ile pamięci jest naprawdę używane przez proces. Ponieważ visual studio jest mieszany (zarządzany & natywny), od czasu do czasu jest możliwe dla natywnego alokatora i modułu zbierającego elementy bezużyteczne konkurować o ograniczone zasoby pamięci. W warunkach wysokiego użycia pamięci może pomóc wymusić moduł zbierający elementy bezużyteczne do uruchomienia.

Aby wymusić wyrzucanie elementów bezużytecznych, użyj klawisza skrótu: **Ctrl**+**Alt**+**Shift**+**F12**, **Ctrl**+**Alt**+**Shift**+**F12** (naciśnij go dwukrotnie).

Jeśli wymuszanie wyrzucania elementów bezużytecznych niezawodnie sprawia, że scenariusz pracy, plik raportu za pośrednictwem narzędzia opinii programu Visual Studio, ponieważ to zachowanie może być błąd.

Aby uzyskać szczegółowy opis modułu zbierającego elementy bezużyteczne CLR, zobacz [Podstawy wyrzucania elementów bezużytecznych](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Zobacz też

- [Optymalizowanie wydajności programu Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Szybsze ładowanie rozwiązań (blog programu Visual Studio)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
