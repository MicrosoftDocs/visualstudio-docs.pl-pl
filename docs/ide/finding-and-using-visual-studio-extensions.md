---
title: Znajdź i zainstaluj rozszerzenia
description: Dowiedz się więcej o rozszerzeniach w programie Visual Studio i sposobach zarządzania nimi, aby korzystać z kontrolek, przykładów, szablonów, narzędzi i innych składników, których potrzebujesz.
ms.custom: SEO-VS-2020
ms.date: 09/18/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bb088954833f42e35de6c8316e5553d0f9e3fc68
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945594"
---
# <a name="manage-extensions-for-visual-studio"></a>Zarządzanie rozszerzeniami dla programu Visual Studio

Rozszerzenia są pakietami kodu, które działają w programie Visual Studio i udostępniają nowe lub udoskonalone funkcje. Rozszerzeniami mogą być formanty, przykłady, szablony, narzędzia lub inne składniki, które dodają funkcje do programu Visual Studio, na przykład [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) lub [Visual Studio rozszerzenia intellicode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode).

Aby uzyskać informacje na temat tworzenia rozszerzeń programu Visual Studio, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Informacje o korzystaniu z rozszerzeń można znaleźć na stronie poszczególnych rozszerzeń na [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Okno dialogowe rozszerzenia i aktualizacje

Za pomocą okna dialogowego **rozszerzenia i aktualizacje** można zainstalować rozszerzenia programu Visual Studio i zarządzać nimi. Aby otworzyć okno dialogowe **rozszerzenia i aktualizacje** , wybierz **pozycję Narzędzia**  >  **rozszerzenia i aktualizacje** lub wpisz **rozszerzenia** w polu wyszukiwania **Szybkie uruchamianie** .

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Okno dialogowe Zarządzanie rozszerzeniami

Za pomocą okna dialogowego **Zarządzanie rozszerzeniami** można instalować rozszerzenia programu Visual Studio i zarządzać nimi. Aby otworzyć okno dialogowe **Zarządzanie rozszerzeniami** , wybierz **rozszerzenia**  >  **Zarządzanie rozszerzeniami**. Lub wpisz **rozszerzenia** w polu wyszukiwania i wybierz pozycję **Zarządzaj rozszerzeniami**.

::: moniker-end

![Okno rozszerzeń w programie Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

W okienku po lewej stronie są dostępne rozszerzenia, które są zainstalowane, które są dostępne w Visual Studio Marketplace (**online**), oraz te, które mają dostępną aktualizację. **Menedżer rozszerzenia roamingu** utrzymuje listę wszystkich rozszerzeń programu Visual Studio, które zostały zainstalowane na dowolnym komputerze lub wystąpieniu programu Visual Studio. Jest ona zaprojektowana, aby umożliwić łatwiejsze znajdowanie ulubionych rozszerzeń.

## <a name="find-and-install-extensions"></a>Znajdź i zainstaluj rozszerzenia

::: moniker range="vs-2017"

Rozszerzenia można zainstalować z [Visual Studio Marketplace](https://marketplace.visualstudio.com) lub okna dialogowego rozszerzenia i aktualizacje w programie Visual Studio.

Aby zainstalować rozszerzenia z poziomu programu Visual Studio:

1. W obszarze **Narzędzia**  >  **rozszerzenia i aktualizacje** Znajdź rozszerzenie, które chcesz zainstalować. Jeśli znasz nazwę lub część nazwy rozszerzenia, możesz wyszukać w oknie **wyszukiwania** .

2. Kliknij pozycję **Pobierz**.

   Zaplanowano zainstalowanie rozszerzenia. Rozszerzenie zostanie zainstalowane po zamknięciu wszystkich wystąpień programu Visual Studio.

Podczas próby instalacji rozszerzenia, które ma zależności, instalator sprawdza, czy są one już zainstalowane. Jeśli nie są zainstalowane, okno dialogowe **rozszerzenia i aktualizacje** zawiera listę zależności, które należy zainstalować przed zainstalowaniem rozszerzenia.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Zainstaluj bez korzystania z okna dialogowego rozszerzenia i aktualizacje

Rozszerzenia, które zostały spakowane w plikach *. vsix* , mogą być dostępne w lokalizacjach innych niż Visual Studio Marketplace. Okna   >  dialogowego **rozszerzenia i aktualizacje** narzędzi nie mogą wykryć tych plików, ale można zainstalować plik *. vsix* , klikając dwukrotnie plik lub wybierając plik i naciskając klawisz **Enter**. Następnie postępuj zgodnie z instrukcjami. Po zainstalowaniu rozszerzenia można użyć okna dialogowego **rozszerzenia i aktualizacje** , aby je włączyć, wyłączyć lub odinstalować.

> [!NOTE]
> - Visual Studio Marketplace zawiera rozszerzenia VSIX i MSI. Okna dialogowe rozszerzenia i aktualizacje nie mogą włączać ani wyłączać rozszerzeń MSI.
> - Jeśli rozszerzenie programu MSI zawiera plik *rozszerzenia. vsixmanifest* , rozszerzenie pojawia się w oknie dialogowym **rozszerzenia i aktualizacje** .

::: moniker-end

::: moniker range=">=vs-2019"

Rozszerzenia można zainstalować z [Visual Studio Marketplace](https://marketplace.visualstudio.com) lub okna dialogowego Zarządzanie rozszerzeniami w programie Visual Studio.

Aby zainstalować rozszerzenia z poziomu programu Visual Studio:

1. W obszarze **rozszerzenia**  >  **Zarządzaj rozszerzeniami** Znajdź rozszerzenie, które chcesz zainstalować. (Jeśli znasz nazwę lub część nazwy rozszerzenia, możesz wyszukać w oknie **wyszukiwania** ).

2. Kliknij pozycję **Pobierz**.

   Zaplanowano zainstalowanie rozszerzenia. Rozszerzenie zostanie zainstalowane po zamknięciu wszystkich wystąpień programu Visual Studio.

Podczas próby instalacji rozszerzenia, które ma zależności, instalator sprawdza, czy są one już zainstalowane. Jeśli nie są zainstalowane, okno dialogowe **Zarządzanie rozszerzeniami** zawiera listę zależności, które należy zainstalować przed zainstalowaniem rozszerzenia.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Zainstaluj bez korzystania z okna dialogowego Zarządzanie rozszerzeniami

Rozszerzenia, które zostały spakowane w plikach *. vsix* , mogą być dostępne w lokalizacjach innych niż Visual Studio Marketplace. Okno dialogowe **rozszerzenia**  >  **zarządzania** rozszerzeniami nie może wykryć tych plików, ale plik *. vsix* można zainstalować przez dwukrotne kliknięcie pliku lub wybranie pliku, a następnie naciśnięcie klawisza **Enter**. Następnie postępuj zgodnie z instrukcjami. Po zainstalowaniu rozszerzenia można użyć okna dialogowego **Zarządzanie rozszerzeniami** , aby je włączyć, wyłączyć lub odinstalować.

> [!NOTE]
> - Visual Studio Marketplace zawiera rozszerzenia VSIX i MSI. Okno dialogowe Zarządzanie rozszerzeniami nie może włączać ani wyłączać rozszerzeń MSI.
> - Jeśli rozszerzenie programu MSI zawiera plik *rozszerzenia. vsixmanifest* , rozszerzenie pojawia się w oknie dialogowym **Zarządzanie rozszerzeniami** .

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Odinstaluj lub Wyłącz rozszerzenie

Jeśli nie chcesz już dłużej używać rozszerzenia, możesz je wyłączyć lub odinstalować. Wyłączone rozszerzenie jest wciąż zainstalowane, ale nie jest załadowane. Znajdź rozszerzenie, a następnie kliknij przycisk **Odinstaluj** lub **Wyłącz**. Uruchom ponownie program Visual Studio, aby zwolnić wyłączone rozszerzenie.

> [!NOTE]
> Rozszerzenia VSIX można wyłączyć, ale nie rozszerzenia, które zostały zainstalowane przy użyciu pliku MSI. Rozszerzenia zainstalowane w pliku MSI można odinstalować tylko.

## <a name="per-user-and-administrative-extensions"></a>Rozszerzenia dla poszczególnych użytkowników i administratorów

Większość rozszerzeń jest dla poszczególnych użytkowników i są instalowane w folderze *%LocalAppData%\Microsoft\VisualStudio \\<programu Visual Studio w wersji \> \Extensions \\* . Niektóre rozszerzenia są rozszerzeniami administracyjnymi i są instalowane w folderze *\<Visual Studio installation folder> \Common7\IDE\Extensions \\* .

Aby chronić system przed rozszerzeniami, które mogą zawierać błędy lub złośliwy kod, można ograniczyć rozszerzenia dla poszczególnych użytkowników tylko wtedy, gdy program Visual Studio jest uruchamiany z normalnymi uprawnieniami użytkownika. Oznacza to, że rozszerzenia dla poszczególnych użytkowników są wyłączone po uruchomieniu programu Visual Studio z podniesionymi uprawnieniami.

Aby ograniczyć czas ładowania rozszerzeń dla poszczególnych użytkowników:

1. Otwórz stronę opcje rozszerzeń (opcje **Narzędzia**  >    >    >  **rozszerzenia** środowiska).

2. Wyczyść pole wyboru **Załaduj rozszerzenia na użytkownika podczas uruchamiania jako administrator** .

3. Uruchom ponownie program Visual Studio.

## <a name="automatic-extension-updates"></a>Automatyczne aktualizacje rozszerzeń

Rozszerzenia są aktualizowane automatycznie, gdy nowa wersja jest dostępna w Visual Studio Marketplace. Nowa wersja rozszerzenia zostanie wykryta i zainstalowana w tle. Przy następnym otwarciu programu Visual Studio zostanie uruchomiona nowa wersja rozszerzenia.

Jeśli chcesz wyłączyć aktualizacje automatyczne, możesz wyłączyć tę funkcję dla wszystkich rozszerzeń lub tylko dla określonych rozszerzeń.

::: moniker range="vs-2017"

- Aby wyłączyć aktualizacje automatyczne dla wszystkich rozszerzeń, wybierz link **Zmień ustawienia rozszerzeń i aktualizacji** w oknie   >  dialogowym **rozszerzenia i aktualizacje** narzędzi. W oknie dialogowym **Opcje** Usuń zaznaczenie pola wyboru **automatycznie Aktualizuj rozszerzenia**.

- Aby wyłączyć aktualizacje automatyczne dla określonego rozszerzenia, usuń zaznaczenie pola wyboru **automatycznie Aktualizuj to rozszerzenie** w okienku szczegółów rozszerzenia po prawej stronie okna dialogowego **rozszerzenia i aktualizacje** .

::: moniker-end

::: moniker range=">=vs-2019"

- Aby wyłączyć aktualizacje automatyczne dla wszystkich rozszerzeń, należy wybrać łącze **Zmień ustawienia dla rozszerzeń** w oknie dialogowym **rozszerzenia**  >  **Zarządzanie** rozszerzeniami. W oknie dialogowym **Opcje** Usuń zaznaczenie pola wyboru **automatycznie Aktualizuj rozszerzenia**.

- Aby wyłączyć aktualizacje automatyczne dla określonego rozszerzenia, usuń zaznaczenie pola wyboru **automatycznie Aktualizuj to rozszerzenie** w okienku szczegółów rozszerzenia po prawej stronie okna dialogowego **Zarządzanie rozszerzeniami** .

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Powiadomienia o awarii i braku odpowiedzi

Program Visual Studio powiadamia użytkownika, jeśli podejrzewa, że rozszerzenie dotyczyło awarii podczas poprzedniej sesji. Gdy program Visual Studio ulega awarii, przechowuje stos wyjątków. Przy następnym uruchomieniu programu Visual Studio sprawdzi on stos, rozpoczynając od liścia i przechodząc do bazy. Jeśli program Visual Studio ustali, że ramka należy do modułu, który jest częścią zainstalowanego i włączonego rozszerzenia, wyświetla powiadomienie.

Program Visual Studio powiadamia również o tym, czy podejrzewa, że rozszerzenie jest przyczyną braku odpowiedzi interfejsu użytkownika.

Gdy te powiadomienia są wyświetlane, można zignorować powiadomienie lub wykonać jedną z następujących czynności:

::: moniker range="vs-2017"

- Wybierz opcję **Wyłącz to rozszerzenie**. Program Visual Studio wyłącza rozszerzenie i pozwala sprawdzić, czy konieczne jest ponowne uruchomienie systemu, aby wyłączenie zaczęło obowiązywać. W razie potrzeby można ponownie włączyć rozszerzenie w oknie   >  dialogowym **rozszerzenia i aktualizacje** narzędzi.

::: moniker-end

::: moniker range=">=vs-2019"

- Wybierz opcję **Wyłącz to rozszerzenie**. Program Visual Studio wyłącza rozszerzenie i pozwala sprawdzić, czy konieczne jest ponowne uruchomienie systemu, aby wyłączenie zaczęło obowiązywać. Jeśli chcesz, możesz ponownie włączyć rozszerzenie w oknie dialogowym **rozszerzenia**  >  **Zarządzanie** rozszerzeniami.

::: moniker-end

- Wybierz **nigdy nie pokazuj tego komunikatu ponownie**.

  - Jeśli powiadomienie dotyczy awarii w poprzedniej sesji, program Visual Studio nie wyświetla powiadomienia, gdy wystąpi awaria skojarzona z tym rozszerzeniem. Program Visual Studio będzie nadal wyświetlał powiadomienia, gdy nie można skojarzyć z tym rozszerzeniem lub w przypadku awarii lub braku odpowiedzi, które mogą być skojarzone z innymi rozszerzeniami.
  - Jeśli powiadomienie dotyczy braku odpowiedzi, zintegrowane środowisko programistyczne (IDE) nie pokazuje już powiadomienia, gdy to rozszerzenie jest skojarzone z nieodpowiedzią. Program Visual Studio będzie nadal wyświetlał powiadomienia dotyczące awarii dla tego rozszerzenia oraz powiadomienia dotyczące awarii i nieodpowiedzi dla innych rozszerzeń.

- Wybierz pozycję **Dowiedz się więcej** , aby przejść do tej strony.

- Wybierz przycisk **X** na końcu powiadomienia, aby odrzucić powiadomienie. Nowe powiadomienie pojawi się w przyszłych wystąpieniach rozszerzenia skojarzonego z awarią lub nieodpowiedzią interfejsu użytkownika.

> [!NOTE]
> Nieodpowiadający interfejs użytkownika lub powiadomienie o awarii oznacza tylko, że jeden z modułów rozszerzenia znajdował się na stosie, gdy interfejs użytkownika nie odpowiada lub wystąpił błąd. Nie musi to oznaczać, że rozszerzenie było przyczyna. Istnieje możliwość, że rozszerzenie wywołuje kod, który jest częścią programu Visual Studio, co z kolei spowodowało nieodpowiadający interfejs użytkownika lub awarię. Jednak powiadomienie może być nadal przydatne, jeśli rozszerzenie, które doprowadziło do nieodpowiedzi interfejsu użytkownika lub awarii, nie jest ważne dla użytkownika. W takim przypadku wyłączenie rozszerzenia pozwala uniknąć braku odpowiedzi interfejsu użytkownika lub awarii w przyszłości bez wywierania wpływu na wydajność.

## <a name="samples"></a>Samples

Po zainstalowaniu przykładu online, rozwiązanie jest przechowywane w dwóch miejscach:

- Kopia robocza jest przechowywana w lokalizacji określonej podczas tworzenia projektu.

- Oddzielna kopia główna jest przechowywana na komputerze.

::: moniker range="vs-2017"

Za pomocą  > okna dialogowego **rozszerzenia i aktualizacje** narzędzi można wykonywać następujące zadania związane z przykładami:

::: moniker-end

::: moniker range=">=vs-2019"

Można użyć okna dialogowego **rozszerzenia** > **Zarządzanie rozszerzeniami** , aby wykonać następujące zadania związane z przykładami:

::: moniker-end

- Wypisanie listy kopii głównych przykładów, które zostały zainstalowane.

- Wyłączenie lub odinstalowanie kopii głównej przykładu.

- Zainstalowanie pakietów przykładów, które są zbiorami przykładów odnoszących się do technologii lub funkcji.

- Instalowanie pojedynczych przykładów online.

- Wyświetlanie powiadomień o aktualizacjach, gdy zostaną opublikowane zmiany kodu źródłowego dla zainstalowanych przykładów.

- Zaktualizuj główną kopię zainstalowanego przykładu w przypadku powiadomienia o aktualizacji.

## <a name="see-also"></a>Zobacz też

- [Witryna Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
