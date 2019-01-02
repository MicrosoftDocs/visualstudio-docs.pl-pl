---
title: Wdrażanie rozszerzenia modelu warstwy
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 8614df4c8e7b3a640f7ba488ad18384886b56afe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834311"
---
# <a name="deploy-a-layer-model-extension"></a>Wdrażanie rozszerzenia modelu warstwy

Innym użytkownikom programu Visual Studio można zainstalować warstwę modelowania rozszerzeń, które tworzysz przy użyciu programu Visual Studio.

## <a name="install-your-extension"></a>Instalowanie rozszerzenia

Rozszerzenie jest skompilowane do pliku VSIX, który można zainstalować na innych komputerach. Można także zainstalować na komputerze dewelopera, aby udostępnić rozszerzenie w głównym wystąpieniu programu Visual Studio.

### <a name="to-install-the-extension"></a>Aby zainstalować rozszerzenie

1. W projekcie, który zawiera **source.vsix.manifest**, otwórz *bin* katalogu w Eksploratorze plików.

2. Kopiuj  **\*.vsix** pliku na komputerze, na którym chcesz zainstalować rozszerzenie.

3. Na komputerze docelowym kliknij dwukrotnie plik *.vsix w Eksploratorze Windows.

    Otwiera Instalatora VSIX.

### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenie

1.  W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.

2.  Kliknij nazwę rozszerzenia, a następnie kliknij przycisk **Odinstaluj**.

## <a name="install-an-extension-on-team-foundation-server"></a>Zainstaluj rozszerzenie na serwerze Team Foundation Server

Team Foundation Server serwery zazwyczaj nie mają zainstalowanego programu Visual Studio, a więc nie można zainstalować VSIX, klikając go dwukrotnie. Trzeba ręcznie zainstalować rozszerzenie.

### <a name="to-install-your-layer-extension-on-a-team-foundation-server-server"></a>Aby zainstalować rozszerzenie warstwy na serwerze Team Foundation Server

1.  Kopiowanie. *vsix* pliki z komputera dewelopera na komputer Team Foundation Server (TFS).

     Umieść plik VSIX w jednej z następujących lokalizacji:

    -   Aby zainstalować dla wszystkich użytkowników i usług:

         %ProgramFiles%\Microsoft visual Studio [wersja] \Common7\IDE\Extensions\Microsoft

    -   Aby zainstalować tylko w przypadku usługi sieciowej, która uruchamia kompilację:

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   Jeśli skonfigurowano kompilacji do uruchamiania w trybie interakcyjnym jako określony użytkownik, można zainstalować tylko dla tego użytkownika:

         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

2.  Rozwiń każdy pliku VSIX do folderu w tej samej lokalizacji:

    1.  Zmień rozszerzenie nazwy pliku z **.vsix** do **zip**.

    2.  Wyodrębnij zawartość pliku .zip do folderu.

    3.  Usuń plik .zip.

3.  Ponowne uruchomienie serwera TFS.
