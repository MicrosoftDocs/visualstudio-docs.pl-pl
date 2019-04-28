---
title: Usuwanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak całkowicie usunąć program Visual Studio z komputera, krok po kroku.
ms.date: 03/30/2019
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
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e363065d96169660817a548fb97d39f09cf679c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810393"
---
# <a name="remove-visual-studio"></a>Usuwanie programu Visual Studio

Jeśli występują z powodu błędu krytycznego i nie można naprawić lub odinstalować program Visual Studio, możesz uruchomić `InstallCleanup.exe` narzędzie, aby usunąć pliki instalacyjne oraz informacje o produkcie dla wszystkich zainstalowanych wystąpień programu Visual Studio 2017 lub Visual Studio 2019 r. Uruchamianie tego narzędzia ma być przeprowadzane tylko w ostateczności jeśli napraw lub odinstaluj kończyć się niepowodzeniem i może odinstalować funkcji z inne instalacje programu Visual Studio lub innych produktów, które następnie może także zajść potrzeba naprawy.

W poniższych instrukcjach można uruchomić narzędzie z różnych przełączników wiersza polecenia przy użyciu następujące zachowanie:

| Przełącznik | Zachowanie |
| ------ | -------- |
| `-i`   | Ten przełącznik jest domyślna Jeżeli przełączników nie są przekazywane i usuwa tylko instalacja głównego katalogu i informacje o produkcie. To zachowanie jest preferowana, jeśli zamierzasz zainstalować ponownie tę samą wersję, po uruchomieniu `InstallCleanup.exe` narzędzia. |
| `-f`   | Określenie tego przełącznika spowoduje usunięcie katalogu głównym instalacji, informacje o produkcie i większości innych funkcji zainstalowane poza katalogiem instalacji, która może być współużytkowana z inne instalacje programu Visual Studio lub innych produktów. To zachowanie jest preferowana, jeśli zamierzasz usunąć program Visual Studio bez ponownej instalacji później. |

1. Zamknij Instalatora programu Visual Studio.
2. Otwórz wiersz polecenia administratora. Aby otworzyć wiersz polecenia administratora, wykonaj następujące kroki:
   * Typ **cmd** w polu "Wpisz tutaj, aby wyszukać".
   * Kliknij prawym przyciskiem myszy pozycję **Wiersz polecenia**, a następnie kliknij polecenie **Uruchom jako administrator**.
3. Wpisz pełną ścieżkę `InstallCleanup.exe` narzędzia i niezależnie od przełącznika wiersza polecenia, które chcesz przekazać. Domyślnie ścieżkę narzędzia jest następująca:

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Jeśli nie znajdziesz `InstallCleanup.exe` katalogu Instalatora programu Visual Studio — zawsze znajdujący się w `%ProgramFiles(x86)%\Microsoft Visual Studio` -postępuj zgodnie z instrukcjami, aby [instalacji programu Visual Studio](install-visual-studio.md) i po wyświetleniu ekranu wyboru obciążenia Zamknij okna i wykonaj poprzednie kroki ponownie.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
