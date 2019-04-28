---
title: Znajdowanie i używanie rozszerzeń
ms.date: 01/30/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e282cdfda27579fd83871153a19897652d55865
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962067"
---
# <a name="find-and-use-visual-studio-extensions"></a>Znajdowanie i używanie rozszerzeń programu Visual Studio

Rozszerzenia programu Visual Studio są pakiety kodu, które są uruchamiane w programie Visual Studio i udostępnia nowe i ulepszone funkcje programu Visual Studio. Można znaleźć więcej informacji na temat rozszerzeń programu Visual Studio tutaj: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

::: moniker range="vs-2017"

Użyj **rozszerzenia i aktualizacje** okno dialogowe, aby zainstalować i zarządzać rozszerzeniami programu Visual Studio. Aby otworzyć **rozszerzenia i aktualizacje** okno dialogowe, wybierz **narzędzia** > **rozszerzenia i aktualizacje**, lub typu **rozszerzenia** w **Szybkie uruchamianie** pola wyszukiwania.

::: moniker-end

::: moniker range=">=vs-2019"

Użyj **Zarządzaj rozszerzeniami** okno dialogowe, aby zainstalować i zarządzać rozszerzeniami programu Visual Studio. Aby otworzyć **Zarządzaj rozszerzeniami** okno dialogowe, wybierz **rozszerzenia** > **Zarządzaj rozszerzeniami**. Lub typ **rozszerzenia** w wyszukiwaniu pole, a następnie wybierz **Zarządzaj rozszerzeniami**.

::: moniker-end

![Okno rozszerzeń w programie Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

W okienku po lewej stronie kategoryzuje rozszerzenia przez osoby, które są zainstalowane, te, które są dostępne w Visual Studio Marketplace (**Online**) oraz te, które są dostępne aktualizacje. **Menedżer roamingu rozszerzeń** przechowuje listę rozszerzeń programu Visual Studio po zainstalowaniu na dowolnym komputerze lub wystąpieniu programu Visual Studio. Został zaprojektowany tak, co pozwala łatwiej znaleźć ulubionych rozszerzeń.

## <a name="find-visual-studio-extensions"></a>Znajdowanie rozszerzeń programu Visual Studio

Można zainstalować rozszerzenia z [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Rozszerzeniami mogą być formanty, przykłady, szablony, narzędzia lub inne składniki, które dodają nowe funkcjonalności do programu Visual Studio. Program Visual Studio obsługuje rozszerzenia w formacie pakietu VSIX — te obejmują szablony projektów, szablony elementów, elementy **przybornika** elementów, składniki zarządzane rozszerzenia Framework (MEF) i pakiety VSPackages.

::: moniker range="vs-2017"

Można również pobrać i zainstalować rozszerzenia na podstawie tożsamości usługi Zarządzanej, ale **rozszerzenia i aktualizacje** okno dialogowe nie można je włączyć lub wyłączyć. Visual Studio Marketplace zawiera rozszerzenia MSI i VSIX.

::: moniker-end

::: moniker range=">=vs-2019"

Można również pobrać i zainstalować rozszerzenia na podstawie tożsamości usługi Zarządzanej, ale **Zarządzaj rozszerzeniami** okno dialogowe nie można je włączyć lub wyłączyć. Visual Studio Marketplace zawiera rozszerzenia MSI i VSIX.

::: moniker-end

## <a name="install-or-uninstall-visual-studio-extensions"></a>Instalowanie lub odinstalowywanie rozszerzenia programu Visual Studio

::: moniker range="vs-2017"

W **rozszerzenia i aktualizacje**, znaleźć rozszerzenia, którą chcesz zainstalować. (Jeśli znasz nazwę lub część nazwy rozszerzenia, możesz wyszukiwać w **wyszukiwania** okna.) Kliknij przycisk **Pobierz**. To rozszerzenie zaplanowano do zainstalowania. Rozszerzenie zostanie zainstalowane po zamknięciu wszystkich wystąpień programu Visual Studio.

Podczas próby instalacji rozszerzenia, które ma zależności, instalator sprawdza, czy są one już zainstalowane. Jeśli nie są zainstalowane, **rozszerzenia i aktualizacje** okno dialogowe zawiera listę zależności, które muszą być zainstalowane, zanim będzie można zainstalować rozszerzenia.

::: moniker-end

::: moniker range=">=vs-2019"

W **Zarządzaj rozszerzeniami**, znaleźć rozszerzenia, którą chcesz zainstalować. (Jeśli znasz nazwę lub część nazwy rozszerzenia, możesz wyszukiwać w **wyszukiwania** okna.) Kliknij przycisk **Pobierz**. To rozszerzenie zaplanowano do zainstalowania. Rozszerzenie zostanie zainstalowane po zamknięciu wszystkich wystąpień programu Visual Studio.

Podczas próby instalacji rozszerzenia, które ma zależności, instalator sprawdza, czy są one już zainstalowane. Jeśli nie są zainstalowane, **Zarządzaj rozszerzeniami** okno dialogowe zawiera listę zależności, które muszą być zainstalowane, zanim będzie można zainstalować rozszerzenia.

::: moniker-end

Jeśli nie chcesz już dłużej używać rozszerzenia, możesz je wyłączyć lub odinstalować. Wyłączone rozszerzenie jest wciąż zainstalowane, ale nie jest załadowane. Można wyłączyć tylko rozszerzenia VSIX; rozszerzenia, które zostały zainstalowane za pomocą Instalatora MSI można tylko odinstalować. Znaleźć rozszerzenia, a następnie kliknij przycisk **Odinstaluj** lub **wyłączyć**. Uruchom ponownie Visual Studio, aby zwolnić wyłączone rozszerzenie.

## <a name="per-user-and-administrative-extensions"></a>Rozszerzenia administracyjne i dla poszczególnych użytkowników

Większość rozszerzeń to rozszerzenia dla poszczególnych użytkowników i są instalowane w *%LocalAppData%\Microsoft\VisualStudio\\< wersja programu Visual Studio\>\Extensions\\*  folderu. Kilka rozszerzeń to rozszerzenia administracyjne i są instalowane w *\<folder instalacji programu Visual Studio > \Common7\IDE\Extensions\\* folderu.

Aby chronić system przed rozszerzeniami, które mogą zawierać błędy lub złośliwy kod, można ograniczyć rozszerzenia dla poszczególnych użytkowników można załadować tylko wtedy, gdy program Visual Studio jest uruchamiany z uprawnieniami zwykłego użytkownika. Oznacza to, że rozszerzenia dla poszczególnych użytkowników są wyłączone, po uruchomieniu programu Visual Studio z uprawnieniami administratora. Aby to zrobić, przejdź na stronę opcje rozszerzenia (**narzędzia** > **opcje** > **środowiska**  >   **Rozszerzenia**). Wyczyść **obciążenia rozszerzenia dla poszczególnych użytkowników podczas uruchamiania jako administrator** pole wyboru, a następnie uruchom ponownie program Visual Studio.

## <a name="automatic-extension-updates"></a>Aktualizacje automatyczne rozszerzenia

Rozszerzenia są automatycznie aktualizowane, gdy nowa wersja jest dostępna w Visual Studio Marketplace. Nowa wersja rozszerzenia jest wykryte i zainstalowane w tle. Przy następnym otwarciu programu Visual Studio, nowa wersja rozszerzenia zostanie uruchomiona.

Jeśli chcesz wyłączyć automatyczne aktualizacje, można wyłączyć funkcję dla wszystkich rozszerzeń lub tylko określone rozszerzenia.

::: moniker range="vs-2017"

- Aby wyłączyć aktualizacje automatyczne dla wszystkich rozszerzeń, wybierz opcję **zmiany ustawień rozszerzenia i aktualizacje** łącze w **rozszerzenia i aktualizacje** okna dialogowego. W **opcje** okno dialogowe, usuń zaznaczenie pola wyboru **automatyczne aktualizowanie rozszerzeń**.

- Aby wyłączyć automatyczne aktualizacje dla określonego rozszerzenia, usuń zaznaczenie pola wyboru **automatycznie Aktualizuj to rozszerzenie** opcji w okienku szczegółów rozszerzenia na prawej krawędzi **rozszerzenia i aktualizacje** okna dialogowego.

::: moniker-end

::: moniker range=">=vs-2019"

- Aby wyłączyć aktualizacje automatyczne dla wszystkich rozszerzeń, wybierz opcję **zmiany ustawień dla rozszerzeń** łącze w **Zarządzaj rozszerzeniami** okna dialogowego. W **opcje** okno dialogowe, usuń zaznaczenie pola wyboru **automatyczne aktualizowanie rozszerzeń**.

- Aby wyłączyć automatyczne aktualizacje dla określonego rozszerzenia, usuń zaznaczenie pola wyboru **automatycznie Aktualizuj to rozszerzenie** opcji w okienku szczegółów rozszerzenia na prawej krawędzi **Zarządzaj rozszerzeniami** okna dialogowego.

::: moniker-end

## <a name="extension-crash-and-unresponsiveness-notifications"></a>Powiadomienia o awariach i sek rozszerzenia

Program Visual Studio powiadamia użytkownika, jeśli podejrzenia, że rozszerzenie brał udział w awarii podczas poprzedniej sesji. Visual Studio ulega awarii, są przechowywane stosu wyjątków. Przy następnym uruchomieniu programu Visual Studio sprawdza, czy stosu, rozpoczynając od typu liść i działa na bazie. Jeśli program Visual Studio okaże się, że ramki należy do modułu, który jest częścią rozszerzenia zainstalowane i włączone, wyświetlane jest powiadomienie.

Program Visual Studio również powiadamia użytkownika, jeśli podejrzenia, że rozszerzenie jest przyczyną interfejsu użytkownika przestanie odpowiadać.

Gdy te powiadomienia są wyświetlane, można zignorować powiadomienie lub wykonać jedną z następujących czynności:

::: moniker range="vs-2017"

- Wybierz **Wyłącz to rozszerzenie**. Visual Studio wyłącza rozszerzenia i informuje o tym, czy należy ponownie uruchomić system wyłączenie zaczęły obowiązywać. Można ponownie włączyć rozszerzenia w **rozszerzenia i aktualizacje** okno dialogowe, jeśli chcesz.

::: moniker-end

::: moniker range=">=vs-2019"

- Wybierz **Wyłącz to rozszerzenie**. Visual Studio wyłącza rozszerzenia i informuje o tym, czy należy ponownie uruchomić system wyłączenie zaczęły obowiązywać. Można ponownie włączyć rozszerzenia w **Zarządzaj rozszerzeniami** okno dialogowe, jeśli chcesz.

::: moniker-end

- Wybierz **nigdy nie pokazuj tego komunikatu ponownie**.

  - Jeśli powiadomienia dotyczą awarii w poprzedniej sesji, program Visual Studio już nie wyświetla występuje powiadomienie, gdy awaria skojarzony z tym rozszerzeniem. Program Visual Studio w dalszym ciągu będzie powiadomienia w przypadku braku odpowiedzi może być skojarzony z tym rozszerzeniem lub awarie lub braku odpowiedzi, które mogą być skojarzone z innymi rozszerzeniami.
  - Jeśli powiadomienia dotyczą sek, IDE nie powoduje już zgłaszania powiadomienie po to rozszerzenie jest skojarzony z sek. Program Visual Studio w dalszym ciągu będzie powiadomień dotyczące awarii dla tego rozszerzenia i związane z awarii i sek powiadomienia dla innych rozszerzeń.

- Wybierz **więcej** wejść do tej strony.

- Wybierz **X** przycisk na końcu powiadomienie, aby odrzucić powiadomienie. Nowe powiadomienie pojawi się dla przyszłych wystąpień rozszerzenia są skojarzone z awarię lub brak reakcji interfejsu użytkownika.

> [!NOTE]
> Powiadomienie sek lub awarii interfejsu użytkownika oznacza tylko, że jeden z modułów rozszerzenia znajdowała się na stosie podczas odpowiadać interfejsu użytkownika lub w przypadku wystąpienia awarii. Nie musi to oznaczać, że rozszerzenia, sama jest przyczyna nadmiernego. Istnieje możliwość, że rozszerzenie wywołać kod, który jest częścią programu Visual Studio, co z kolei spowodowało interfejsu użytkownika nie odpowiada lub awarię. Jednak powiadomienia nadal może być przydatne, jeśli rozszerzenie, które doprowadziły do awarii lub brak reakcji interfejsu użytkownika nie jest dla Ciebie ważne. W tym przypadku wyłączenie rozszerzenia pozwala uniknąć braku odpowiedzi interfejsu użytkownika lub awaria w przyszłości, bez wywierania wpływu na wydajność.

## <a name="sample-master-copies-and-working-copies"></a>Przykład kopii głównych i kopie robocze

Po zainstalowaniu przykładu online, rozwiązanie jest przechowywane w dwóch miejscach:

- Kopia robocza znajduje się w lokalizacji, które zostały określone podczas tworzenia projektu.

- Oddzielna kopia główna jest przechowywana na komputerze.

::: moniker range="vs-2017"

Możesz użyć **rozszerzenia i aktualizacje** okna do wykonania tych zadań związanych z przykładami:

::: moniker-end

::: moniker range=">=vs-2019"

Możesz użyć **Zarządzaj rozszerzeniami** okna do wykonania tych zadań związanych z przykładami:

::: moniker-end

- Wypisanie listy kopii głównych przykładów, które zostały zainstalowane.

- Wyłączenie lub odinstalowanie kopii głównej przykładu.

- Zainstalowanie pakietów przykładów, które są zbiorami przykładów odnoszących się do technologii lub funkcji.

- Instalowanie pojedynczych przykładów online.

- Wyświetlanie powiadomień o aktualizacjach, gdy zostaną opublikowane zmiany kodu źródłowego dla zainstalowanych przykładów.

- Aktualizowanie kopii głównej zainstalowanego przykładu, po powiadomienie o aktualizacji.

::: moniker range="vs-2017"

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalowanie bez używania okna dialogowego rozszerzenia i aktualizacje

Rozszerzenia, które zostały spakowane do *.vsix* pliki mogą być dostępne w lokalizacjach innych niż Visual Studio Marketplace. **Rozszerzenia i aktualizacje** okno dialogowe nie może wykryć tych plików, ale można zainstalować *.vsix* pliku przez dwukrotne kliknięcie pliku, lub zaznacz ją i naciskając klawisz **Enter**klucza. Następnie postępuj zgodnie z instrukcjami. Jeśli rozszerzenie jest zainstalowane, możesz użyć **rozszerzenia i aktualizacje** okno dialogowe, aby ją włączyć, wyłączyć lub odinstaluj je.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Typy rozszerzeń, które nie są obsługiwane przez okno dialogowe rozszerzenia i aktualizacje

Program Visual Studio w dalszym ciągu obsługuje rozszerzenia, które są instalowane przez Instalator (MSI) programu Microsoft ale nie za pomocą **rozszerzenia i aktualizacje** okno dialogowe bez żadnych modyfikacji.

> [!TIP]
> Jeśli rozszerzenie opartym na MSI obejmuje *extension.vsixmanifest* rozszerzenie pojawia się w pliku **rozszerzenia i aktualizacje** okno dialogowe.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="installing-without-using-the-manage-extensions-dialog-box"></a>Instalowanie bez używania okna dialogowego Zarządzaj rozszerzeniami

Rozszerzenia, które zostały spakowane do *.vsix* pliki mogą być dostępne w lokalizacjach innych niż Visual Studio Marketplace. **Zarządzaj rozszerzeniami** okno dialogowe nie może wykryć tych plików, ale można zainstalować *.vsix* pliku przez dwukrotne kliknięcie pliku, lub zaznacz ją i naciskając klawisz **Enter** klucz. Następnie postępuj zgodnie z instrukcjami. Jeśli rozszerzenie jest zainstalowane, możesz użyć **Zarządzaj rozszerzeniami** okno dialogowe, aby ją włączyć, wyłączyć lub odinstaluj je.

## <a name="extension-types-not-supported-by-the-manage-extensions-dialog-box"></a>Typy rozszerzeń, które nie są obsługiwane przez okna dialogowego Zarządzaj rozszerzeniami

Program Visual Studio w dalszym ciągu obsługuje rozszerzenia, które są instalowane przez Instalator (MSI) programu Microsoft ale nie za pomocą **Zarządzaj rozszerzeniami** okno dialogowe bez żadnych modyfikacji.

> [!TIP]
> Jeśli rozszerzenie opartym na MSI obejmuje *extension.vsixmanifest* rozszerzenie pojawia się w pliku **Zarządzaj rozszerzeniami** okno dialogowe.

::: moniker-end