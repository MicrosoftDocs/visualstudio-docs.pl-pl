---
title: 'Instrukcje: Uruchamianie procesu roboczego w ramach konta użytkownika | Dokumentacja firmy Microsoft'
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
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebb8ec1fe10f6fbc5c367cb0ed127e048351b0e4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105919"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Instrukcje: Uruchamianie procesu roboczego w ramach konta użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby skonfigurować komputer, dzięki czemu możesz uruchomić [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy (aspnet_wp.exe lub w3wp.exe) w ramach konta użytkownika, wykonaj następujące kroki.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Aby uruchomić aspnet_wp.exe przy użyciu konta użytkownika  
  
1. Otwórz plik machine.config, znajduje się w folderze konfiguracji w ścieżce, gdzie zainstalowano środowisko uruchomieniowe na komputerze.  
  
2. Znajdź &lt;processModel&gt; sekcji, a następnie zmień atrybuty użytkownika i hasła na nazwę i hasło konta użytkownika, które chcesz aspnet_wp.exe uruchamiany w kontekście.  
  
3. Zapisz plik machine.config.  
  
4. Na [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)], usług IIS 6.0 jest instalowany domyślnie. Odpowiedni proces roboczy jest w3wp.exe.To uruchamiania w trybie aspnet_wp.exe jako proces roboczy usług IIS 6.0, należy wykonać następujące czynności:  
  
    1. Kliknij przycisk **Start**, kliknij przycisk **narzędzia administracyjne** , a następnie wybierz **Internetowe usługi informacyjne**.  
  
    2. W **Internetowe usługi informacyjne** okno dialogowe, kliknij prawym przyciskiem myszy **witryn sieci Web** folder i wybierz polecenie **właściwości**.  
  
    3. W **właściwości witryn sieci Web** okna dialogowego wybierz **usługi**.  
  
    4. Wybierz **Uruchom usługę WWW w trybie izolacji IIS6.0**.  
  
    5. Zamknij **właściwości** okno dialogowe i **Menedżera internetowych usług**.  
  
5. Otwórz wiersz polecenia programu Windows i zresetuj serwera, uruchamiając:  
  
    ```  
    iisreset  
    ```  

    — lub —  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6. Znajdź tymczasowy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] folderu plików, który powinien znajdować się w tej samej ścieżce co folder konfiguracji. Kliknij prawym przyciskiem myszy tymczasowy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] folder plików, a następnie wybierz **właściwości** w menu skrótów.  
  
7. W **tymczasowe ASP.NET pliki właściwości** okno dialogowe, kliknij przycisk **zabezpieczeń** kartę.  
  
8. Kliknij przycisk **zaawansowane**.  
  
9. W **Zaawansowane ustawienia zabezpieczeń dla Temporary ASP.Net Files** okno dialogowe, kliknij przycisk **Dodaj**.  
  
    **Wybierz użytkownika, komputera lub grupy, okno dialogowe** pojawia się.  
  
10. Wpisz nazwę żądanego użytkownika w **wprowadź nazwę obiektu do wybrania** , a następnie kliknij przycisk **OK**. Nazwa użytkownika, należy wykonać następujący format: Nazwa_domeny\nazwa_użytkownika.  
  
11. W **wpis uprawnienia dla Temporary ASP.NET Files** okna dialogowego pole, przyznać użytkownikowi **Pełna kontrola**, a następnie kliknij przycisk **OK** zamknąć **wpis dla tymczasowych ASP Pliki .NET** okno dialogowe.  
  
12. A **zabezpieczeń** pojawi się okno dialogowe i pyta, jeśli na pewno chcesz zmienić uprawnienia do folderu systemu. Kliknij przycisk **Tak**.  
  
13. Kliknij przycisk **OK** zamknąć **tymczasowe ASP.NET pliki właściwości** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
[ASP.NET Debugging: Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)  
