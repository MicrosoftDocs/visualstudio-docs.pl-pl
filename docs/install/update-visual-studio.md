---
title: Aktualizowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zaktualizować program Visual Studio do najnowszej wersji, krok po kroku.
ms.date: 04/23/2018
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- update Visual Studio
- change visual studio
- changing Visual Studio
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8e972c86f4a3dfecdcd36d2aec768e0ea3b0065
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953961"
---
# <a name="update-visual-studio-2017-to-the-most-recent-release"></a>Aktualizacja programu Visual Studio 2017 do najnowszej wersji

Firma Microsoft zachęca do aktualizacji do maksymalnie [najnowszej wersji](/visualstudio/releasenotes/vs2017-relnotes) programu Visual Studio 2017, tak aby zawsze uzyskać najnowsze funkcje, poprawki i udoskonalenia.

A jeśli chcesz wypróbować wszystko przed wydajemy nowe wersje, należy wziąć pod uwagę pobieranie [wersji zapoznawczej](/visualstudio/releasenotes/vs2017-preview-relnotes) następnej wersji zbyt.

> [!IMPORTANT]
> Musisz zalogować się za pomocą konta mającego uprawnienia administracyjne, aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](../ide/user-permissions-and-visual-studio.md).

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [zaktualizować program Visual Studio dla komputerów Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Aktualizacja programu Visual Studio 2017 w wersji 15.6 lub nowszej

Firma Microsoft usprawniliśmy instalacji i zaktualizować środowisko, aby ułatwić do użycia bezpośrednio z poziomu środowiska IDE. Poniżej przedstawiono sposób aktualizacji z wersji 15.6 i nowszych do nowszej wersji programu Visual Studio.

### <a name="use-the-notifications-hub"></a>Za pomocą Centrum powiadomień

W przypadku aktualizacji ma odpowiedni Flaga powiadomienia w programie Visual Studio.

1. Zapisz swoją pracę.

2. Wybierz flagę powiadomienia, aby otworzyć **powiadomienia** koncentratora, a następnie wybierz aktualizację, którą chcesz zainstalować.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/vs-install-notifications-hub-15dot6.png "Centrum powiadomień w programie Visual Studio 2017")

3. Gdy **aktualizacji** zostanie otwarte okno dialogowe, wybierz polecenie **Aktualizuj teraz**.

    ![Aktualizowanie programu Visual Studio 2017 przy użyciu okno dialogowe aktualizacji w Centrum powiadomień](media/vs-update-now-from-notifications-hub.png "okno dialogowe aktualizacji w Centrum powiadomień w programie Visual Studio")

     Jeśli zostanie otwarte okno dialogowe User Access Control, wybierz opcję **tak**. Następnie okno dialogowe "Proszę czekać" może zostać otwarta przez chwilę, a następnie Instalatora programu Visual Studio otwiera, aby rozpocząć aktualizację.

     ![Nowe środowisko Instalatora programu Visual Studio w wersji 15.6](media/visual-studio-15dot6-installer.png "nowe środowisko Instalatora programu Visual Studio w wersji 15.6")

     Nadal aktualizacji. Po zakończeniu, ponowne uruchomienie programu Visual Studio.

     > [!NOTE]
     > Po uruchomieniu programu Visual Studio w trybie administratora, należy ręcznie ponownie uruchomić Visual Studio po aktualizacji.

### <a name="use-the-ide"></a>Używaj środowiska IDE

Możesz sprawdzić dostępność aktualizacji i zainstalować aktualizację na pasku menu w programie Visual Studio.

1. Zapisz swoją pracę.

2. Wybierz **pomocy** > **sprawdzać dostępność aktualizacji**.

     ![Nowy w menu Pomoc programu Visual Studio w wersji 15.6](media/vs-help-menu-check-for-updates.png "nowy w menu Pomoc programu Visual Studio w wersji 15.6")

3. Gdy **aktualizacji** zostanie otwarte okno dialogowe, wybierz polecenie **Aktualizuj teraz**.

   Aktualizacja będzie kontynuowana zgodnie z opisem w poprzedniej sekcji, a następnie programu Visual Studio zostanie ponownie uruchomiony po pomyślnym ukończeniu aktualizacji.

   > [!NOTE]
   > Po uruchomieniu programu Visual Studio w trybie administratora, należy ręcznie ponownie uruchomić Visual Studio po aktualizacji.

### <a name="use-the-visual-studio-installer"></a>Użyj Instalatora programu Visual Studio

Jak w starszych wersjach programu Visual Studio 2017 można użyć Instalatora programu Visual Studio do zainstalowania aktualizacji.

1. Zapisz swoją pracę.

2. Otwórz Instalator programu. Instalator programu Visual Studio może wymagać aktualizacji przed kontynuowaniem.

   > [!NOTE]
   > Na komputerze z systemem Windows 10, możesz znaleźć Instalatora w obszarze list **V** jako **Instalatora programu Visual Studio**, lub na podstawie litery **M** jako  **Instalator programu Microsoft Visual Studio**.

3. Na **produktu** stronie w Instalatorze, poszukaj wersji programu Visual Studio, która została zainstalowana.

4. Jeśli aktualizacja jest dostępna, zostanie wyświetlony **aktualizacji** przycisku. (Może potrwać kilka sekund Instalatora Aby ustalić, czy dostępna jest aktualizacja.)

   Wybierz **aktualizacji** przycisk, aby zainstalować aktualizacje.

     ![Aktualizowanie programu Visual Studio 2017 przy użyciu Instalatora programu Visual Studio](media/update-visual-studio.png "aktualizacji programu Visual Studio 2017 przy użyciu Instalatora programu Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Aktualizacja programu Visual Studio 2017 w wersji 15.5 lub starszej

Jeśli używasz starszej wersji, poniżej przedstawiono sposób stosowania aktualizacji w programie Visual Studio 2017 wersja 15.0 za pośrednictwem wersji 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Aktualizowanie za pomocą Centrum powiadomień

1. Gdy są dostępne aktualizacje, brak odpowiednich Flaga powiadomienia w programie Visual Studio.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notification-flag.png "aktualizacji Flaga powiadomienia w programie Visual Studio")

   Wybierz flagę powiadomienia, aby otworzyć **powiadomienia** koncentratora.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notifications-hub.png "Centrum powiadomień w programie Visual Studio")

2. Wybierz **"Visual Studio Update" jest dostępna**, co spowoduje otwarcie **rozszerzenia i aktualizacje** okno dialogowe.

   ![Aktualizowanie programu Visual Studio 2017 przy użyciu Centrum powiadomień](media/notifications-hub-select.png "Centrum powiadomień w programie Visual Studio")

3. W **rozszerzenia i aktualizacje** okna dialogowego wybierz **aktualizacji** przycisku.

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

2. Na **produktu** stronie w Instalatorze, poszukaj wersji programu Visual Studio, która została zainstalowana.

3. Jeśli aktualizacja jest dostępna, zostanie wyświetlony **aktualizacji** przycisku. (Może potrwać kilka sekund Instalatora Aby ustalić, czy dostępna jest aktualizacja.)

   Wybierz **aktualizacji** przycisk, aby zainstalować aktualizacje.

     ![Aktualizowanie programu Visual Studio 2017 przy użyciu Instalatora programu Visual Studio](media/update-visual-studio.png "aktualizacji programu Visual Studio 2017 przy użyciu Instalatora programu Visual Studio")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Modyfikowanie programu Visual Studio 2017](modify-visual-studio.md)
* [Odinstaluj program Visual Studio 2017](uninstall-visual-studio.md)
* [Aktualizacja programu Visual Studio dla komputerów Mac](/visualstudio/mac/update)