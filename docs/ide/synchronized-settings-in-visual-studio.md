---
title: Synchronizowanie ustawień
ms.date: 12/10/2018
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f7183f20139df82d14f80ee4b57e28b4aed3a66
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566790"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Synchronizowanie ustawień programu Visual Studio na wielu komputerach

Po zalogowaniu się do programu Visual Studio na wielu komputerach przy użyciu tego samego konta personalizacji ustawienia mogą być synchronizowane między komputerami.

## <a name="synchronized-settings"></a>Zsynchronizowane ustawienia

Domyślnie synchronizowane są następujące ustawienia:

- Ustawienia programistyczne. Wybierz kolekcję ustawień przy pierwszym otwarciu programu Visual Studio, ale można zmienić zaznaczenie w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [Ustawienia środowiska](../ide/environment-settings.md).

- Aliasy poleceń zdefiniowane przez użytkownika. Aby uzyskać więcej informacji na temat definiowania aliasów poleceń, zobacz [Aliasy poleceń programu Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Układy okien zdefiniowane przez użytkownika na stronie **Zarządzanie** > **oknami w oknach.**

- Następujące opcje na stronach**Opcje** **narzędzi:** > 

  - Ustawienia wielkości liter i paska menu na stronie Opcje**ogólne** **środowiska.** > 

  - Wszystkie ustawienia **Environment** > na stronie opcji**Czcionki środowiska i Kolory.**

  - Wszystkie skróty klawiaturowe na stronie Opcje**klawiatury** **środowiska.** > 

  - Wszystkie ustawienia na kartach **środowiska** > i na stronie opcji**systemu Windows.**

  - Wszystkie ustawienia na stronie Opcje**uruchamiania** **środowiska.** > 

  - Wszystkie ustawienia na stronach opcji **Edytora tekstu,** na przykład [preferencje stylu kodu](code-styles-and-code-cleanup.md).

  - Wszystkie ustawienia na stronach opcji **projektanta XAML.**

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Wyłączanie ustawień synchronizowanych na określonym komputerze

Zsynchronizowane ustawienia programu Visual Studio są domyślnie włączone. Synchronizowane ustawienia na komputerze można wyłączyć, przechodząc na stronę**Konta** **środowiska** > **Opcje** >  **narzędzi** > i odznaczając **zaznaczanie ustawień synchronizacji na różnych urządzeniach po zalogowaniu się do programu Visual Studio**.

Na przykład, jeśli zdecydujesz się nie synchronizować ustawień programu Visual Studio na komputerze "A", wszelkie zmiany ustawień wprowadzone na komputerze "A" nie są wyświetlane na komputerze "B" lub komputerze "C". Komputery "B" i "C" będą nadal synchronizować ze sobą, ale nie z komputerem "A".

> [!NOTE]
> Jeśli nie chcesz synchronizować ustawień, odznaczając tę opcję na stronie**Konta** **środowiska** > **opcje** >  **narzędzi,** > nie ma to wpływu na inne wersje lub wersje programu Visual Studio na tym samym komputerze. Te instalacje side-by-side programu Visual Studio będą nadal synchronizować swoje ustawienia (chyba że wyczyść tę opcję).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronizowanie ustawień między produktami i wersjami rodzinnymi programu Visual Studio

Ustawienia są synchronizowane między wersjami i wersjami programu Visual Studio zainstalowanymi *obok siebie*. Ustawienia są również synchronizowane między produktami z rodziny programu Visual Studio, w tym Blend for Visual Studio. Jednak produkt rodziny może mieć własne ustawienia, które nie są współużytkowane w programie Visual Studio. Na przykład ustawienia specyficzne dla Blend for Visual Studio na komputerze "A" nie są udostępniane programowi Visual Studio na komputerach "A" lub "B".

## <a name="side-by-side-synchronized-settings"></a>Ustawienia synchronizowane obok siebie

::: moniker range="vs-2017"

Niektóre ustawienia, takie jak układ okna narzędzia nie są współużytkowane przez różne instalacje obok siebie programu Visual Studio. Plik *CurrentSettings.vssettings* w *%userprofile%\Documents\Visual Studio 2017\Settings* znajduje się w folderze specyficznym dla instalacji, który jest podobny do *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Aby użyć nowych ustawień specyficznych dla instalacji, wykonaj nową instalację. Po uaktualnieniu istniejącej instalacji programu Visual Studio używa istniejącej lokalizacji udostępnionej.

Jeśli obecnie masz instalacje obok siebie programu Visual Studio i chcesz użyć nowej lokalizacji pliku ustawień specyficznych dla instalacji, wykonaj następujące kroki:

1. Uaktualnienie do programu Visual Studio 2017 w wersji 15.3 lub nowszej.

2. Za pomocą **Kreatora importu i eksportu ustawień** można wyeksportować wszystkie istniejące ustawienia do określonej lokalizacji poza folderem *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx.*

3. Otwórz **wiersz polecenia dewelopera dla programu VS 2017** i uruchom program `devenv /resetuserdata`.

1. Otwórz program Visual Studio i zaimportuj zapisane ustawienia z wyeksportowanego pliku ustawień.

::: moniker-end

::: moniker range=">=vs-2019"

Niektóre ustawienia, takie jak układ okna narzędzia nie są współużytkowane przez różne instalacje obok siebie programu Visual Studio. Plik *CurrentSettings.vssettings* w *%userprofile%\Documents\Visual Studio 2019\Settings* znajduje się w folderze specyficznym dla instalacji, który jest podobny do *%localappdata%\Microsoft\VisualStudio\16.0_xxxxxxxx\Ustawienia*.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Resetowanie ustawień synchronizowanych

Aby zresetować wszystkie ustawienia do ustawień domyślnych, zaloguj się w programie Visual Studio, a następnie wybierz pozycję Ustawienia**importu i eksportu** **narzędzi,** > aby otworzyć **Kreatora importu i eksportu ustawień**. Wybierz **pozycję Resetuj wszystkie ustawienia,** a następnie postępuj zgodnie z pozostałymi krokami kreatora.

## <a name="see-also"></a>Zobacz też

- [Personalizowanie ide](../ide/personalizing-the-visual-studio-ide.md)
- [Ustawienia środowiska](../ide/environment-settings.md)
- [Okno dialogowe Opcje kont > środowiska](reference/accounts-environment-options-dialog-box.md)
