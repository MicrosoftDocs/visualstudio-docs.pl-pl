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
ms.sourcegitcommit: e3b9cbeea282f1b531c6a3f60515ebfe1688aa0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453398"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Aktualizowanie programu Visual Studio do najnowszej wersji

::: moniker range="vs-2017"

Zachęcamy do aktualizacji do najnowszej [wersji](/visualstudio/releasenotes/vs2017-relnotes/) programu Visual Studio 2017, aby zawsze uzyskać najnowsze funkcje, poprawki i ulepszenia.

Jeśli chcesz wypróbować naszą najnowszą wersję, rozważ pobranie i zainstalowanie [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads) .

> [!IMPORTANT]
> Musisz zalogować się za pomocą konta mającego uprawnienia administracyjne, aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [aktualizacja Visual Studio dla komputerów Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Aktualizacja programu Visual Studio 2017 w wersji 15.6 lub nowszej

Firma Microsoft usprawniliśmy instalacji i zaktualizować środowisko, aby ułatwić do użycia bezpośrednio z poziomu środowiska IDE. Poniżej przedstawiono sposób aktualizacji z wersji 15.6 i nowszych do nowszej wersji programu Visual Studio.

### <a name="using-the-notifications-hub"></a>Korzystanie z centrum powiadomień

Gdy jest dostępna aktualizacja, w programie Visual Studio znajduje się odpowiednia flaga powiadomienia.

1. Zapisz pracę.

1. Wybierz flagę powiadomienia, aby otworzyć Centrum **powiadomień** , a następnie wybierz aktualizację, którą chcesz zainstalować.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/vs-install-notifications-hub-15dot6.png "Centrum powiadomień w programie Visual Studio 2017")

      > [!TIP]
      > Aktualizacja wersji programu Visual Studio 2017 jest zbiorcza, więc zawsze należy wybrać opcję zainstalowania jej przy użyciu najnowszego numeru wersji.

1. Po otwarciu okna dialogowego **aktualizacji** wybierz pozycję **Aktualizuj teraz**.

    ![Aktualizowanie programu Visual Studio 2017 przy użyciu okna dialogowego aktualizacji z centrum powiadomień](media/vs-update-now-from-notifications-hub.png "Okno dialogowe Aktualizowanie z centrum powiadomień w programie Visual Studio")

     Jeśli zostanie otwarte okno dialogowe Access Control użytkownika, wybierz pozycję **tak**. Następnie okno dialogowe "Proszę czekać" może zostać otwarta przez chwilę, a następnie Instalatora programu Visual Studio otwiera, aby rozpocząć aktualizację.

     ![Nowe środowisko Instalator programu Visual Studio w wersji 15,6](media/visual-studio-15dot6-installer.png "Nowe środowisko Instalator programu Visual Studio w wersji 15,6")

     Nadal aktualizacji. Po zakończeniu, ponowne uruchomienie programu Visual Studio.

     > [!NOTE]
     > Po uruchomieniu programu Visual Studio w trybie administratora, należy ręcznie ponownie uruchomić Visual Studio po aktualizacji.

### <a name="using-the-ide"></a>Używanie IDE

Możesz sprawdzić dostępność aktualizacji i zainstalować aktualizację na pasku menu w programie Visual Studio.

1. Zapisz pracę.

1. Wybierz **pomoc** > **sprawdzić dostępność aktualizacji**.

     ![Nowe menu Pomoc w programie Visual Studio w wersji 15,6](media/vs-help-menu-check-for-updates.png "Nowe menu Pomoc w programie Visual Studio w wersji 15,6")

1. Po otwarciu okna dialogowego **aktualizacji** wybierz pozycję **Aktualizuj teraz**.

   Aktualizacja będzie kontynuowana zgodnie z opisem w poprzedniej sekcji, a następnie programu Visual Studio zostanie ponownie uruchomiony po pomyślnym ukończeniu aktualizacji.

   > [!NOTE]
   > Po uruchomieniu programu Visual Studio w trybie administratora, należy ręcznie ponownie uruchomić Visual Studio po aktualizacji.

### <a name="using-the-visual-studio-installer"></a>Korzystanie z Instalator programu Visual Studio

Tak jak w starszych wersjach programu Visual Studio, można użyć Instalator programu Visual Studio, aby zainstalować aktualizację.

1. Zapisz pracę.

1. Otwórz Instalator programu. Instalator programu Visual Studio może wymagać aktualizacji przed kontynuowaniem.

   > [!NOTE]
   > Na komputerze z systemem Windows 10 można znaleźć instalatora pod literą **V** jako **Instalator programu Visual Studio**lub pod literą **M** jako **Instalator Microsoft Visual Studio**.

1. Na stronie **produkt** w instalatorze zapoznaj się z wcześniej zainstalowaną wersją programu Visual Studio.

1. Jeśli dostępna jest aktualizacja, zobaczysz przycisk **Aktualizuj** . (Może potrwać kilka sekund Instalatora Aby ustalić, czy dostępna jest aktualizacja.)

   Kliknij przycisk **Aktualizuj** , aby zainstalować aktualizacje.

     ![Aktualizowanie programu Visual Studio 2017 przy użyciu Instalator programu Visual Studio](media/update-visual-studio.png "Aktualizowanie programu Visual Studio 2017 przy użyciu Instalator programu Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Aktualizacja programu Visual Studio 2017 w wersji 15.5 lub starszej

Jeśli używasz wcześniejszej wersji, Oto jak zastosować aktualizację z programu Visual Studio 2017 w wersji 15,0 do wersji 15,5.

### <a name="update-by-using-the-notifications-hub"></a>Aktualizowanie za pomocą Centrum powiadomień

1. Gdy są dostępne aktualizacje, brak odpowiednich Flaga powiadomienia w programie Visual Studio.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notification-flag.png "Flaga powiadomienia o aktualizacjach w programie Visual Studio")

   Wybierz flagę powiadomienia, aby otworzyć Centrum **powiadomień** .

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notifications-hub.png "Centrum powiadomień w programie Visual Studio")

      > [!TIP]
      > Aktualizacja wersji programu Visual Studio 2017 jest zbiorcza, więc zawsze należy wybrać opcję zainstalowania jej przy użyciu najnowszego numeru wersji.

1. Wybierz opcję **"Aktualizacja programu Visual Studio" jest dostępna**, która otwiera okno dialogowe **rozszerzenia i aktualizacje** .

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notifications-hub-select.png "Centrum powiadomień w programie Visual Studio")

1. W oknie dialogowym **rozszerzenia i aktualizacje** wybierz przycisk **Aktualizuj** .

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notifications-extensions-and-updates.png "Okno dialogowe rozszerzenia i aktualizacje w programie Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Więcej informacji na temat powiadomienia programu Visual Studio

Program Visual Studio powiadamia użytkownika, gdy aktualizacja jest dostępna dla programu Visual Studio lub wszystkie elementy, a także po wystąpieniu określonego zdarzenia w środowisku Visual Studio.

* Gdy flaga powiadomienia jest żółta, można zainstalować aktualizację produktu Visual Studio.
* Gdy flaga powiadomienia jest czerwona, występuje problem z licencją.
* Jeśli flaga powiadomienia jest czarny, są opcjonalne lub informacyjne wiadomości, aby zapoznać się z.

Wybierz flagę powiadomienia, aby otworzyć Centrum **powiadomień** , a następnie wybierz powiadomienia, na których chcesz wykonać działania. Lub zignorować lub odrzucić powiadomienie.

 ![Wyświetlanie opcjonalnego lub informacyjnego komunikatu w centrum powiadomień](media/notification-flag-optional.png "Opcjonalna lub informacyjna flaga powiadomienia o komunikatach w programie Visual Studio")

Jeśli zostanie wybrane ignorowanie powiadomienie, program Visual Studio przestaje pokazywania go. Jeśli chcesz zresetować listę ignorowanych powiadomień, wybierz przycisk **Ustawienia** w centrum powiadomień.

   ![Wybierz przycisk Ustawienia w centrum powiadomień, aby wyświetlić opcje powiadomień](media/vs-notifications-hub-settings-button.png "Wybierz przycisk Ustawienia w centrum powiadomień, aby wyświetlić opcje powiadomień")

### <a name="update-by-using-the-visual-studio-installer"></a>Aktualizowanie przy użyciu Instalatora programu Visual Studio

1. Otwórz Instalator programu. Być może musisz zaktualizować Instalatora przed kontynuowaniem. W takim przypadku zostanie wyświetlony monit, aby to zrobić.

   > [!NOTE]
   > Na komputerze z systemem Windows 10 można znaleźć instalatora pod literą **V** jako **Instalator programu Visual Studio**lub pod literą **M** jako **Instalator Microsoft Visual Studio**.

1. Na stronie **produkt** w instalatorze zapoznaj się z wersją programu Visual Studio, która została zainstalowana wcześniej.

1. Jeśli dostępna jest aktualizacja, zobaczysz przycisk **Aktualizuj** . (Może potrwać kilka sekund Instalatora Aby ustalić, czy dostępna jest aktualizacja.)

   Kliknij przycisk **Aktualizuj** , aby zainstalować aktualizacje.

     ![Aktualizowanie programu Visual Studio 2017 przy użyciu Instalator programu Visual Studio](media/update-visual-studio.png "Aktualizowanie programu Visual Studio przy użyciu Instalator programu Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

Zachęcamy do aktualizacji do najnowszej [wersji](/visualstudio/releases/2019/release-notes/) programu Visual Studio 2019, aby zawsze uzyskać najnowsze funkcje, poprawki i ulepszenia.

Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie. Jeśli obecnie używasz innej wersji programu Visual Studio, możesz [zainstalować wersje programu Visual Studio obok](../install/install-visual-studio-versions-side-by-side.md)siebie lub [odinstalować poprzednie wersje programu Visual Studio](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Musisz zalogować się za pomocą konta mającego uprawnienia administracyjne, aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [aktualizacja Visual Studio dla komputerów Mac](/visualstudio/mac/update).

Oto jak zaktualizować program Visual&nbsp;Studio&nbsp;2019.

## <a name="use-the-visual-studio-installer"></a>Użyj Instalatora programu Visual Studio

1. Otwórz Instalator programu.

     ![Otwórz Instalator programu Visual Studio z systemu Windows](media/vs-2019/vs-installer-windows-start.png "Otwórz Instalator programu Visual Studio")

   Może być konieczne zaktualizowanie Instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z monitami.

1. W instalatorze zapoznaj się z zainstalowaną wersją programu Visual Studio.

   Na przykład jeśli wcześniej zainstalowano program Visual&nbsp;Studio Community&nbsp;2019, a dla niego jest dostępna aktualizacja, w instalatorze zostanie wyświetlony komunikat z **aktualizacją** .

     ![Wybierz wersję programu Visual Studio 2019, którą chcesz zaktualizować](media/vs-2019/vs-installer-update-visual-studio-community.png "Wybierz wersję programu Visual Studio 2019, którą chcesz zaktualizować")

1. Wybierz pozycję **Aktualizuj** , aby zainstalować aktualizacje.

    ![Wybierz przycisk Aktualizuj, aby zainstalować aktualizacje](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Wybierz przycisk Aktualizuj, aby zainstalować aktualizacje")

1. Po zakończeniu aktualizacji może zostać wyświetlony monit o ponowne uruchomienie komputera. Jeśli tak, zrób to, a następnie uruchom program Visual Studio, jak zwykle.

   Jeśli nie zostanie wyświetlony monit o ponowne uruchomienie komputera, wybierz pozycję **Uruchom** , aby uruchomić program Visual Studio z Instalatora.

    ![Wybierz przycisk Uruchom, aby uruchomić program Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Wybierz przycisk Uruchom, aby uruchomić program Visual Studio")

## <a name="use-the-ide"></a>Używaj środowiska IDE

Możesz sprawdzić dostępność aktualizacji, a następnie zainstalować ją za pomocą paska menu lub pola wyszukiwania w programie Visual Studio 2019.

### <a name="open-visual-studio"></a>Otwórz program Visual Studio.

1. Z menu **Start** systemu Windows wybierz pozycję **Visual Studio 2019**.

    ![Otwórz program Visual Studio 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Otwórz program Visual Studio 2019 w systemie Windows")

1. W obszarze **wprowadzenie**wybierz dowolną opcję, aby otworzyć środowisko IDE.

    ![Otwórz Instalator programu Visual Studio](media/vs2019-choose-option-from-get-started.png "Otwórz Instalator programu Visual Studio")

    Zostanie otwarty program Visual Studio. W środowisku IDE zostanie wyświetlony komunikat **Aktualizacja programu Visual Studio 2019** .

    ![Komunikat "Visual Studio 2019 Update" w IDE](media/vs-2019/update-visual-studio-ide-message.png "Komunikat "Visual Studio 2019 Update" w IDE")

1. W komunikacie **Update programu Visual Studio 2019** wybierz pozycję **Wyświetl szczegóły**.

   ![Kliknij przycisk Wyświetl szczegóły w komunikacie środowiska IDE programu Visual Studio 2019](media/vs-2019/update-visual-studio-ide-view-details.png "Wybierz przycisk Wyświetl szczegóły w komunikacie aktualizacji programu Visual Studio 2019")

1. W oknie dialogowym **Aktualizuj pobrane i gotowe do zainstalowania** wybierz pozycję **Aktualizuj**.

     ![Wybierz przycisk Aktualizuj w oknie dialogowym "Aktualizuj pobrane i gotowe do zainstalowania"](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "Wybierz przycisk Aktualizuj w oknie dialogowym "Aktualizuj pobrane i gotowe do zainstalowania"")

   Program Visual Studio aktualizuje, zamyka i ponownie otwiera.

### <a name="in-visual-studio"></a>W programie Visual Studio

1. Na pasku menu wybierz **Pomoc**, a następnie wybierz polecenie **Sprawdź aktualizacje**.

     ![Wybierz pozycję "Sprawdź aktualizacje" w menu Pomoc](media/vs-2019/vs-ide-check-updates-help-menu.png "Wybierz pozycję "Sprawdź aktualizacje" w menu Pomoc")

    > [!NOTE]
    > Aby sprawdzić aktualizacje, można również użyć pola wyszukiwania w IDE. Naciśnij klawisz **Ctrl**+**Q**, wpisz "Check for Updates", a następnie wybierz odpowiedni wynik wyszukiwania.

1. W oknie dialogowym **Aktualizuj dostępne** wybierz pozycję **Aktualizuj**.

     ![Wybierz przycisk Aktualizuj w oknie dialogowym "Aktualizuj pobrane i gotowe do zainstalowania"](media/vs-2019/update-visual-studio-community-from-ide.png "Wybierz przycisk Aktualizuj w oknie dialogowym "Aktualizuj pobrane i gotowe do zainstalowania"")

   Program Visual Studio aktualizuje, zamyka i ponownie otwiera.

## <a name="use-the-notifications-hub"></a>Za pomocą Centrum powiadomień

1. W programie Visual Studio Zapisz swoją służbę.

1. Wybierz ikonę powiadomienia w prawym dolnym rogu środowiska IDE programu Visual Studio, aby otworzyć Centrum **powiadomień** .

   ![Ikona powiadomienia w środowisku IDE programu Visual Studio](media/vs-2019/notification-bar.png "Ikona powiadomienia w środowisku IDE programu Visual Studio")

1. W **centrum powiadomień**wybierz aktualizację, którą chcesz zainstalować, a następnie wybierz pozycję **Wyświetl szczegóły**.

     ![Centrum powiadomień w programie Visual Studio 2019](media/vs-2019/notification-hub-update.png "Centrum powiadomień w programie Visual Studio 2019")

      > [!TIP]
      > Aktualizacja wersji programu Visual Studio 2019 jest zbiorcza, więc zawsze należy wybrać opcję zainstalowania jej przy użyciu najnowszego numeru wersji.

1. W oknie dialogowym **Aktualizuj dostępne** wybierz pozycję **Aktualizuj**.

   Program Visual Studio aktualizuje, zamyka i ponownie otwiera.

## <a name="customize-update-settings"></a>Dostosuj ustawienia aktualizacji

Ustawienia aktualizacji w programie Visual Studio można dostosować na kilka różnych sposobów, na przykład przez zmianę trybu instalacji i wybranie opcji Pobieranie automatyczne.

Istnieją dwa tryby instalacji do wyboru:

* **Zainstaluj podczas pobierania**
* **Pobierz wszystko, a następnie zainstaluj**

Możesz również wybrać ustawienie **automatycznie Pobierz aktualizacje** , które umożliwia pobieranie aktualizacji, gdy maszyna jest w stanie bezczynności.

Oto kroki tej procedury:

1. Na pasku menu wybierz polecenie **narzędzia** > **Opcje**.

2. Rozwiń węzeł **środowisko**, a następnie wybierz pozycję **Aktualizacje produktów**.

    ![Aktualizuje ustawienia w programie Visual Studio](media/vs-2019/update-settings-options.png)

3. Wybierz tryb instalacji i opcje pobierania automatycznego dla aktualizacji programu Visual Studio.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie wersji programu Visual Studio obok siebie](install-visual-studio-versions-side-by-side.md)
* [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizowanie programu Visual Studio w punkcie odniesienia obsługi](update-servicing-baseline.md)
* [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
