---
title: Synchronizacja ustawień
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 107b1096f694e0dc784181eae675a0c1a2285726
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935206"
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

Synchronizacja ustawień dla programu Visual Studio są włączone domyślnie. Zsynchronizowane ustawienia na komputerze, można wyłączyć, przechodząc do **narzędzia** > **opcje** > **środowiska**  >   **Konta** strony i usuwając zaznaczenie pola wyboru **synchronizację ustawień między urządzeniami po zalogowaniu do programu Visual Studio**.

Na przykład jeśli zdecydujesz się na synchronizację ustawień programu Visual Studio na komputerze "A", zmiany ustawień na komputerze "A" nie są wyświetlane na komputerze "B" lub "C". Komputery, "B" i "C", będą w dalszym ciągu synchronizacji ze sobą, ale nie z komputera "A".

> [!NOTE]
> Jeśli nie zdecydujesz się na synchronizację ustawień przez usunięcie zaznaczenia tej opcji opcję w **narzędzia** > **opcje** > **środowiska**  >  **Kont** strony, inne wersje lub wersji programu Visual Studio, który znajduje się na tym samym komputerze nie ma wpływu. Instalacje side-by-side programu Visual Studio będzie synchronizować swoje ustawienia (o ile nie usuniesz zaznaczenie pola wyboru opcji, zbyt).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronizacja ustawień w wersji i rodziny produktów Visual Studio

Ustawienia są synchronizowane z różnych wersji i wydań programu Visual Studio *side-by-side*. Ustawienia są synchronizowane między rodziny produktów Visual Studio, w tym program Blend for Visual Studio. Jednak poszczególnych rodziny produktów mogą mieć własne ustawienia, które nie są udostępniane za pomocą programu Visual Studio. Na przykład ustawienia specyficzne dla programu Blend for Visual Studio na komputerze, który "A" nie są współdzielone z programem Visual Studio na komputerach, "A" lub "B".

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
- [Środowisko > okno dialogowe Opcje konta](reference/accounts-environment-options-dialog-box.md)
