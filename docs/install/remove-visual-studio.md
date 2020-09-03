---
title: Usuń program Visual Studio
titleSuffix: ''
description: Dowiedz się, jak całkowicie usunąć program Visual Studio z komputera, krok po kroku.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b26e837ec2c4155c1be0b3639368c4315d2aecd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85418928"
---
# <a name="remove-visual-studio"></a>Usuń program Visual Studio

Jeśli wystąpił błąd krytyczny i nie można naprawić ani odinstalować programu Visual Studio, można uruchomić `InstallCleanup.exe` Narzędzie w celu usunięcia plików instalacyjnych i informacji o produkcie dla wszystkich zainstalowanych wystąpień programu Visual studio 2017 lub Visual studio 2019.

> [!WARNING]
> Użyj narzędzia InstallCleanup **tylko jako ostatniej,** Jeśli naprawa lub Dezinstalacja nie powiedzie się. To narzędzie może odinstalować funkcje z innych instalacji programu Visual Studio lub innych produktów, które mogą być również wymagane do naprawy lub ponownego zainstalowania.

## <a name="run-installcleanupexe"></a>Uruchom InstallCleanup.exe

Za pomocą narzędzia można użyć dowolnego z następujących przełączników wiersza polecenia `InstallCleanup.exe` :

| Przełącznik | Zachowanie |
| ------ | -------- |
| `-i`   | Ten przełącznik jest wartością domyślną, jeśli nie przeszedł innego przełącznika. Usuwa tylko główny katalog instalacji i informacje o produkcie. Użyj tego przełącznika, jeśli zamierzasz ponownie zainstalować tę samą wersję programu Visual Studio po uruchomieniu `InstallCleanup.exe` Narzędzia. |
| `-f`   | Ten przełącznik usuwa główny katalog instalacji, informacje o produkcie i większość innych funkcji zainstalowanych poza katalogiem instalacji, które mogą być również udostępniane innym urządzeniom Visual Studio lub innym produktom. Użyj tego przełącznika, jeśli zamierzasz usunąć program Visual Studio bez konieczności jego ponownej instalacji. |

Oto jak uruchomić `InstallCleanup.exe` Narzędzie:

1. Zamknij Instalatora programu Visual Studio.
1. Otwórz wiersz polecenia administratora. Aby otworzyć wiersz polecenia administratora, wykonaj następujące czynności:
   * Wpisz **polecenie cmd** w polu "Wpisz tutaj, aby wyszukać".
   * Kliknij prawym przyciskiem myszy **wiersz polecenia**, a następnie wybierz polecenie **Uruchom jako administrator**.
1. Wprowadź pełną ścieżkę do `InstallCleanup.exe` Narzędzia i dodaj preferowany przełącznik wiersza polecenia. Domyślnie ścieżka narzędzia jest następująca. Podwójne cudzysłowy zakrywają polecenie zawierające spacje:

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Jeśli nie możesz znaleźć `InstallCleanup.exe` w katalogu Instalator programu Visual Studio, który zawsze znajduje się w sekcji `%ProgramFiles(x86)%\Microsoft Visual Studio` , należy wykonać poniższe czynności. Postępuj zgodnie z instrukcjami, aby [zainstalować program Visual Studio](install-visual-studio.md). Następnie po wyświetleniu ekranu wyboru obciążenia Zamknij okno i wykonaj ponownie kroki opisane na tej stronie.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
