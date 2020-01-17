---
title: Usuwanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak całkowicie usunąć program Visual Studio z komputera, krok po kroku.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
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
ms.openlocfilehash: b0e8c8fe10451e9e5906eabf7f4f65086d147904
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113711"
---
# <a name="remove-visual-studio"></a>Usuwanie programu Visual Studio

Jeśli wystąpił błąd krytyczny i nie można naprawić ani odinstalować programu Visual Studio, można uruchomić narzędzie `InstallCleanup.exe`, aby usunąć pliki instalacyjne i informacje o produkcie dla wszystkich zainstalowanych wystąpień programu Visual Studio 2017 lub Visual Studio 2019.

> [!WARNING]
> Użyj narzędzia InstallCleanup **tylko jako ostatniej,** Jeśli naprawa lub Dezinstalacja nie powiedzie się. To narzędzie może odinstalować funkcje z innych instalacji programu Visual Studio lub innych produktów, które mogą być również wymagane do naprawy lub ponownego zainstalowania.

## <a name="run-installcleanupexe"></a>Uruchom InstallCleanup. exe

Można użyć dowolnego z następujących przełączników wiersza polecenia za pomocą narzędzia `InstallCleanup.exe`:

| Przełącznik | Zachowanie |
| ------ | -------- |
| `-i`   | Ten przełącznik jest wartością domyślną, jeśli nie przeszedł innego przełącznika. Usuwa tylko główny katalog instalacji i informacje o produkcie. Użyj tego przełącznika, jeśli zamierzasz ponownie zainstalować tę samą wersję programu Visual Studio po uruchomieniu narzędzia `InstallCleanup.exe`. |
| `-f`   | Ten przełącznik usuwa główny katalog instalacji, informacje o produkcie i większość innych funkcji zainstalowanych poza katalogiem instalacji, które mogą być również udostępniane innym urządzeniom Visual Studio lub innym produktom. Użyj tego przełącznika, jeśli zamierzasz usunąć program Visual Studio bez konieczności jego ponownej instalacji. |

Poniżej przedstawiono sposób uruchamiania narzędzia `InstallCleanup.exe`:

1. Zamknij Instalatora programu Visual Studio.
1. Otwórz wiersz polecenia administratora. Aby otworzyć wiersz polecenia administratora, wykonaj następujące kroki:
   * Wpisz **polecenie cmd** w polu "Wpisz tutaj, aby wyszukać".
   * Kliknij prawym przyciskiem myszy **wiersz polecenia**, a następnie wybierz polecenie **Uruchom jako administrator**.
1. Wprowadź pełną ścieżkę do narzędzia `InstallCleanup.exe` i dodaj preferowany przełącznik wiersza polecenia. Domyślnie ścieżka narzędzia jest następująca:

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

   > [!NOTE]
   > Jeśli nie możesz znaleźć `InstallCleanup.exe` w katalogu Instalator programu Visual Studio, który zawsze znajduje się w `%ProgramFiles(x86)%\Microsoft Visual Studio`, Oto co należy zrobić dalej. Postępuj zgodnie z instrukcjami, aby [zainstalować program Visual Studio](install-visual-studio.md). Następnie po wyświetleniu ekranu wyboru obciążenia Zamknij okno i wykonaj ponownie kroki opisane na tej stronie.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
