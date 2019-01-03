---
title: Usuwanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak całkowicie usunąć program Visual Studio z komputera, krok po kroku.
ms.date: 09/12/2017
ms.custom: seodec18
ms.prod: visual-studio-dev15
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
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26d29ccf0bfa834ec7581fea11a606ce0558cf74
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985670"
---
# <a name="remove-visual-studio-2017"></a>Usuń program Visual Studio 2017

Jeśli występują z powodu błędu krytycznego i nie można naprawić lub odinstalować program Visual Studio, możesz uruchomić `InstallCleanup.exe` narzędzie, aby usunąć pliki instalacyjne oraz informacje o produkcie dla wszystkich zainstalowanych wystąpień programu Visual Studio 2017 i nowszych. Uruchamianie tego narzędzia ma zostać wykonane w ostateczności, jeśli napraw lub odinstaluj kończyć się niepowodzeniem i może odinstalować funkcji z inne instalacje programu Visual Studio lub innych produktów, które będą musiały zostać naprawiony.

W poniższych instrukcjach można uruchomić narzędzie z różnych przełączników wiersza polecenia przy użyciu następujące zachowanie:

| Przełącznik | Zachowanie |
| ------ | -------- |
| `-i`   | Ten przełącznik jest domyślna Jeżeli przełączników nie są przekazywane i usuwa tylko instalacja głównego katalogu i informacje o produkcie. To zachowanie jest preferowana, jeśli zamierzasz zainstalować ponownie tę samą wersję, po uruchomieniu `InstallCleanup.exe` narzędzia. |
| `-f`   | Określenie tego przełącznika spowoduje usunięcie katalogu głównym instalacji, informacje o produkcie i większości innych funkcji zainstalowane poza katalogiem instalacji, która może być współużytkowana z inne instalacje programu Visual Studio lub innych produktów. To zachowanie jest preferowana, jeśli zamierzasz usunąć program Visual Studio bez ponownej instalacji później. |

1. Zamknij Instalatora programu Visual Studio.
2. Otwórz wiersz polecenia administratora. Aby otworzyć wiersz polecenia administratora, wykonaj następujące kroki:
   * Kliknij przycisk **Start** menu
   * Typ **cmd**.
   * Kliknij prawym przyciskiem myszy pozycję **Wiersz polecenia**, a następnie kliknij polecenie **Uruchom jako administrator**.
3. Wpisz pełną ścieżkę `InstallCleanup.exe` narzędzia i niezależnie od przełącznika wiersza polecenia, które chcesz przekazać. Domyślnie ścieżkę narzędzia jest następująca:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Jeśli nie znajdziesz `InstallCleanup.exe` katalogu Instalatora programu Visual Studio — zawsze znajdujący się w `%ProgramFiles(x86)%\Microsoft Visual Studio` -postępuj zgodnie z instrukcjami, aby [instalacji programu Visual Studio](install-visual-studio.md) i po wyświetleniu ekranu wyboru obciążenia Zamknij okna i wykonaj poprzednie kroki ponownie.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio 2017](install-visual-studio.md)
* [Update Visual Studio 2017](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio 2017](modify-visual-studio.md)
* [Odinstaluj program Visual Studio 2017](uninstall-visual-studio.md)
