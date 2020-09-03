---
title: Wdrażanie rozszerzenia modelu warstwy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c11c952223854ff1b4b963e24615e7abe831496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669864"
---
# <a name="deploy-a-layer-model-extension"></a>Wdrażanie rozszerzenia modelu warstwy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inni użytkownicy programu Visual Studio mogą instalować rozszerzenia modelowania warstwy tworzone za pomocą programu Visual Studio.

## <a name="installing-your-extension"></a>Instalowanie rozszerzenia
 Twoje rozszerzenie jest kompilowane do pliku VSIX, który można zainstalować na innych komputerach. Można go również zainstalować na komputerze deweloperskim, aby udostępnić rozszerzenie w głównym wystąpieniu programu Visual Studio.

#### <a name="to-install-the-extension"></a>Aby zainstalować rozszerzenie

1. W projekcie zawierającym **Źródło. VSIX. manifest**, Open **bin \\ \\ *** w Eksploratorze plików.

2. Skopiuj plik ** \* . vsix** do komputera, na którym chcesz zainstalować rozszerzenie.

3. Na komputerze docelowym kliknij dwukrotnie plik *. vsix w Eksploratorze Windows.

    Zostanie otwarty Instalator VSIX.

#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenie

1. W programie Visual Studio w menu **Narzędzia** kliknij pozycję **rozszerzenia i aktualizacje**.

2. Kliknij nazwę rozszerzenia, a następnie kliknij przycisk **Odinstaluj**.

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Instalowanie rozszerzenia na serwerze Team Foundation Build
 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] na serwerach zazwyczaj nie jest zainstalowany program Visual Studio, dlatego nie można zainstalować VSIX, klikając go dwukrotnie. Instalacja programu [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] obejmuje pewne składniki, które umożliwiają uruchomienie rozszerzenia VSIX, ale rozszerzenie należy zainstalować ręcznie.

#### <a name="to-install-your-layer-extension-on-a-esprbuild-server"></a>Aby zainstalować rozszerzenie warstwy na [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] serwerze

1. Skopiuj pliki **VSIX** z komputera deweloperskiego do [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] komputera.

     Umieść plik VSIX w jednej z następujących lokalizacji:

    - Aby zainstalować dla wszystkich użytkowników i usług:

         %ProgramFiles%\Microsoft Visual Studio [wersja] \Common7\IDE\Extensions\Microsoft

    - Aby zainstalować tylko dla usługi sieciowej, która jest uruchomiona [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] :

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio \\ [wersja] \Extensions\Microsoft

    - Jeśli skonfigurowano [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] Uruchamianie programu w trybie interaktywnym jako określony użytkownik, można zainstalować tylko dla tego użytkownika:

         %LocalAppData%\Microsoft\VisualStudio \\ [wersja] \Extensions\Microsoft

        > [!NOTE]
        > % LocalAppData% jest zazwyczaj *DriveName*: Users*username*AppDataLocal.

2. Rozwiń każdy plik VSIX do folderu w tej samej lokalizacji:

    1. Zmień rozszerzenie nazwy pliku z **. vsix** na **. zip**.

    2. Wyodrębnij zawartość pliku zip do folderu.

    3. Usuń plik zip

3. Uruchom ponownie [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] .
