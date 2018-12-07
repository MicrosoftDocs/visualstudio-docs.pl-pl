---
title: Uruchom proces roboczy w ramach konta użytkownika | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47aefcb73fd20dcc82b19ed6200fec5fd57dd486
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067819"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Porady: uruchamianie procesu roboczego z konta użytkownika
Aby skonfigurować komputer, dzięki czemu możesz uruchomić [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy (aspnet_wp.exe lub w3wp.exe) w ramach konta użytkownika, wykonaj następujące kroki.  

 > [!IMPORTANT]
 > Począwszy od systemu Windows Server 2008 R2, firma Microsoft zaleca użycie [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) jako tożsamość, dla każdej puli aplikacji.
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Aby uruchomić aspnet_wp.exe przy użyciu konta użytkownika  
  
1. Otwórz plik machine.config, znajduje się w folderze konfiguracji w ścieżce, gdzie zainstalowano środowisko uruchomieniowe na komputerze.  
  
2. Znajdź &lt;processModel&gt; sekcji, a następnie zmień atrybuty użytkownika i hasła na nazwę i hasło konta użytkownika, które chcesz aspnet_wp.exe uruchamiany w kontekście.  
  
3. Zapisz plik machine.config.  
  
4. Na [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)], usług IIS 6.0 jest instalowany domyślnie. Odpowiedni proces roboczy jest w3wp.exe.To uruchamiania w trybie aspnet_wp.exe jako proces roboczy usług IIS 6.0, należy wykonać następujące czynności:  
  
   1.  Kliknij przycisk **Start**, kliknij przycisk **narzędzia administracyjne** , a następnie wybierz **Internetowe usługi informacyjne**.  
  
   2.  W **Internetowe usługi informacyjne** okno dialogowe, kliknij prawym przyciskiem myszy **witryn sieci Web** folder i wybierz polecenie **właściwości**.  
  
   3.  W **właściwości witryn sieci Web** okna dialogowego wybierz **usługi**.  
  
   4.  Wybierz **Uruchom usługę WWW w trybie izolacji IIS6.0**.  
  
   5.  Zamknij **właściwości** okno dialogowe i **Menedżera internetowych usług**.  
  
5. Otwórz wiersz polecenia programu Windows i zresetuj serwera, uruchamiając:  
  
   ```cmd
   iisreset  
   ```  
   — lub —  
  
   ```cmd
   net stop iisadmin /y  
   net start w3svc  
   ```  
  
6. Znajdź tymczasowy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] folderu plików, który powinien znajdować się w tej samej ścieżce co folder konfiguracji. Kliknij prawym przyciskiem myszy tymczasowy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] folder plików, a następnie wybierz **właściwości** w menu skrótów.  
  
7. W **tymczasowe ASP.NET pliki właściwości** okno dialogowe, kliknij przycisk **zabezpieczeń** kartę.  
  
8. Kliknij przycisk **zaawansowane**.  
  
9. W **Zaawansowane ustawienia zabezpieczeń dla Temporary ASP.Net Files** okno dialogowe, kliknij przycisk **Dodaj**.  
  
    **Wybierz użytkownika, komputera lub grupy, okno dialogowe** pojawia się.  
  
10. Wpisz nazwę żądanego użytkownika w **wprowadź nazwę obiektu do wybrania** , a następnie kliknij przycisk **OK**. Nazwa użytkownika, należy wykonać następujący format: Nazwa_domeny\nazwa_użytkownika.  
  
11. W **wpis uprawnienia dla Temporary ASP.NET Files** okna dialogowego pole, przyznać użytkownikowi **Pełna kontrola**, a następnie kliknij przycisk **OK** zamknąć **wpis dla tymczasowych ASP Pliki .NET** okno dialogowe.  
  
12. A **zabezpieczeń** pojawi się okno dialogowe i pyta, jeśli na pewno chcesz zmienić uprawnienia do folderu systemu. Kliknij przycisk **Tak**.  
  
13. Kliknij przycisk **OK** zamknąć **tymczasowe ASP.NET pliki właściwości** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
[Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
[Debugowanie ASP.NET: Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)  
  
