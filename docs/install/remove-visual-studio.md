---
title: Usuwanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak krok po kroku usunąć program Visual Studio z komputera.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113711"
---
# <a name="remove-visual-studio"></a>Usuwanie programu Visual Studio

Jeśli wystąpi katastrofalny błąd i nie można naprawić lub odinstalować programu Visual Studio, można uruchomić `InstallCleanup.exe` narzędzie, aby usunąć pliki instalacyjne i informacje o produkcie dla wszystkich zainstalowanych wystąpień programu Visual Studio 2017 lub Visual Studio 2019.

> [!WARNING]
> Narzędzie InstallCleanup należy używać **tylko w ostateczności,** jeśli naprawa lub odinstalowanie nie powiedzie się. To narzędzie może odinstalować funkcje z innych instalacji programu Visual Studio lub innych produktów, które następnie mogą wymagać naprawy lub ponownej instalacji.

## <a name="run-installcleanupexe"></a>Uruchom program InstallCleanup.exe

Za pomocą narzędzia można użyć jednego z następujących `InstallCleanup.exe` przełączników wiersza polecenia:

| Przełącznik | Zachowanie |
| ------ | -------- |
| `-i`   | Ten przełącznik jest domyślny, jeśli żaden inny przełącznik nie jest przekazywany. Usuwa tylko główny katalog instalacyjny i informacje o produkcie. Użyj tego przełącznika, jeśli zamierzasz ponownie zainstalować tę samą wersję programu Visual Studio po uruchomieniu `InstallCleanup.exe` narzędzia. |
| `-f`   | Ten przełącznik usuwa główny katalog instalacji, informacje o produkcie i większość innych funkcji zainstalowanych poza katalogiem instalacyjnym, które mogą być również współużytkowane innym instalacjom programu Visual Studio lub innym produktom. Użyj tego przełącznika, jeśli zamierzasz usunąć program Visual Studio bez ponownej instalacji później. |

Oto jak uruchomić `InstallCleanup.exe` narzędzie:

1. Zamknij Instalatora programu Visual Studio.
1. Otwórz wiersz polecenia administratora. Aby otworzyć wiersz polecenia administratora, wykonaj następujące czynności:
   * Wpisz **cmd** w polu "Wpisz tutaj, aby wyszukać".
   * Kliknij prawym przyciskiem myszy **wiersz polecenia**, a następnie wybierz polecenie Uruchom **jako administrator**.
1. Wprowadź pełną ścieżkę `InstallCleanup.exe` narzędzia i dodaj preferowany przełącznik wiersza polecenia. Domyślnie ścieżka narzędzia jest następująca:

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

   > [!NOTE]
   > Jeśli nie możesz `InstallCleanup.exe` znaleźć w katalogu Instalatora programu Visual Studio, który jest zawsze znajduje się w `%ProgramFiles(x86)%\Microsoft Visual Studio`, oto co zrobić dalej. Postępuj zgodnie z instrukcjami, aby [zainstalować program Visual Studio](install-visual-studio.md). Następnie po wyświetleniu ekranu wyboru obciążenia zamknij okno i wykonaj kroki opisane na tej stronie ponownie.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
