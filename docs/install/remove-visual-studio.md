---
title: Usuń Visual Studio
titleSuffix: ''
description: Dowiedz się, jak Visual Studio usuwać dane z komputera krok po kroku.
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
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5af0cf31d3a53b12910ea8108c93a99cbaf3e87f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306959"
---
# <a name="remove-visual-studio"></a>Usuń Visual Studio

Jeśli wystąpi błąd krytyczny i nie można naprawić ani odinstalować programu Visual Studio, możesz uruchomić narzędzie w celu usunięcia plików instalacyjnych i informacji o produkcie dla wszystkich zainstalowanych wystąpień programu `InstallCleanup.exe` Visual Studio 2017, Visual Studio 2019 lub Visual Studio 2022.

> [!WARNING]
> Użyj narzędzia InstallCleanup **tylko w** ostateczności, jeśli naprawa lub dezinstalacja nie powiedzie się. To narzędzie może odinstalować funkcje z innych Visual Studio instalacji lub innych produktów, które następnie mogą wymagać naprawy lub ponownej instalacji.

## <a name="run-installcleanupexe"></a>Uruchom InstallCleanup.exe

Za pomocą narzędzia można użyć jednego z następujących przełączników `InstallCleanup.exe` wiersza polecenia:

| Przełącznik | Zachowanie                                                                                                                                                                                                                                                                                                                 |
|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-i`   | Ten przełącznik jest domyślny, jeśli żaden inny przełącznik nie zostanie przekazany. Usuwa tylko główny katalog instalacyjny i informacje o produkcie. Użyj tego przełącznika, jeśli zamierzasz ponownie zainstalować tę samą wersję Visual Studio po uruchomieniu `InstallCleanup.exe` narzędzia.                                                              |
| `-f`   | Ten przełącznik usuwa główny katalog instalacyjny, informacje o produkcie i większość innych funkcji zainstalowanych poza katalogiem instalacyjnym, które mogą być również udostępniane innym Visual Studio instalacji lub innych produktów. Użyj tego przełącznika, jeśli zamierzasz usunąć Visual Studio bez jego ponownej instalacji później. |

Oto jak uruchomić `InstallCleanup.exe` narzędzie:

1. Zamknij Instalatora programu Visual Studio.
1. Otwórz wiersz polecenia administratora. Aby otworzyć wiersz polecenia administratora, wykonaj następujące kroki:
   * Wpisz **cmd** w polu "Wpisz tutaj, aby wyszukać".
   * Kliknij prawym przyciskiem **myszy pozycję Wiersz polecenia,** a następnie wybierz **polecenie Uruchom jako administrator.**
1. Wprowadź pełną ścieżkę narzędzia i dodaj preferowany `InstallCleanup.exe` przełącznik wiersza polecenia. Domyślnie ścieżka narzędzia jest następująca. Cudzysłowy otaczają polecenie zawierające spacje:

   ```shell
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Jeśli nie możesz znaleźć w katalogu Instalator programu Visual Studio, który zawsze znajduje się w katalogu , oto co `InstallCleanup.exe` `%ProgramFiles(x86)%\Microsoft Visual Studio` należy zrobić dalej. Postępuj zgodnie z [instrukcjami, aby zainstalować Visual Studio](install-visual-studio.md). Następnie, gdy zostanie wyświetlony ekran wyboru obciążenia, zamknij okno i ponownie wykonaj kroki opisane na tej stronie.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
