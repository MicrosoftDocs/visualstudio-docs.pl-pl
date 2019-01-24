---
title: Wdrażanie rozszerzenia modelu warstwy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 63538797f335cab770f3748d946b08de6b44c609
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800105"
---
# <a name="deploy-a-layer-model-extension"></a>Wdrażanie rozszerzenia modelu warstwy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Innym użytkownikom programu Visual Studio można zainstalować warstwę modelowania rozszerzeń, które tworzysz przy użyciu programu Visual Studio.  
  
## <a name="installing-your-extension"></a>Instalowanie rozszerzenia  
 Rozszerzenie jest skompilowane do pliku VSIX, który można zainstalować na innych komputerach. Można także zainstalować na komputerze dewelopera, aby udostępnić rozszerzenie w głównym wystąpieniu programu Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Aby zainstalować rozszerzenie  
  
1. W projekcie, który zawiera **source.vsix.manifest**, otwórz **bin\\\\*** w Eksploratorze plików.  
  
2. Kopiuj  **\*.vsix** pliku na komputerze, na którym chcesz zainstalować rozszerzenie.  
  
3. Na komputerze docelowym kliknij dwukrotnie plik *.vsix w Eksploratorze Windows.  
  
    Otwiera Instalatora VSIX.  
  
#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenie  
  
1.  W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.  
  
2.  Kliknij nazwę rozszerzenia, a następnie kliknij przycisk **Odinstaluj**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Instalowanie rozszerzenia na serwerze kompilacji Team Foundation  
 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] serwery zwykle nie mają zainstalowanego programu Visual Studio, a więc nie można zainstalować VSIX, klikając go dwukrotnie. Instalacja [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] zawiera kilka składników, pozwalają rozszerzeniu VSIX do uruchomienia, ale należy ręcznie zainstalować rozszerzenia.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildincludesesprbuild-mdmd-server"></a>Aby zainstalować rozszerzenie warstwy na [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] serwera  
  
1.  Kopiuj **.vsix** pliki z komputera dewelopera do [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] komputera.  
  
     Umieść plik VSIX w jednej z następujących lokalizacji:  
  
    -   Aby zainstalować dla wszystkich użytkowników i usług:  
  
         %ProgramFiles%\Microsoft visual Studio [wersja] \Common7\IDE\Extensions\Microsoft  
  
    -   Aby zainstalować tylko dla usługi sieciowej, która uruchamia [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    -   Jeśli skonfigurowano [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] do uruchamiania w trybie interakcyjnym jako określony użytkownik, można zainstalować tylko dla tego użytkownika:  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
        > [!NOTE]
        >  % LocalAppData % zazwyczaj znajduje *DriveName*: Użytkownicy*UserName*AppDataLocal.  
  
2.  Rozwiń każdy pliku VSIX do folderu w tej samej lokalizacji:  
  
    1.  Zmień rozszerzenie nazwy pliku z **.vsix** do **zip**.  
  
    2.  Wyodrębnij zawartość pliku .zip do folderu.  
  
    3.  Usuń plik .zip.  
  
3.  Uruchom ponownie [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].
