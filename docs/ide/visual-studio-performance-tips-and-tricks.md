---
title: Porady dotyczące poprawy wydajności
description: Dowiedz się, jak zoptymalizować pewne funkcje programu Visual Studio, które mogą nie być używane, aby zwiększyć wydajność.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e2187426fbd2e8892d41672c1cf682ed0b93592
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683772"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Porady i wskazówki dotyczące wydajności programu Visual Studio

Zalecenia dotyczące wydajności programu Visual Studio są przeznaczone dla małych ilości pamięci, które mogą wystąpić w rzadkich przypadkach. W takich sytuacjach można zoptymalizować niektóre funkcje programu Visual Studio, które mogą nie być używane. Poniższe wskazówki nie są przeznaczone do ogólnych zaleceń.

> [!NOTE]
> Jeśli masz trudności z użyciem produktu ze względu na problemy z pamięcią, poinformuj nas o tym za pośrednictwem [Narzędzia do przesyłania opinii](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="use-a-64-bit-os"></a>Korzystanie z 64-bitowego systemu operacyjnego

Jeśli uaktualniasz system z 32-bitowej wersji systemu Windows do wersji 64-bitowej, rozszerzasz ilość pamięci wirtualnej dostępnej dla programu Visual Studio z 2 GB do 4 GB. Dzięki temu program Visual Studio może obsługiwać znacznie większe obciążenia, nawet jeśli jest to proces 32-bitowy.

Aby uzyskać więcej informacji, zobacz [limity pamięci](/windows/desktop/Memory/memory-limits-for-windows-releases) i [używanie/LARGEADDRESSAWARE w 64-bitowym systemie Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Wyłącz automatyczne przywracanie plików

Program Visual Studio automatycznie ponownie otwiera dokumenty, które zostały pozostawione otwarte w poprzedniej sesji. Może to wydłużyć czas ładowania rozwiązania o maksymalnie 30%, w zależności od typu projektu i otwartych dokumentów. Projektanci, takie jak Windows Forms i XAML, a także niektóre pliki JavaScript i TypeScript, mogą być wolne do otwarcia.

Program Visual Studio powiadamia Cię na żółtym pasku, gdy automatyczne przywracanie dokumentów powoduje znacznie wolniejsze ładowanie rozwiązania. Automatyczne ponowne otwieranie plików można wyłączyć, wykonując następujące czynności:

1. Wybierz pozycję **Narzędzia**  >  **Opcje** , aby otworzyć okno dialogowe **Opcje** .

1. Na stronie **Ogólne projekty i rozwiązanie**  >   Usuń zaznaczenie opcji **Otwórz ponownie dokumenty po załadowaniu rozwiązania**.

Jeśli wyłączysz automatyczne przywracanie plików, możesz szybko przejść do plików, które chcesz otworzyć, za pomocą jednego z poleceń [Przejdź do](../ide/go-to.md) :

- **Aby uzyskać ogólne funkcje** , wybierz pozycję **Edytuj**  >  **Przejdź do** pozycji  >  **Przejdź do wszystkiego** lub naciśnij klawisz **Ctrl** + **T**.

- Przejdź do ostatnio edytowanej lokalizacji w rozwiązaniu za pomocą polecenia **Edytuj**  >  **Przejdź do**  >  **lokalizacji ostatniej edycji** lub naciskając klawisz **Ctrl** + **SHIFT** + **Backspace**.

- Użyj **Przejdź do ostatniego pliku** , aby wyświetlić listę ostatnio odwiedzonych plików w rozwiązaniu. Wybierz pozycję **Edytuj**  >  **Przejdź do** pozycji  >  **Przejdź do ostatniego pliku** lub naciśnij **klawisze CTRL** + **1**, **Ctrl** + **R**.

## <a name="configure-debugging-options"></a>Konfigurowanie opcji debugowania

Jeśli zwykle zaczyna brakować wolnej pamięci podczas debugowania sesji, można zoptymalizować wydajność, wprowadzając co najmniej jedną zmianę konfiguracji.

- **Włącz Tylko mój kod**

    Najprostsza Optymalizacja polega na włączeniu funkcji **tylko mój kod** , która ładuje tylko symbole dla projektu. Włączenie tej funkcji może spowodować znaczny zapis pamięci na potrzeby debugowania aplikacji zarządzanych (.NET). Ta opcja jest już włączona domyślnie w niektórych typach projektów.

    Aby włączyć **tylko mój kod**, wybierz   >  **Opcje** narzędzia  >  **debugowanie**  >  **Ogólne**, a następnie wybierz pozycję **Włącz tylko mój kod**.

- **Określ symbole do załadowania**

    W przypadku debugowania natywnego ładowanie plików symboli (*. pdb*) jest kosztowne w odniesieniu do zasobów pamięci. Można skonfigurować ustawienia symboli debugera, aby zaoszczędzić pamięć. Zazwyczaj można skonfigurować rozwiązanie do ładowania tylko modułów z projektu.

    Aby określić ładowanie symboli, wybierz pozycję **Narzędzia**  >  **Opcje**  >  **debugowania**  >  **symbole**.

    Ustaw dla opcji **tylko określone moduły** , a nie **wszystkie moduły** , a następnie określ moduły, które chcesz załadować. Podczas debugowania można również kliknąć prawym przyciskiem myszy określone moduły w oknie **moduły** , aby jawnie dołączyć moduł do ładowania symboli. (Aby otworzyć okno podczas debugowania, wybierz **Debuguj**  >  **System Windows**  >  **Moduły**).

    Aby uzyskać więcej informacji, zobacz [Opis plików symboli](?view=vs-2019&preserve-view=true).

- **Wyłącz narzędzia diagnostyczne**

    Zaleca się wyłączenie profilowania procesora CPU po użyciu. Ta funkcja może zużywać duże ilości zasobów. Po włączeniu profilowania procesora CPU ten stan jest utrwalany w kolejnych sesjach debugowania, więc warto jawnie wyłączyć go po zakończeniu. Niektóre zasoby można zapisać, wyłączając narzędzia diagnostyczne podczas debugowania, jeśli nie są potrzebne podane funkcje.

    Aby wyłączyć **Narzędzia diagnostyczne**, Rozpocznij sesję debugowania, wybierz pozycję **Narzędzia**  >  **Opcje**  >  **debugowanie**  >  **Ogólne**, a następnie usuń zaznaczenie opcji **Włącz narzędzia diagnostyczne podczas debugowania** .

    Aby uzyskać więcej informacji, zobacz [narzędzia profilowania](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Wyłącz narzędzia i rozszerzenia

Niektóre narzędzia i rozszerzenia można wyłączyć, aby zwiększyć wydajność.

> [!TIP]
> Często można wyizolować problemy z wydajnością, wyłączając je i uruchamiając ponownie wydajność.

### <a name="managed-language-service-roslyn"></a>Usługa języka zarządzanego (Roslyn)

Aby uzyskać informacje dotyczące wydajności .NET Compiler Platform ("Roslyn"), zobacz [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

- **Wyłącz pełną analizę rozwiązania**

    Program Visual Studio wykonuje analizę całego rozwiązania, aby zapewnić rozbudowane środowisko o błędach przed wywołaniem kompilacji. Ta funkcja jest przydatna do identyfikowania błędów tak szybko, jak to możliwe. Jednak w przypadku dużych rozwiązań ta funkcja może zużywać znaczną ilość zasobów pamięci. Jeśli występują problemy z ilością pamięci lub podobnymi problemami, możesz wyłączyć to środowisko, aby zwolnić te zasoby. Domyślnie ta opcja jest włączona dla Visual Basic i wyłączone dla języka C#.

    Aby wyłączyć **pełną analizę rozwiązania**, wybierz   >  **Opcje** narzędzia  >  **Edytor tekstu**, a następnie wybierz opcję **Visual Basic** lub **C#**. Wybierz pozycję **Zaawansowane** i usuń zaznaczenie opcji **Włącz pełną analizę rozwiązania**.

- **Wyłącz CodeLens**

    Program Visual Studio wykonuje zadanie **Znajdź wszystkie odwołania** dla każdej metody w miarę wyświetlania. CodeLens udostępnia funkcje, takie jak wbudowane wyświetlanie liczby odwołań. Prace są wykonywane w osobnym procesie, takim jak *zadanie servicehub. RoslynCodeAnalysisService32*. W dużych rozwiązaniach lub w systemach z ograniczeniami zasobów ta funkcja może mieć znaczący wpływ na wydajność. Jeśli występują problemy z pamięcią, na przykład podczas ładowania dużego rozwiązania na komputerze 4-GB lub dużego użycia procesora CPU dla tego procesu, można wyłączyć CodeLens w celu zwolnienia zasobów.

    Aby wyłączyć **CodeLens**, wybierz   >  **Opcje** narzędzia  >  **Edytor tekstu**  >  **wszystkie języki**  >  **CodeLens** i usuń zaznaczenie tej funkcji.

    > [!NOTE]
    > CodeLens jest dostępny w wersjach Professional i Enterprise programu Visual Studio.

### <a name="other-tools-and-extensions"></a>Inne narzędzia i rozszerzenia

- **Wyłącz rozszerzenia**

    Rozszerzenia to dodatkowe składniki oprogramowania dodane do programu Visual Studio, które udostępniają nowe funkcje lub rozszerzają istniejące funkcje. Rozszerzenia często mogą być źródłem problemów z zasobami pamięci. Jeśli występują problemy z zasobami pamięci, spróbuj wyłączać rozszerzenia pojedynczo, aby zobaczyć, jak ma to wpływ na scenariusz lub przepływ pracy.

   ::: moniker range="vs-2017"

    Aby wyłączyć rozszerzenia, przejdź do pozycji **Narzędzia** > **rozszerzenia i aktualizacje**, a następnie wyłącz określone rozszerzenie.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Aby wyłączyć rozszerzenia, przejdź do **rozszerzeń** > **Zarządzanie rozszerzeniami** i Wyłącz określone rozszerzenie.

   ::: moniker-end

- **Wyłącz tryb mapy**

    [**Tryb mapy**](how-to-track-your-code-by-customizing-the-scrollbar.md#display-modes) wyświetla linie kodu w miniaturach na pasku przewijania. Tryb mapy jest domyślnie włączony.

    Aby wyłączyć tryb mapy, przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **wszystkie języki**  >  **paski przewijania** i w sekcji **zachowanie** Usuń zaznaczenie opcji **Użyj trybu mapy dla pionowego paska przewijania** .

- **Wyłącz Zawijanie wierszy**

    [**Zawijanie**](./reference/how-to-manage-word-wrap-in-the-editor.md) wierszy wyświetla część długiego wiersza kodu, który wykracza poza bieżącą szerokość okna edytora kodu. Zawijanie słów jest domyślnie włączone.

    Aby wyłączyć zawijanie wyrazów dla projektu, nad którym pracujesz, przejdź do obszaru **Edycja**  >  **Zaawansowane**  >  **Zawijanie wierszy**. (Można przełączać to ustawienie za pomocą tych samych poleceń menu).

    Aby wyłączyć Zawijanie wierszy dla wszystkich projektów, przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **Ogólne**  >  **Edytor tekstu**  >  **wszystkie języki**  >  **Ogólne** i w sekcji **Ustawienia** Usuń zaznaczenie opcji **zawijania wyrazów** .

- **Wyłącz projektant XAML**

    Projektant XAML jest domyślnie włączony, ale tylko wtedy, gdy otworzysz plik *. XAML* . Jeśli pracujesz z plikami XAML, ale nie chcesz korzystać z funkcjonalności projektanta, wyłącz tę funkcję, aby zwolnić część pamięci.

    Aby wyłączyć Projektant XAML, przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **Projektant XAML**  >  **Włącz Projektant XAML** i usuń zaznaczenie opcji.

- **Usuń obciążenia**

    Możesz użyć Instalator programu Visual Studio, aby usunąć obciążenia, które nie są już używane. Ta akcja może usprawnić koszty uruchamiania i wykonywania, pomijając pakiety i zestawy, które nie są już potrzebne.

- **Dodaj Nieśledzone pliki do pliku Local. gitignore**

    Program Visual Studio uruchamia polecenie git `git status` z nieśledzonymi plikami, aby zapewnić bezproblemowe środowisko przy dodawaniu nowych plików do repozytorium. Jeśli istnieje duża liczba nieśledzonych plików, `git status` może zużywać dodatkową pamięć. Aby zignorować te pliki i zwiększyć wydajność programu `git status` , możesz dodać te pliki lub foldery do pliku Local. gitignore. Aby uzyskać dostęp do pliku, przejdź do pozycji ustawienia **git** ustawienia  >    >  **repozytorium git**. Następnie w sekcji **pliki git** kliknij przycisk **Dodaj** , aby utworzyć plik. gitignore, lub kliknij przycisk **Edytuj** , jeśli już istnieje.

## <a name="force-a-garbage-collection"></a>Wymuś wyrzucanie elementów bezużytecznych

Środowisko CLR używa systemu zarządzania pamięcią do wyrzucania elementów bezużytecznych. W tym systemie czasami pamięć jest używana przez obiekty, które nie są już potrzebne. Ten stan jest tymczasowy; Moduł wyrzucania elementów bezużytecznych zwolni tę pamięć na podstawie jej heurystyki wydajności i użycia zasobów. Można wymusić zebranie przez środowisko CLR dowolnej nieużywanej pamięci przy użyciu klawisza skrótu w programie Visual Studio. Jeśli istnieje znaczna ilość elementów bezużytecznych oczekujących na zbieranie i wymuszenie wyrzucania elementów bezużytecznych, należy zobaczyć użycie pamięci przez Porzuć proces *devenv.exe* w **Menedżerze zadań**. Nie trzeba używać tej metody. Jednak po ukończeniu kosztownej operacji (np. pełnej kompilacji, sesji debugowania lub otwartego zdarzenia rozwiązania) może pomóc określić, ile pamięci jest rzeczywiście używane przez proces. Ponieważ program Visual Studio jest mieszany (zarządzany & Native), czasami istnieje możliwość, że natywny Alokator i moduł wyrzucania elementów bezużytecznych konkurują o ograniczonych zasobach pamięci. W warunkach dużego użycia pamięci może być pomocne, aby wymusić uruchomienie modułu wyrzucania elementów bezużytecznych.

Aby wymusić wyrzucanie elementów bezużytecznych, użyj klawisza skrótu **Ctrl** + **Alt** + **SHIFT** + , **Ctrl** + **Alt** + **SHIFT** + **F12** (naciśnij dwukrotnie przycisk).

Jeśli wymuszenie nieniezawodnego wyrzucania elementów bezużytecznych sprawia, że Twój scenariusz działa, należy zgłosić raport za pomocą narzędzia opinii programu Visual Studio, ponieważ takie zachowanie może być przyczyną błędu.

Aby uzyskać szczegółowy opis modułu zbierającego elementy bezużyteczne środowiska CLR, zobacz podstawowe informacje na temat [odzyskiwania pamięci](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Zobacz też

- [Optymalizowanie wydajności programu Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Szybsze ładowanie rozwiązań (blog programu Visual Studio)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)