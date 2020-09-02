---
title: 'Instrukcje: Znajdowanie nazwy procesu ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685965"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Porada: Znajdowanie nazwy procesu ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby dołączyć do uruchomionej [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji, musisz znać nazwę [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu:  
  
- W przypadku korzystania z usług IIS 6,0 lub IIS 7,0 nazwa jest w3wp.exe.  
  
- Jeśli używasz starszej wersji usług IIS, nazwa jest aspnet_wp.exe.  
  
  W przypadku aplikacji zbudowanych przy użyciu programu [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] lub nowszych wersji [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod może znajdować się w systemie plików i działać w ramach serwera testowego WebDev.WebServer.exe. W takim przypadku należy dołączyć do WebDev.WebServer.exe zamiast [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu. Ten scenariusz dotyczy tylko debugowania lokalnego.  
  
  Starsze aplikacje ASP działają w procesie usług IIS inetinfo.exe, gdy działają w procesie.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Aby określić, czy kod projektu znajduje się w systemie plików lub usługach IIS  
  
1. W programie Visual Studio Otwórz **Eksplorator rozwiązań** , jeśli nie jest jeszcze otwarty.  
  
2. Wybierz górny węzeł, który zawiera nazwę aplikacji.  
  
3. Jeśli tytuł okna **Właściwości** zawiera ścieżkę pliku, kod aplikacji znajduje się w systemie plików.  
  
     W przeciwnym razie tytuł okna **Właściwości** będzie zawierać nazwę witryny sieci Web.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Aby określić wersję usług IIS, w której działa aplikacja  
  
1. Znajdź **Narzędzia administracyjne** i uruchom je. W zależności od używanego systemu operacyjnego może to być ikona w **Panelu sterowania**lub pozycja menu, która pojawia się po kliknięciu przycisku **Rozpocznij**.  
  
     W systemie Windows XP **Panel sterowania** może być w widoku kategorii lub widoku klasycznym. W widoku kategorii należy kliknąć pozycję **Przełącz na widok klasyczny** lub **wydajność i konserwacja** , aby wyświetlić ikonę **Narzędzia administracyjne** .  
  
2. Z poziomu **narzędzi administracyjnych**Uruchom Internet Information Services. Zostanie wyświetlone okno dialogowe programu MMC.  
  
3. Jeśli w okienku po lewej stronie znajduje się więcej niż jeden komputer, wybierz ten, na którym znajduje się kod aplikacji.  
  
4. Wersja usług IIS znajduje się w kolumnie **wersja** okienka po prawej stronie.  
  
## <a name="see-also"></a>Zobacz też  
 [Prerequistes do zdalnego debugowania aplikacji sieci Web](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)   
 [Przygotowywanie do debugowania ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Debugowanie aplikacji internetowych i skryptu](../debugger/debugging-web-applications-and-script.md)
