---
title: Aktualizowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zaktualizować program Visual Studio do najnowszej wersji, krok po kroku.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a64256f44e9de5bbfd9e65dd6410b9911aaf5075
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997694"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Aktualizacja programu Visual Studio do najnowszej wersji

::: moniker range="vs-2017"

Firma Microsoft zachęca do aktualizacji do maksymalnie [najnowszej wersji](/visualstudio/releasenotes/vs2017-relnotes/) programu Visual Studio 2017, tak aby zawsze uzyskać najnowsze funkcje, poprawki i udoskonalenia.

A jeśli chcesz wypróbować następnej wersji, należy wziąć pod uwagę pobieranie [w wersji Release candidate](//visualstudio/releases/2019/release-notes/) programu Visual Studio 2019 r, zbyt.

> [!IMPORTANT]
> Musisz zalogować się za pomocą konta mającego uprawnienia administracyjne, aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [zaktualizować program Visual Studio dla komputerów Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Aktualizacja programu Visual Studio 2017 w wersji 15.6 lub nowszej

Firma Microsoft usprawniliśmy instalacji i zaktualizować środowisko, aby ułatwić do użycia bezpośrednio z poziomu środowiska IDE. Poniżej przedstawiono sposób aktualizacji z wersji 15.6 i nowszych do nowszej wersji programu Visual Studio.

### <a name="using-the-notifications-hub"></a>Za pomocą Centrum powiadomień

W przypadku aktualizacji ma odpowiedni Flaga powiadomienia w programie Visual Studio.

1. Zapisz swoją pracę.

1. Wybierz flagę powiadomienia, aby otworzyć **powiadomienia** koncentratora, a następnie wybierz aktualizację, którą chcesz zainstalować.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/vs-install-notifications-hub-15dot6.png "Centrum powiadomień w programie Visual Studio 2017")

      > [!TIP]
      > Jest zbiorcza aktualizacja dla wersji programu Visual Studio 2017, dlatego zawsze chce zainstalować jedną z najbardziej aktualną numerem wersji.

1. Gdy **aktualizacji** zostanie otwarte okno dialogowe, wybierz polecenie **Aktualizuj teraz**.

    ![Aktualizowanie programu Visual Studio 2017 przy użyciu okno dialogowe aktualizacji w Centrum powiadomień](media/vs-update-now-from-notifications-hub.png "okno dialogowe aktualizacji w Centrum powiadomień w programie Visual Studio")

     Jeśli zostanie otwarte okno dialogowe User Access Control, wybierz opcję **tak**. Następnie okno dialogowe "Proszę czekać" może zostać otwarta przez chwilę, a następnie Instalatora programu Visual Studio otwiera, aby rozpocząć aktualizację.

     ![Nowe środowisko Instalatora programu Visual Studio w wersji 15.6](media/visual-studio-15dot6-installer.png "nowe środowisko Instalatora programu Visual Studio w wersji 15.6")

     Nadal aktualizacji. Po zakończeniu, ponowne uruchomienie programu Visual Studio.

     > [!NOTE]
     > Po uruchomieniu programu Visual Studio w trybie administratora, należy ręcznie ponownie uruchomić Visual Studio po aktualizacji.

### <a name="using-the-ide"></a>Używanie IDE

Możesz sprawdzić dostępność aktualizacji i zainstalować aktualizację na pasku menu w programie Visual Studio.

1. Zapisz swoją pracę.

1. Wybierz **pomocy** > **sprawdzać dostępność aktualizacji**.

     ![Nowy w menu Pomoc programu Visual Studio w wersji 15.6](media/vs-help-menu-check-for-updates.png "nowy w menu Pomoc programu Visual Studio w wersji 15.6")

1. Gdy **aktualizacji** zostanie otwarte okno dialogowe, wybierz polecenie **Aktualizuj teraz**.

   Aktualizacja będzie kontynuowana zgodnie z opisem w poprzedniej sekcji, a następnie programu Visual Studio zostanie ponownie uruchomiony po pomyślnym ukończeniu aktualizacji.

   > [!NOTE]
   > Po uruchomieniu programu Visual Studio w trybie administratora, należy ręcznie ponownie uruchomić Visual Studio po aktualizacji.

### <a name="using-the-visual-studio-installer"></a>Za pomocą Instalatora programu Visual Studio

Jak w starszych wersjach programu Visual Studio można użyć Instalatora programu Visual Studio do zainstalowania aktualizacji.

1. Zapisz swoją pracę.

1. Otwórz Instalator programu. Instalator programu Visual Studio może wymagać aktualizacji przed kontynuowaniem.

   > [!NOTE]
   > Na komputerze z systemem Windows 10, możesz znaleźć Instalatora w obszarze list **V** jako **Instalatora programu Visual Studio**, lub na podstawie litery **M** jako  **Instalator programu Microsoft Visual Studio**.

1. Na **produktu** stronie w Instalatorze, poszukaj wersji programu Visual Studio, która została zainstalowana.

1. Jeśli aktualizacja jest dostępna, zostanie wyświetlony **aktualizacji** przycisku. (Może potrwać kilka sekund Instalatora Aby ustalić, czy dostępna jest aktualizacja.)

   Wybierz **aktualizacji** przycisk, aby zainstalować aktualizacje.

     ![Aktualizowanie programu Visual Studio 2017 przy użyciu Instalatora programu Visual Studio](media/update-visual-studio.png "aktualizacji programu Visual Studio 2017 przy użyciu Instalatora programu Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Aktualizacja programu Visual Studio 2017 w wersji 15.5 lub starszej

Jeśli używasz starszej wersji, poniżej przedstawiono sposób stosowania aktualizacji w programie Visual Studio 2017 wersja 15.0 za pośrednictwem wersji 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Aktualizowanie za pomocą Centrum powiadomień

1. Gdy są dostępne aktualizacje, brak odpowiednich Flaga powiadomienia w programie Visual Studio.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notification-flag.png "aktualizacji Flaga powiadomienia w programie Visual Studio")

   Wybierz flagę powiadomienia, aby otworzyć **powiadomienia** koncentratora.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notifications-hub.png "Centrum powiadomień w programie Visual Studio")

      > [!TIP]
      > Jest zbiorcza aktualizacja dla wersji programu Visual Studio 2017, dlatego zawsze chce zainstalować jedną z najbardziej aktualną numerem wersji.

1. Wybierz **"Visual Studio Update" jest dostępna**, co spowoduje otwarcie **rozszerzenia i aktualizacje** okno dialogowe.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notifications-hub-select.png "Centrum powiadomień w programie Visual Studio")

1. W **rozszerzenia i aktualizacje** okna dialogowego wybierz **aktualizacji** przycisku.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notifications-extensions-and-updates.png "dialogowym rozszerzenia i aktualizacje w programie Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Więcej informacji na temat powiadomienia programu Visual Studio

Program Visual Studio powiadamia użytkownika, gdy aktualizacja jest dostępna dla programu Visual Studio lub wszystkie elementy, a także po wystąpieniu określonego zdarzenia w środowisku Visual Studio.

* Gdy Flaga powiadomienia jest żółty, Brak dostępnej aktualizacji produktu Visual Studio do zainstalowania.
* Gdy Flaga powiadomienia jest czerwony, istnieje problem z licencją.
* Jeśli flaga powiadomienia jest czarny, są opcjonalne lub informacyjne wiadomości, aby zapoznać się z.

Wybierz flagę powiadomienia, aby otworzyć **powiadomienia** koncentratora, a następnie wybierz powiadomienia, które działają na. Lub zignorować lub odrzucić powiadomienie.

 ![Wyświetl wiadomości opcjonalne lub informacyjną w Centrum powiadomień](media/notification-flag-optional.png "opcjonalne lub informacyjne wiadomości Flaga powiadomienia w programie Visual Studio")

Jeśli zostanie wybrane ignorowanie powiadomienie, program Visual Studio przestaje pokazywania go. Jeśli chcesz zresetować listę ignorowanych powiadomień, wybierz opcję **ustawienia** przycisku w Centrum powiadomień.

   ![Kliknij przycisk Ustawienia w Centrum powiadomień, aby wyświetlić opcje powiadamiania](media/vs-notifications-hub-settings-button.png "kliknij przycisk Ustawienia w Centrum powiadomień, aby wyświetlić opcje powiadamiania")

### <a name="update-by-using-the-visual-studio-installer"></a>Aktualizowanie przy użyciu Instalatora programu Visual Studio

1. Otwórz Instalator programu. Być może musisz zaktualizować Instalatora przed kontynuowaniem. Jeśli jest to możliwe, są zostanie wyświetlony monit, aby to zrobić.

   > [!NOTE]
   > Na komputerze z systemem Windows 10, możesz znaleźć Instalatora w obszarze list **V** jako **Instalatora programu Visual Studio**, lub na podstawie litery **M** jako  **Instalator programu Microsoft Visual Studio**.

1. Na **produktu** stronie w Instalatorze, poszukaj wersji programu Visual Studio, która została zainstalowana.

1. Jeśli aktualizacja jest dostępna, zostanie wyświetlony **aktualizacji** przycisku. (Może potrwać kilka sekund Instalatora Aby ustalić, czy dostępna jest aktualizacja.)

   Wybierz **aktualizacji** przycisk, aby zainstalować aktualizacje.

     ![Aktualizowanie programu Visual Studio 2017 przy użyciu Instalatora programu Visual Studio](media/update-visual-studio.png "zaktualizować program Visual Studio za pomocą Instalatora programu Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

Firma Microsoft zachęca do aktualizacji do maksymalnie [najnowszej wersji](/visualstudio/releases/2019/release-notes/) programu Visual Studio 2019 r, tak aby zawsze uzyskać najnowsze funkcje, poprawki i udoskonalenia.

> [!IMPORTANT]
> Musisz zalogować się za pomocą konta mającego uprawnienia administracyjne, aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [zaktualizować program Visual Studio dla komputerów Mac](/visualstudio/mac/update).

Poniżej przedstawiono sposób aktualizacji Visual&nbsp;Studio&nbsp;2019&nbsp;(wersja zapoznawcza) lub wizualizacji&nbsp;Studio&nbsp;2019&nbsp;RC.

## <a name="use-the-visual-studio-installer"></a>Użyj Instalatora programu Visual Studio

1. Otwórz Instalator programu.

     ![Otwórz Instalator programu Visual Studio](media/vs2019-visual-studio-installer.png "Otwórz Instalatora programu Visual Studio")

   Trzeba zaktualizować Instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z monitami.

1. W oknie Instalatora poszukaj wersji programu Visual Studio, który został zainstalowany.

   Na przykład, jeśli wcześniej zainstalowano Visual&nbsp;Studio Community&nbsp;2019&nbsp;RC i tam jest aktualizacja dla niego, a następnie wiadomość **dostępna aktualizacja** w Instalatorze zostanie wyświetlony komunikat.

     ![Wybierz wersję programu Visual Studio 2019, który chcesz zaktualizować](media/vs2019-update-visual-studio-community-rc.png "wybierz wersję programu Visual Studio 2019, który chcesz zaktualizować")

1. Wybierz **aktualizacji** do zainstalowania aktualizacji.

    ![Wybierz przycisk Aktualizuj, aby zainstalować aktualizacje](media/vs2019-choose-update-visual-studio-community-rc.png "wybierz przycisk Aktualizuj, aby zainstalować aktualizacje")

1. Po zakończeniu aktualizacji wybierz **Uruchom** do uruchamiania programu Visual Studio.

    ![Wybierz przycisk Uruchom, aby uruchomić program Visual Studio](media/vs2019-choose-launch-visual-studio-community-rc.png "wybierz przycisk Uruchom, aby uruchomić program Visual Studio")

## <a name="use-the-ide"></a>Używaj środowiska IDE

Można sprawdzić dostępność aktualizacji, a następnie zainstaluj go przy użyciu paska menu lub pola wyszukiwania w programie Visual Studio 2019 r.

### <a name="open-visual-studio"></a>Open Visual Studio

1. Od Windows **Start** menu, wybierz **Visual Studio 2019**.

    ![Otwórz program Visual Studio RC 2019](media/vs2019-visual-studio-rc.png "Otwórz program Visual Studio 2019 r z Windows")

1. W obszarze **wprowadzenie**, wybierz dowolną opcję, aby otworzyć środowiska IDE.

    ![Otwórz Instalator programu Visual Studio](media/vs2019-choose-option-from-get-started.png "Otwórz Instalatora programu Visual Studio")

    Zostanie otwarty program Visual Studio. W środowisku IDE programu **aktualizacji programu Visual Studio 2019** zostanie wyświetlony komunikat.

    ![Komunikat "Aktualizacja Visual Studio 2019 r" w środowisku IDE](media/vs2019-update-visual-studio-ide-message.png "komunikat \"Aktualizacja Visual Studio 2019 r\" w środowisku IDE")

1. W **aktualizacji programu Visual Studio 2019** komunikatu, wybierz polecenie **wyświetlić szczegóły**.

   ![Wybierz przycisk Wyświetl szczegóły w komunikacie o aktualizacji Visual Studio 2019 IDE](media/vs2019-update-visual-studio-ide-view-details.png "kliknij przycisk Wyświetl szczegóły w komunikacie aktualizacji programu Visual Studio 2019 r.")

1. W **aktualizacji pobrane i gotowe do zainstalowania** okna dialogowego wybierz **aktualizacji**.

     ![Wybierz przycisk Aktualizuj w oknie dialogowym "Pobrane i gotowe do zainstalowania aktualizacji"](media/vs2019-update-visual-studio-community-rc-from-ide.png "wybierz przycisk Aktualizuj w oknie dialogowym \"Pobrane i gotowe do zainstalowania aktualizacji\"")

   Visual Studio aktualizacji zostanie zamknięty, a następnie ponownie otworzy.

### <a name="in-visual-studio"></a>In Visual Studio

1. Na pasku menu wybierz **pomocy**, a następnie wybierz **sprawdzać dostępność aktualizacji**.

     ![Wybierz pozycję "Sprawdź aktualizacje" w menu Pomoc](media/vs-2019/vs-ide-check-updates-help-menu.png "wybierz pozycję \"Sprawdź aktualizacje\" w menu Pomoc")

    > [!NOTE]
    > Pole wyszukiwania w środowisku IDE umożliwia również sprawdzać dostępność aktualizacji. Naciśnij klawisz **Ctrl**+**Q**, wpisz "Sprawdź aktualizacje", a następnie wybierz wynik wyszukiwania, który jest zgodny.

1. W **aktualizacji pobrane i gotowe do zainstalowania** okna dialogowego wybierz **aktualizacji**.

     ![Wybierz przycisk Aktualizuj w oknie dialogowym "Pobrane i gotowe do zainstalowania aktualizacji"](media/vs2019-update-visual-studio-community-rc-from-ide.png "wybierz przycisk Aktualizuj w oknie dialogowym \"Pobrane i gotowe do zainstalowania aktualizacji\"")

   Visual Studio aktualizacji zostanie zamknięty, a następnie ponownie otworzy.

## <a name="use-the-notifications-hub"></a>Za pomocą Centrum powiadomień

1. W programie Visual Studio należy zapisać swoją pracę.

1. Wybierz ikonę powiadomienia w prawym dolnym rogu programu Visual Studio IDE, aby otworzyć **powiadomienia** koncentratora.

   ![Ikony powiadomień w środowisku IDE programu Visual Studio](media/vs-2019/notification-bar.png "ikonę powiadomienia w środowisku IDE programu Visual Studio")

1. W **Centrum powiadomień**, wybierz aktualizację, którą chcesz zainstalować, a następnie wybierz **wyświetlić szczegóły**.

     ![Centrum powiadomień w programie Visual Studio 2019](media/vs-2019/notification-hub-update.png "Centrum powiadomień w programie Visual Studio 2019 r.")

      > [!TIP]
      > Jest zbiorcza aktualizacja dla wersji programu Visual Studio 2019 r, dlatego zawsze chce zainstalować jedną z najbardziej aktualną numerem wersji.

1. W **aktualizacji pobrane i gotowe do zainstalowania** okna dialogowego wybierz **aktualizacji**.

   Visual Studio aktualizacji zostanie zamknięty, a następnie ponownie otworzy.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizacja programu Visual Studio dla komputerów Mac](/visualstudio/mac/update)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
