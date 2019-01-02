---
title: Porady dotyczące poprawy wydajności
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdc20f22fc535028cb67939fed9c9472ed081428
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956897"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Porady dotyczące wydajności programu Visual Studio i wskazówki

Zalecenia dotyczące wydajności programu Visual Studio są przeznaczone dla sytuacje małej ilości pamięci, które mogą wystąpić w rzadkich przypadkach. W takich przypadkach można zoptymalizować niektóre funkcje programu Visual Studio, których nie używasz. Poniższe porady nie odnoszą się jako ogólne zalecenia.

> [!NOTE]
> Jeśli występują problemy z używaniem produktu z powodu problemów z pamięcią, Daj nam znać za pośrednictwem [narzędzia opinii](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="use-a-64-bit-os"></a>Użyj 64-bitowego systemu operacyjnego

Po uaktualnieniu do wersji 64-bitowego systemu z 32-bitowej wersji systemu Windows możesz rozwinąć ilość dostępnej pamięci wirtualnej w programie Visual Studio, od 2 do 4 GB. Dzięki temu Visual Studio, aby obsłużyć znacznie większych obciążeń, mimo że jest proces 32-bitowy.

Aby uzyskać więcej informacji, zobacz [limity pamięci](/windows/desktop/Memory/memory-limits-for-windows-releases#memory_limits) i [/largeaddressaware w systemie Windows 64-bitowych](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Wyłącz automatyczne plików przywracania

Program Visual Studio ponownie automatycznie otwiera dokumenty, które zostały pozostawione otwarte w poprzedniej sesji. To może przedłużyć czas przypadków, gdy ładowania rozwiązania przez maksymalnie 30% lub dłużej w zależności od typu projektu i dokumenty, jest otwarty. Projektanci, takie jak Windows Forms i XAML i niektórych plików JavaScript i typescript można otwierać się powoli.

Visual Studio powiadamia kolorem żółtym paskiem podczas przywracania automatycznych dokumentu powoduje rozwiązanie znacznie wolniejsze ładowanie. Aby wyłączyć automatyczne plików otworzyć ponownie, wykonując następujące czynności:

1. Wybierz **narzędzia** > **opcje** otworzyć **opcje** okno dialogowe.

1. Na **projekty i rozwiązania** > **ogólne** strony, usuń zaznaczenie **ponownie otworzyć dokumentów przy ładowaniu rozwiązania**.

Jeśli wyłączysz plik automatycznego przywracania, Szybkie nawigowanie do plików, który chcesz otworzyć jest przy użyciu jednej z [przejdź do](../ide/go-to.md) poleceń:

- Do ogólnych **przejdź do** funkcji, wybierz opcję **Edytuj** > **przejdź do** > **przejdź do wszystkich**, lub naciśnij  **CTRL**+**T**.

- W programie Visual Studio 2017 w wersji należy zachować 15,8 i nowszych możesz przejść do ostatniej edycji lokalizacji w rozwiązaniu za pomocą **Edytuj** > **przejdź do** > **przejdź do ostatniego edytowanie lokalizacji**, lub naciskając **Ctrl**+**Shift**+**Backspace**.

- W programie Visual Studio 2017 w wersji należy zachować 15,8 i nowszych **przejdź do pliku ostatnie** umożliwia wyświetlenie listy ostatnio odwiedzonych plików w rozwiązaniu. Wybierz **Edytuj** > **przejdź do** > **przejdź do pliku ostatnie**, lub naciśnij **Ctrl** + **1**, **Ctrl**+**R**.

## <a name="configure-debugging-options"></a>Skonfiguruj opcje debugowania

Jeśli masz zazwyczaj mało pamięci podczas sesji debugowania, można zoptymalizować wydajność, wprowadzając zmiany w konfiguracji co najmniej jeden.

- **Włącz opcję tylko mój kod**

    Najprostsza optymalizacji jest umożliwienie **tylko mój kod** funkcji, która tylko ładuje symbole dla Twojego projektu. Włączenie tej funkcji może spowodować znaczne pamięci, zapisywanie do debugowania zarządzanej aplikacji (.NET). Ta opcja jest już włączona domyślnie w niektórych typach projektów.

    Aby włączyć **tylko mój kod**, wybierz **narzędzia** > **opcje** > **debugowanie**  >   **Ogólne**, a następnie wybierz pozycję **Włącz tylko mój kod**.

- **Określa symbole, aby załadować**

    Debugowanie natywne ładowania plików symboli (*.pdb*) jest kosztowna pod względem zasobów pamięci. Można skonfigurować ustawienia symboli debugera w celu zachowywania pamięci. Zazwyczaj należy skonfigurować rozwiązanie, aby załadować tylko moduły z projektu.

    Aby określić ładowania symboli, wybierz **narzędzia** > **opcje** > **debugowanie** > **symbole**.

    Ustawić opcje **tylko określonych modułów** zamiast **wszystkie moduły** , a następnie określ, które moduły care do załadowania. Podczas debugowania, można również prawym przyciskiem myszy w określonych modułach **modułów** okna, aby jawnie objęte moduł ładowania symboli. (Aby otworzyć okno podczas debugowania, wybierz opcję **debugowania** > **Windows** > **modułów**.)

    Aby uzyskać więcej informacji, zobacz [zrozumieć pliki symboli](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).

- **Wyłącz narzędzia diagnostyczne**

    Zalecane jest, wyłącz profilowanie procesora CPU po użyciu. Ta funkcja może zużywać dużą ilością zasobów. Po włączeniu profilowania procesora CPU ten stan są utrwalane między sesjami debugowania kolejne, więc warto jawnie wyłączając ją po zakończeniu. Niektóre zasoby mogą zapisać, wyłączając narzędzia diagnostyczne podczas debugowania, jeśli nie potrzebujesz funkcji podana.

    Aby wyłączyć **narzędzia diagnostyczne**uruchamianie sesji debugowania, wybierz **narzędzia** > **opcje** > **Włączanie diagnostyki Narzędzia**i usuń zaznaczenie opcji.

    Aby uzyskać więcej informacji, zobacz [Profiling Tools](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Wyłączanie narzędzi i rozszerzeń

Poprawianie wydajności można wyłączyć niektóre narzędzia lub rozszerzenia.

> [!TIP]
> Wyłączanie rozszerzenia jednego naraz, a następnie ponowne sprawdzanie wydajności, można często wyizolować problemy z wydajnością.

### <a name="managed-language-service-roslyn"></a>Zarządzana usługa językowa (Roslyn)

Aby uzyskać informacje dotyczące wydajności platformy kompilatora .NET ("Roslyn"), zobacz [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Wyłączanie pełnej analizy rozwiązania**

    Aby zapewnić rozbudowane środowisko o błędach przed wywołaniem kompilacji programu Visual Studio wykonuje analizy całego rozwiązania. Ta funkcja jest przydatna na identyfikację błędów tak szybko, jak to możliwe. Jednak w przypadku dużych rozwiązań tej funkcji mogą wykorzystywać zasoby pamięci znaczące. W przypadku dużego wykorzystania pamięci lub podobne problemy, możesz wyłączyć to środowisko, aby zwolnić zasoby. Domyślnie ta opcja jest włączona dla języka Visual Basic i wyłączone dla języka C#.

    Aby wyłączyć **pełnej analizy rozwiązania**, wybierz **narzędzia** > **opcje** > **edytora tekstów**, a następnie wybierz pozycję albo **języka Visual Basic** lub **C#**. Wybierz **zaawansowane** i usuń zaznaczenie opcji **Włączanie pełnej analizy rozwiązania**.

- **Wyłączanie funkcji CodeLens**

    Wykonuje program Visual Studio **Znajdź wszystkie odwołania** zadań dla każdej metody, która jest wyświetlana. Funkcja CodeLens dostarcza funkcje takie jak śródwierszowe wyświetlanie liczby odwołań. Praca jest wykonywana w oddzielnym procesie, takie jak *ServiceHub.RoslynCodeAnalysisService32*. W przypadku dużych rozwiązań lub w systemach ograniczonych zasobach ta funkcja może mieć znaczący wpływ na wydajność. Jeśli występują problemy z pamięcią, na przykład podczas ładowania dużych rozwiązania na komputerze 4 GB, lub wysokie użycie procesora CPU dla tego procesu możesz wyłączyć funkcji CodeLens, aby zwolnić zasoby.

    Aby wyłączyć **CodeLens**, wybierz **narzędzia** > **opcje** > **edytora tekstów**  >   **Wszystkie języki** > **CodeLens**i usuń zaznaczenie opcji tej funkcji.

    > [!NOTE]
    > Funkcja CodeLens jest dostępna w wersjach Professional i Enterprise programu Visual Studio.

### <a name="other-tools-and-extensions"></a>Inne narzędzia i rozszerzenia

- **Wyłącz rozszerzenia**

    Rozszerzenia są dodatkowych składników oprogramowania dodane do programu Visual Studio, które zapewniają nowe funkcje lub rozszerzanie istniejących funkcji. Rozszerzenia można źródłem problemów zasobów pamięci. Jeśli występują problemy z zasobami pamięci, spróbuj wyłączyć rozszerzenia jeden w czasie, aby zobaczyć, jak wpływa na scenariuszu lub przepływu pracy.

    Aby wyłączyć rozszerzenia, przejdź do **narzędzia** > **rozszerzenia i aktualizacje**i Wyłącz określonego rozszerzenia.

- **Wyłącz projektanta XAML**

    Projektant XAML jest domyślnie włączona, ale tylko wykorzystuje zasoby, jeśli otworzysz *.xaml* pliku. Praca z plikami XAML, ale nie chcesz, aby korzystać z funkcji projektanta, należy wyłączyć tę funkcję, aby zwolnić z pamięci.

    Aby wyłączyć **projektanta XAML**, przejdź do **narzędzia** > **opcje** > **projektanta XAML**  >  **Włącz projektanta XAML**i usuń zaznaczenie opcji.

- **Usuń obciążeń**

    Aby usunąć obciążeń, które nie są już używane, można użyć Instalatora programu Visual Studio. Ta akcja, można ograniczyć koszty uruchamiania i wykonywania przez pominięcie pakiety i zestawy, które nie są już potrzebne.

## <a name="force-a-garbage-collection"></a>Wymuszenia wyrzucania elementów bezużytecznych

Środowisko CLR używa systemu zarządzania pamięcią wyrzucania elementów kolekcji. W tym systemie czasami pamięć jest używana przez obiekty, które nie są już potrzebne. Ten stan jest tymczasowa. Moduł zbierający elementy bezużyteczne spowoduje zwolnienie tej pamięci na podstawie jego wydajności i algorytmy heurystyczne użycia zasobów. Można wymusić CLR, aby zbierać wszystkie nieużywane pamięci przy użyciu klawisz dostępu w programie Visual Studio. W przypadku znacznej ilości pamięci oczekiwanie na kolekcji wymuszenia wyrzucania elementów bezużytecznych, powinien zostać wyświetlony użycie pamięci przez *devenv.exe* procesu upuść w **Menedżera zadań**. Jest to rzadko niezbędne do używania tej metody. Jednak po ukończeniu kosztowną operacją (na przykład Pełna kompilacja, sesji debugowania lub zdarzenia otwarte rozwiązanie) może pomóc określić, ile pamięci naprawdę jest on używany przez proces. Ponieważ Visual Studio jest mieszany (zarządzany i natywnego), użytkownik może od czasu do czasu natywnego programu przydzielania i moduł zbierający elementy bezużyteczne konkurują o zasoby pamięci ograniczone. W warunkach wysokiego użycia pamięci może pomóc wymusić moduł odśmiecania pamięci do uruchomienia.

Aby wymusić wyrzucania elementów bezużytecznych, użyj klawisza skrótu: **CTRL**+**Alt**+**Shift**+**F12**, **Ctrl** + **Alt**+**Shift**+**F12** (naciśnij do dwa razy).

Jeśli niezawodnie wymuszenia wyrzucania elementów bezużytecznych sprawia, że dany scenariusz działał, plik raportu za pomocą narzędzia opinii programu Visual Studio to zachowanie może być usterka.

Aby uzyskać szczegółowy opis moduł odśmiecania pamięci CLR, zobacz [podstawowe informacje na temat wyrzucania elementów bezużytecznych](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności programu Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Ładowanie rozwiązania szybciej (blog Visual Studio)](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)