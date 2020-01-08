---
title: Synchronizuj ustawienia
ms.date: 12/10/2018
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f7183f20139df82d14f80ee4b57e28b4aed3a66
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566790"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Synchronizuj ustawienia programu Visual Studio na wielu komputerach

Po zalogowaniu się do programu Visual Studio na wielu komputerach przy użyciu tego samego konta personalizacji ustawienia można synchronizować między komputerami.

## <a name="synchronized-settings"></a>Zsynchronizowane ustawienia

Domyślnie synchronizowane są następujące ustawienia:

- Ustawienia deweloperskie. Można wybrać kolekcję ustawień przy pierwszym otwarciu programu Visual Studio, ale można zmienić zaznaczenie w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [ustawienia środowiska](../ide/environment-settings.md).

- Aliasy zdefiniowane przez użytkownika polecenia. Aby uzyskać więcej informacji o definiowaniu aliasów poleceń, zobacz [Visual Studio — Aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

- Układy okien zdefiniowane przez użytkownika w **oknie** > **Zarządzanie układami okien** .

- Następujące opcje na stronach **narzędzi** > **Opcje** :

  - Motyw i pasek menu ustawienia wielkości liter w **środowisku** > stronie opcje **Ogólne** .

  - Wszystkie ustawienia na stronie **środowisko** > opcje **czcionek i kolorów** .

  - Wszystkie skróty klawiaturowe w **środowisku** > opcje **klawiatury** .

  - Wszystkie ustawienia w **środowisku** > **kart i strony Opcje systemu Windows** .

  - Wszystkie ustawienia w **środowisku** > opcje **uruchamiania** strony.

  - Wszystkie ustawienia na stronach opcje **edytora tekstu** , na przykład [Preferencje stylu kodu](code-styles-and-code-cleanup.md).

  - Wszystkie ustawienia na stronach opcji **Projektant XAML** .

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Wyłączanie ustawień synchronizowanych na określonym komputerze

Synchronizacja ustawień dla programu Visual Studio są włączone domyślnie. Zsynchronizowane ustawienia można wyłączyć na komputerze, przechodząc do strony **narzędzia** > opcje ** >  > ** **konta** , a następnie usuwając zaznaczenie **opcji** **Synchronizuj ustawienia między urządzeniami po zalogowaniu się do programu Visual Studio**.

Na przykład jeśli zdecydujesz, że nie chcesz synchronizować ustawień programu Visual Studio na komputerze "A", wszelkie zmiany ustawień wprowadzone na komputerze "A" nie są wyświetlane na komputerze "B" lub na komputerze "C". Komputery "B" i "C" będą nadal synchronizowane ze sobą, ale nie z komputerem "A".

> [!NOTE]
> Jeśli nie zdecydujesz się synchronizować ustawień, usuń zaznaczenie opcji **na stronie** **narzędzia** > **Opcje** >  > **środowiska** , inne wersje lub wersje programu Visual Studio, które znajdują się na tym samym komputerze, nie mają wpływu na pracę. Te równoległe instalacje programu Visual Studio będą nadal synchronizować swoje ustawienia (o ile nie zostanie ponownie wybrana opcja).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronizuj ustawienia w produktach i wersjach rodziny Visual Studio

Ustawienia są synchronizowane między wersjami i wersjami programu Visual Studio zainstalowanych *obok*siebie. Ustawienia są również synchronizowane między produktami rodziny Visual Studio, w tym Blend for Visual Studio. Jednak poszczególne produkty rodzinne mogą mieć własne ustawienia, które nie są udostępniane w programie Visual Studio. Na przykład ustawienia specyficzne dla Blend for Visual Studio na komputerze "A" nie są udostępniane w programie Visual Studio na komputerach "A" lub "B".

## <a name="side-by-side-synchronized-settings"></a>Ustawienia zsynchronizowane obok siebie

::: moniker range="vs-2017"

Niektóre ustawienia, takie jak układ okna narzędzi, nie są współużytkowane przez różne instalacje równoległe programu Visual Studio. Plik *CurrentSettings. vssettings* w programie *%USERPROFILE%\Documents\Visual Studio 2017 \ Settings* znajduje się w folderze specyficznym dla instalacji podobnym do *%LocalAppData%\microsoft\visualstudio\15.0_xxxxxxxx \Settings*.

> [!NOTE]
> Aby użyć nowych ustawień specyficznych dla instalacji, należy przeprowadzić nową instalację. Po uaktualnieniu istniejącej instalacji programu Visual Studio korzysta ona z istniejącej udostępnionej lokalizacji.

Jeśli obecnie korzystasz z równoległych instalacji programu Visual Studio i chcesz użyć nowej lokalizacji pliku ustawień specyficznych dla instalacji, wykonaj następujące kroki:

1. Uaktualnij do programu Visual Studio 2017 w wersji 15,3 lub nowszej.

2. Użyj **Kreatora importowania i eksportowania ustawień** , aby wyeksportować wszystkie istniejące ustawienia do niektórych lokalizacji poza folderem *0_xxxxxxxx%LocalAppData%\microsoft\visualstudio\15.* .

3. Otwórz **wiersz polecenia dla deweloperów dla programu VS 2017** i uruchom `devenv /resetuserdata`.

1. Otwórz program Visual Studio i zaimportuj zapisane ustawienia z wyeksportowanego pliku ustawień.

::: moniker-end

::: moniker range=">=vs-2019"

Niektóre ustawienia, takie jak układ okna narzędzi, nie są współużytkowane przez różne instalacje równoległe programu Visual Studio. Plik *CurrentSettings. vssettings* w programie *%USERPROFILE%\Documents\Visual Studio 2019 \ Settings* znajduje się w folderze specyficznym dla instalacji podobnym do *%LocalAppData%\microsoft\visualstudio\16.0_xxxxxxxx \Settings*.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Resetuj zsynchronizowane ustawienia

Aby zresetować wszystkie ustawienia do wartości domyślnych, zaloguj się do programu Visual Studio, a następnie wybierz pozycję **narzędzia** > **Importuj i Eksportuj ustawienia** , aby otworzyć **Kreatora importowania i eksportowania ustawień**. Wybierz pozycję **Zresetuj wszystkie ustawienia** , a następnie postępuj zgodnie z pozostałymi krokami kreatora.

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Ustawienia środowiska](../ide/environment-settings.md)
- [Okno dialogowe Opcje kont > środowiska](reference/accounts-environment-options-dialog-box.md)
