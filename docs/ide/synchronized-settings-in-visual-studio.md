---
title: Synchronizacja ustawień
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecac148e745eff956151af71a37b23f67a816f56
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388494"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Synchronizuj ustawienia programu Visual Studio na wielu komputerach

Po zalogowaniu do programu Visual Studio na wielu komputerach przy użyciu tego samego konta personalizacji, ustawienia można synchronizować między komputerami.

## <a name="synchronized-settings"></a>Zsynchronizowane ustawienia

Domyślnie zsynchronizowane są następujące ustawienia:

- Ustawienia środowiska deweloperskiego. Wybierz kolekcję ustawień przy pierwszym otwarciu programu Visual Studio, ale możesz zmienić wybór w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [ustawienia środowiska](../ide/environment-settings.md).

- Aliasy zdefiniowane przez użytkownika polecenia. Aby uzyskać więcej informacji o definiowaniu aliasów poleceń, zobacz [Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

- Układów okien zdefiniowanych przez użytkownika w **okna** > **Zarządzanie układami okien** strony.

- Następujące opcje w **narzędzia** > **opcje** strony:

   - Motyw ustawienia i menu paska wielkość liter w wyrazie na **środowiska** > **ogólne** Strona opcji.

   - Wszystkie ustawienia na **środowiska** > **czcionki i kolory** Strona opcji.

   - Wszystkie skróty klawiaturowe w **środowiska** > **klawiatury** Strona opcji.

   - Wszystkie ustawienia na **środowiska** > **karty i Windows** Strona opcji.

   - Wszystkie ustawienia na **środowiska** > **uruchamiania** Strona opcji.

   - Wszystkie ustawienia na **edytora tekstów** stronach opcji.

   - Wszystkie ustawienia na **projektanta XAML** stronach opcji.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Wyłącz zsynchronizowane ustawienia na określonym komputerze

Synchronizacja ustawień dla programu Visual Studio są włączone domyślnie. Zsynchronizowane ustawienia na komputerze, można wyłączyć, przechodząc do **narzędzia** > **opcje** > **środowiska**  >   **Konta** strony i usuwając zaznaczenie pola wyboru **synchronizację ustawień między urządzeniami po zalogowaniu do programu Visual Studio**. Na przykład jeśli nie chcesz synchronizować ustawienia programu Visual Studio na komputerze "A", zmiany ustawień na komputerze "A" nie są wyświetlane na komputerze "B" lub "C". Komputery, "B" i "C", będą w dalszym ciągu synchronizacji ze sobą, ale nie z komputera "A".

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronizacja ustawień w wersji i rodziny produktów Visual Studio

Ustawienia mogą być synchronizowane w dowolnej wersji programu Visual Studio, w tym Community edition. Ustawienia są synchronizowane dla rodziny produktów Visual Studio. Jednak każdy z tych produktów z rodziny mogą mieć własne ustawienia, które nie są udostępniane za pomocą programu Visual Studio. Na przykład ustawienia specyficzne dla jednego produktu na komputerze, który "A", są udostępniane za pomocą innego produktu na komputerze "B", ale nie za pomocą programu Visual Studio na komputerach, "A" lub "B".

## <a name="side-by-side-synchronized-settings"></a>Side-by-side zsynchronizowane ustawienia

W programie Visual Studio 2017 w wersji 15.3 lub nowszym pewne ustawienia, takie jak układ okna narzędzi nie są współdzielone przez różnych instalacje side-by-side programu Visual Studio 2017. *CurrentSettings.vssettings* w pliku *%userprofile%\Documents\Visual Studio 2017\Settings* znajduje się w folderze specyficznych dla instalacji, która jest podobna do *%localappdata%\ Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Aby korzystać z nowych ustawień specyficznych dla instalacji, należy wykonać nowej instalacji. Po wykonaniu uaktualnienia istniejącej instalacji programu Visual Studio 2017 do najnowszej aktualizacji, za pomocą istniejącej lokalizacji udostępnionej.

Jeśli obecnie korzystasz z side-by-side instalacji programu Visual Studio 2017 i chcesz używać nowej lokalizacji pliku ustawień specyficznych dla instalacji, wykonaj następujące kroki:

1. Uaktualnienie do programu Visual Studio 2017 w wersji 15.3 lub nowszej.

1. Użyj **importu/eksportu ustawień** kreatora, aby wyeksportować wszystkie istniejące ustawienia do lokalizacji poza *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* folderu.

1. Otwórz **wiersz polecenia programisty dla programu VS 2017** uaktualnionej instalacji programu Visual Studio i uruchom `devenv /resetuserdata`.

1. Uruchom program Visual Studio i zaimportuj zapisane ustawienia z wyeksportowanego pliku ustawień.

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Ustawienia środowiska](../ide/environment-settings.md)
- [Środowisko > okno dialogowe Opcje konta](reference/synchronized-settings-environment-options-dialog-box.md)
