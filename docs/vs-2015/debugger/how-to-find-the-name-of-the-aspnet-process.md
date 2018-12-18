---
title: 'Porady: znajdowanie nazwy procesu ASP.NET | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ad3bea47bcde0da87bd185fac132c95f26ce4b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793246"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Porada: Znajdowanie nazwy procesu ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby dołączyć do uruchomionej [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji, musisz znać nazwę [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu:  
  
- Jeśli korzystasz z usług IIS 6.0 i IIS 7.0, nazwa jest w3wp.exe.  
  
- Jeśli używasz starszej wersji programu IIS, nazwa jest aspnet_wp.exe.  
  
  Dla aplikacji skompilowanych za pomocą [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] lub nowsze wersje [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod może znajdować się w systemie plików i działała z serwera testowego WebDev.WebServer.exe. W takim przypadku należy dołączyć do WebDev.WebServer.exe zamiast [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu. Ten scenariusz dotyczy tylko debugowania lokalnego.  
  
  Starsze aplikacje ASP uruchamiane wewnątrz inetinfo.exe proces usług IIS, gdy są uruchomione w procesie.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Aby określić, czy kod projektu znajduje się na system plików lub IIS  
  
1.  W programie Visual Studio, otwórz **Eksploratora rozwiązań** Jeśli nie jest już otwarty.  
  
2.  Zaznacz górny węzeł, który zawiera nazwę aplikacji.  
  
3.  Jeśli **właściwości** tytuł okna zawiera ścieżkę do pliku, kod aplikacji znajduje się w systemie plików.  
  
     W przeciwnym razie **właściwości** tytuł okna będzie zawierać nazwę witryny sieci Web.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Można określić wersji usług IIS, w którym aplikacja jest uruchomiona  
  
1.  Znajdź **narzędzia administracyjne** i uruchomimy ją. W zależności od systemu operacyjnego, może to być ikona wewnątrz **Panelu sterowania**, lub wpis menu, który pojawia się po kliknięciu **Start**.  
  
     Windows XP **Panelu sterowania** mogą znajdować się w widoku kategorii lub widok klasyczny. W widoku kategorii, trzeba kliknąć **Przełącz na widok klasyczny** lub **wydajność i konserwacja** się **narzędzia administracyjne** ikony.  
  
2.  Z **narzędzia administracyjne**, uruchom program Internet Information Services. Zostanie wyświetlone okno dialogowe programu MMC.  
  
3.  Jeśli istnieje więcej niż jednym komputerze, na liście w okienku po lewej stronie, wybierz ten, na którym znajduje się kod aplikacji.  
  
4.  Wersja usług IIS znajduje się w **wersji** kolumny w okienku po prawej stronie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wstępne wymagania zdalne debugowanie aplikacji sieci Web](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)   
 [Przygotowywanie do debugowania ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Debugowanie aplikacji internetowych i skryptu](../debugger/debugging-web-applications-and-script.md)



