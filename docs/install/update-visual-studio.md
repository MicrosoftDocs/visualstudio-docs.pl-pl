---
title: Aktualizowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zaktualizować program Visual Studio do najnowszej wersji, krok po kroku.
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19da163c76724ae56c0e3d83f1ed795333d081d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77453398"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Aktualizowanie programu Visual Studio do najnowszej wersji

::: moniker range="vs-2017"

Zachęcamy do aktualizacji do [najnowszej wersji](/visualstudio/releasenotes/vs2017-relnotes/) programu Visual Studio 2017, dzięki czemu zawsze można uzyskać najnowsze funkcje, poprawki i ulepszenia.

Jeśli chcesz wypróbować naszą najnowszą wersję, rozważ pobranie i zainstalowanie [programu Visual Studio 2019.](https://visualstudio.microsoft.com/downloads)

> [!IMPORTANT]
> Musisz zalogować się przy użyciu konta, które ma uprawnienia administracyjne do instalowania, aktualizowania lub modyfikowania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Uprawnienia użytkownika i Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. Aby zapoznać się z programem Visual Studio dla komputerów Mac, zobacz [Aktualizowanie programu Visual Studio dla komputerów Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Aktualizacja programu Visual Studio 2017 w wersji 15.6 lub nowszej

Usprawniliśmy instalację i aktualizację, aby ułatwić korzystanie bezpośrednio z poziomu ide. Poniżej opisano, jak zaktualizować program Visual Studio z wersji 15.6 i nowszych.

### <a name="using-the-notifications-hub"></a>Korzystanie z Centrum Powiadomień

Gdy jest aktualizacja, istnieje odpowiednia flaga powiadomień w programie Visual Studio.

1. Zapisz pracę.

1. Wybierz flagę powiadomień, aby otworzyć Centrum **powiadomień,** a następnie wybierz aktualizację, którą chcesz zainstalować.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/vs-install-notifications-hub-15dot6.png "Centrum powiadomień w programie Visual Studio 2017")

      > [!TIP]
      > Aktualizacja dla wersji programu Visual Studio 2017 jest kumulatywna, więc zawsze należy zainstalować tę z najnowszym numerem wersji.

1. Po otwarciu okna dialogowego **Aktualizacja** wybierz pozycję **Aktualizuj teraz**.

    ![Aktualizowanie programu Visual Studio 2017 przy użyciu okna dialogowego Aktualizacja z centrum powiadomień](media/vs-update-now-from-notifications-hub.png "Okno dialogowe Aktualizacja z Centrum Powiadomień w programie Visual Studio")

     Jeśli zostanie otwarte okno dialogowe Kontrola dostępu użytkownika, wybierz pozycję **Tak**. Następnie okno dialogowe "Poczekaj" może zostać otwarte na chwilę, a następnie instalator programu Visual Studio otworzy się, aby rozpocząć aktualizację.

     ![Nowe środowisko instalatora programu Visual Studio w wersji 15.6](media/visual-studio-15dot6-installer.png "Nowe środowisko instalatora programu Visual Studio w wersji 15.6")

     Aktualizacja jest kontynuowana. Następnie po jego zakończeniu program Visual Studio uruchamia się ponownie.

     > [!NOTE]
     > Po uruchomieniu programu Visual Studio w trybie administratora, należy ręcznie ponownie uruchomić program Visual Studio po aktualizacji.

### <a name="using-the-ide"></a>Używanie IDE

Można sprawdzić, czy aktualizacja, a następnie zainstalować aktualizację z paska menu w programie Visual Studio.

1. Zapisz pracę.

1. Wybierz pozycję **Pomoc** > **Sprawdź dostępność aktualizacji**.

     ![Nowe menu Pomoc w programie Visual Studio w wersji 15.6](media/vs-help-menu-check-for-updates.png "Nowe menu Pomoc w programie Visual Studio w wersji 15.6")

1. Po otwarciu okna dialogowego **Aktualizacja** wybierz pozycję **Aktualizuj teraz**.

   Aktualizacja jest kontynuowana zgodnie z opisem w poprzedniej sekcji, a następnie program Visual Studio uruchamia się ponownie po pomyślnym zakończeniu aktualizacji.

   > [!NOTE]
   > Po uruchomieniu programu Visual Studio w trybie administratora, należy ręcznie ponownie uruchomić program Visual Studio po aktualizacji.

### <a name="using-the-visual-studio-installer"></a>Korzystanie z Instalatora programu Visual Studio

Podobnie jak we wcześniejszych wersjach programu Visual Studio, można użyć Instalatora programu Visual Studio, aby zainstalować aktualizację.

1. Zapisz pracę.

1. Otwórz instalatora. Instalator programu Visual Studio może wymagać aktualizacji przed kontynuowaniem.

   > [!NOTE]
   > Na komputerze z systemem Windows 10 instalator pod literą **V** można znaleźć jako **Instalator programu Visual Studio**lub pod literą **M** jako Instalator programu Microsoft **Visual Studio**.

1. Na **stronie Produkt** w instalatorze poszukaj wersji programu Visual Studio, która została wcześniej zainstalowana.

1. Jeśli aktualizacja jest dostępna, zostanie wyświetlony przycisk **Aktualizuj.** (Ustalenie, czy aktualizacja jest dostępna, może potrwać kilka sekund).

   Wybierz przycisk **Aktualizuj,** aby zainstalować aktualizacje.

     ![Aktualizowanie programu Visual Studio 2017 przy użyciu instalatora programu Visual Studio](media/update-visual-studio.png "Aktualizowanie programu Visual Studio 2017 przy użyciu instalatora programu Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Aktualizacja programu Visual Studio 2017 w wersji 15.5 lub wcześniejszej

Jeśli używasz wcześniejszej wersji, oto jak zastosować aktualizację z programu Visual Studio 2017 w wersji 15.0 do wersji 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Aktualizuj za pomocą Centrum Powiadomień

1. Gdy są aktualizacje, istnieje odpowiednia flaga powiadomień w programie Visual Studio.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notification-flag.png "Flaga powiadomienia o aktualizacji w programie Visual Studio")

   Wybierz flagę powiadomień, aby otworzyć Centrum **powiadomień.**

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notifications-hub.png "Centrum powiadomień w programie Visual Studio")

      > [!TIP]
      > Aktualizacja dla wersji programu Visual Studio 2017 jest kumulatywna, więc zawsze należy zainstalować tę z najnowszym numerem wersji.

1. Wybierz **opcję "Visual Studio Update" jest dostępna**, która otwiera rozszerzenia i **aktualizacje** okna dialogowego.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu centrum powiadomień](media/notifications-hub-select.png "Centrum powiadomień w programie Visual Studio")

1. W oknie dialogowym **Rozszerzenia i aktualizacje** wybierz przycisk **Aktualizuj.**

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu centrum powiadomień](media/notifications-extensions-and-updates.png "Okno dialogowe Rozszerzenia i aktualizacje w programie Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Więcej informacji o powiadomieniach programu Visual Studio

Visual Studio powiadamia użytkownika, gdy aktualizacja jest dostępna dla samego programu Visual Studio lub dla wszystkich składników, a także wtedy, gdy wystąpią pewne zdarzenia w środowisku programu Visual Studio.

* Gdy flaga powiadomień jest żółta, dostępna jest aktualizacja produktu programu Visual Studio do zainstalowania.
* Gdy flaga powiadomień jest czerwona, występuje problem z licencją.
* Gdy flaga powiadomień jest czarna, istnieją opcjonalne lub informacyjne wiadomości do przejrzenia.

Wybierz flagę powiadomień, aby otworzyć Centrum **powiadomień,** a następnie wybierz powiadomienia, na których chcesz działać. Możesz też zignorować lub odrzucić powiadomienie.

 ![Wyświetlanie opcjonalnej lub informacyjnej wiadomości w Centrum powiadomień](media/notification-flag-optional.png "Flaga powiadomienia o opcjonalnej lub informacyjnej wiadomości w programie Visual Studio")

Jeśli zdecydujesz się zignorować powiadomienie, Visual Studio przestaje je wyświetlać. Jeśli chcesz zresetować listę ignorowanych powiadomień, wybierz przycisk **Ustawienia** w Centrum Powiadomień.

   ![Wybierz przycisk Ustawienia w centrum powiadomień, aby wyświetlić opcje powiadomień](media/vs-notifications-hub-settings-button.png "Wybieranie przycisku Ustawienia w centrum powiadomień, aby wyświetlić opcje powiadomień")

### <a name="update-by-using-the-visual-studio-installer"></a>Aktualizowanie przy użyciu Instalatora programu Visual Studio

1. Otwórz instalatora. Przed kontynuowaniem może być konieczne zaktualizowanie instalatora. W takim przypadku zostanie wyświetlony monit o zrobienie tego.

   > [!NOTE]
   > Na komputerze z systemem Windows 10 instalator pod literą **V** można znaleźć jako **Instalator programu Visual Studio**lub pod literą **M** jako Instalator programu Microsoft **Visual Studio**.

1. Na **stronie Produkt** w instalatorze poszukaj wersji programu Visual Studio, która została zainstalowana wcześniej.

1. Jeśli aktualizacja jest dostępna, zostanie wyświetlony przycisk **Aktualizuj.** (Ustalenie, czy aktualizacja jest dostępna, może potrwać kilka sekund).

   Wybierz przycisk **Aktualizuj,** aby zainstalować aktualizacje.

     ![Aktualizowanie programu Visual Studio 2017 przy użyciu instalatora programu Visual Studio](media/update-visual-studio.png "Aktualizowanie programu Visual Studio przy użyciu Instalatora programu Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

Zachęcamy do aktualizacji do [najnowszej wersji](/visualstudio/releases/2019/release-notes/) programu Visual Studio 2019, dzięki czemu zawsze można uzyskać najnowsze funkcje, poprawki i ulepszenia.

Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie. Jeśli obecnie używasz innej wersji programu Visual Studio, możesz [zainstalować wersje programu Visual Studio obok siebie](../install/install-visual-studio-versions-side-by-side.md)lub [odinstalować poprzednie wersje programu Visual Studio](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Musisz zalogować się przy użyciu konta, które ma uprawnienia administracyjne do instalowania, aktualizowania lub modyfikowania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Uprawnienia użytkownika i Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. Aby zapoznać się z programem Visual Studio dla komputerów Mac, zobacz [Aktualizowanie programu Visual Studio dla komputerów Mac](/visualstudio/mac/update).

Poniżej opisano, jak&nbsp;&nbsp;zaktualizować program Visual Studio 2019.

## <a name="use-the-visual-studio-installer"></a>Korzystanie z Instalatora programu Visual Studio

1. Otwórz instalatora.

     ![Otwieranie Instalatora programu Visual Studio z systemu Windows](media/vs-2019/vs-installer-windows-start.png "Otwieranie Instalatora programu Visual Studio")

   Może być trzeba zaktualizować instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z instrukcjami.

1. W instalatorze poszukaj zainstalowanej wersji programu Visual Studio.

   Na przykład jeśli wcześniej zainstalowano&nbsp;&nbsp;visual studio community 2019 i jest aktualizacja dla niego, a następnie **aktualizacja dostępny** komunikat pojawi się w instalatorze.

     ![Wybierz wersję programu Visual Studio 2019, którą chcesz zaktualizować](media/vs-2019/vs-installer-update-visual-studio-community.png "Wybierz wersję programu Visual Studio 2019, którą chcesz zaktualizować")

1. Wybierz **pozycję Aktualizuj,** aby zainstalować aktualizacje.

    ![Wybierz przycisk Aktualizuj, aby zainstalować aktualizacje](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Wybierz przycisk Aktualizuj, aby zainstalować aktualizacje")

1. Po zakończeniu aktualizacji może zostać zostaniesz poproszony o ponowne uruchomienie komputera. Jeśli tak, zrób to, a następnie uruchom program Visual Studio w taki sposób, w jaki zwykle.

   Jeśli nie zostaniesz poproszony o ponowne uruchomienie komputera, wybierz przycisk **Uruchom,** aby uruchomić program Visual Studio z instalatora.

    ![Wybierz przycisk Uruchom, aby uruchomić program Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Wybierz przycisk Uruchom, aby uruchomić program Visual Studio")

## <a name="use-the-ide"></a>Korzystanie z IDE

Możesz sprawdzić dostępność aktualizacji, a następnie zainstalować ją za pomocą paska menu lub pola wyszukiwania w programie Visual Studio 2019.

### <a name="open-visual-studio"></a>Otwórz program Visual Studio.

1. Z menu **Start** systemu Windows wybierz pozycję **Visual Studio 2019**.

    ![Otwórz visual studio 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Otwórz program Visual Studio 2019 w systemie Windows")

1. W obszarze **Wprowadzenie**wybierz dowolną opcję, aby otworzyć IDE.

    ![Otwieranie Instalatora programu Visual Studio](media/vs2019-choose-option-from-get-started.png "Otwieranie Instalatora programu Visual Studio")

    Zostanie otwarty program Visual Studio. W IDE pojawia się komunikat **aktualizacji programu Visual Studio 2019.**

    ![Komunikat "Aktualizacja programu Visual Studio 2019" w usłudze IDE](media/vs-2019/update-visual-studio-ide-message.png "Komunikat "Aktualizacja programu Visual Studio 2019" w usłudze IDE")

1. W komunikacie **o aktualizacji programu Visual Studio 2019** wybierz pozycję Wyświetl **szczegóły**.

   ![Przycisk Wybierz pozycję Wyświetl szczegóły w komunikacie o aktualizacji IDE programu Visual Studio 2019](media/vs-2019/update-visual-studio-ide-view-details.png "Wybieranie przycisku Wyświetl szczegóły w komunikacie o aktualizacji programu Visual Studio 2019")

1. W oknie dialogowym **Aktualizacja pobrana i gotowa do zainstalowania** wybierz pozycję **Aktualizuj**.

     ![Wybierz przycisk Aktualizuj w oknie dialogowym "Aktualizacja pobrana i gotowa do zainstalowania"](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "Wybierz przycisk Aktualizuj w oknie dialogowym "Aktualizacja pobrana i gotowa do zainstalowania"")

   Visual Studio aktualizuje, zamyka, a następnie ponownie otwiera.

### <a name="in-visual-studio"></a>W programie Visual Studio

1. Na pasku menu wybierz pozycję **Pomoc**, a następnie wybierz pozycję **Sprawdź aktualizacje**.

     ![Wybierz polecenie "Sprawdź aktualizacje" z menu Pomoc](media/vs-2019/vs-ide-check-updates-help-menu.png "Wybierz polecenie "Sprawdź aktualizacje" z menu Pomoc")

    > [!NOTE]
    > Można również użyć pola wyszukiwania w IDE, aby sprawdzić dostępność aktualizacji. Naciśnij **klawisz Ctrl**+**Q**, wpisz "sprawdź aktualizacje", a następnie wybierz zgodny wynik wyszukiwania.

1. W oknie dialogowym **Aktualizowanie dostępnego** wybierz pozycję **Aktualizuj**.

     ![Wybierz przycisk Aktualizuj w oknie dialogowym "Aktualizacja pobrana i gotowa do zainstalowania"](media/vs-2019/update-visual-studio-community-from-ide.png "Wybierz przycisk Aktualizuj w oknie dialogowym "Aktualizacja pobrana i gotowa do zainstalowania"")

   Visual Studio aktualizuje, zamyka, a następnie ponownie otwiera.

## <a name="use-the-notifications-hub"></a>Korzystanie z Centrum Powiadomień

1. W programie Visual Studio zapisz swoją pracę.

1. Wybierz ikonę powiadomień w prawym dolnym rogu środowiska IDE programu Visual Studio, aby otworzyć centrum **powiadomień.**

   ![Ikona powiadomienia w programie Visual Studio IDE](media/vs-2019/notification-bar.png "Ikona powiadomienia w programie Visual Studio IDE")

1. W **centrum Powiadomień**wybierz aktualizację, którą chcesz zainstalować, a następnie wybierz pozycję **Wyświetl szczegóły**.

     ![Centrum powiadomień w programie Visual Studio 2019](media/vs-2019/notification-hub-update.png "Centrum powiadomień w programie Visual Studio 2019")

      > [!TIP]
      > Aktualizacja dla wersji programu Visual Studio 2019 jest kumulatywna, więc zawsze należy zainstalować tę z najnowszym numerem wersji.

1. W oknie dialogowym **Aktualizowanie dostępnego** wybierz pozycję **Aktualizuj**.

   Visual Studio aktualizuje, zamyka, a następnie ponownie otwiera.

## <a name="customize-update-settings"></a>Dostosowywanie ustawień aktualizacji

Ustawienia aktualizacji w programie Visual Studio można dostosować na kilka różnych sposobów, na przykład zmieniając tryb instalacji i wybierając automatyczne pobieranie.

Dostępne są dwa tryby instalacji:

* **Instalowanie podczas pobierania**
* **Pobierz wszystko, a następnie zainstaluj**

Można również wybrać ustawienie **Automatycznie pobieraj aktualizacje,** które umożliwia pobieranie aktualizacji, gdy komputer jest bezczynny.

Oto kroki tej procedury:

1. Na pasku menu wybierz pozycję **Opcje** **narzędzi** > .

2. Rozwiń **węzeł Środowisko**, a następnie wybierz pozycję **Aktualizacje produktów**.

    ![Ustawienia aktualizacji w programie Visual Studio](media/vs-2019/update-settings-options.png)

3. Wybierz tryb instalacji i opcje automatycznego pobierania, które chcesz pobrać dla aktualizacji programu Visual Studio.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie wersji programu Visual Studio obok siebie](install-visual-studio-versions-side-by-side.md)
* [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi](update-servicing-baseline.md)
* [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
