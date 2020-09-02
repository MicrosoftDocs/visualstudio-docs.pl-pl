---
title: Dodawanie danych interakcji między warstwami z wiersza polecenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 369c5b75780e9d557dedbde60b5b584c8b3345b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705834"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Dodawanie danych o interakcji między warstwami za pośrednictwem wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilowanie interakcji między warstwami zawiera dodatkowe informacje o czasach wykonywania [!INCLUDE[vstecado](../includes/vstecado-md.md)] wywołań synchronicznych w funkcjach aplikacji wielowarstwowych, które komunikują się z co najmniej jedną bazą danych.  
  
 **Windows 8 i Windows Server 2012**  
  
 Aby zbierać dane interakcji warstwy w aplikacjach klasycznych systemu Windows 8 i aplikacjach systemu Windows Server 2012, należy użyć metody instrumentacji. Zbieranie danych o interakcji między warstwami w aplikacjach ze sklepu Windows nie jest obsługiwane.  
  
 **Wersje programu Visual Studio**  
  
 Informacje o profilowaniu interakcji między warstwami można zbierać w programach [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] i [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)], Jednak dane profilowania interakcji między warstwami mogą być wyświetlane tylko w [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] i [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
  
 **Zbieranie danych TIP na komputerze zdalnym**  
  
 Aby zbierać dane interakcji warstwy na komputerze zdalnym, należy skopiować plik programu **vs \_ Profiler \_ ** _\<Platform>_ **\_** _\<Language>_ **. exe** z folderu _% VSInstallDir%_**\Team Tools\Performance Tools\Setups** maszyny programu Visual Studio na komputerze zdalnym i zainstalować go. Nie można używać narzędzi profilowania w pakiecie pobierania [narzędzi zdalnych programu Visual Studio](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) .  
  
 **Raporty TIP**  
  
 Dane interakcji między warstwami mogą być wyświetlane tylko w środowisku [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] IDE. Raporty interakcji z warstwą opartą na plikach za pośrednictwem [VSPerfReport](../profiling/vsperfreport.md) są niedostępne.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>Dodawanie danych interakcji warstwy z VSPerfCmd  
 Narzędzie wiersza polecenia VSPerfASPNETCmd umożliwia dostęp do pełnych funkcji dostępnych w narzędzia profilowania. Aby dodać interakcję warstwy do profilowania danych zbieranych przy użyciu VSPerfCmd, należy użyć narzędzia **VSPerfCLREnv** , aby ustawić i usunąć zmienne środowiskowe, które umożliwiają współdziałanie danych między warstwami. Określone opcje i procedury wymagane do zbierania danych zależą od typu aplikacji, która jest profilowania.  
  
### <a name="profiling-stand-alone-applications"></a>Profilowania aplikacji autonomicznych  
 Aby dodać dane interakcji warstwy do aplikacji, która nie jest uruchamiana przez inny proces, taki jak aplikacja klasyczna systemu Windows, która wykonuje wywołania synchroniczne [!INCLUDE[vstecado](../includes/vstecado-md.md)] do bazy danych programu SqlServer, użyj opcji **VSPerfClrEnv/InteractionOn** , aby ustawić zmienne środowiskowe, i opcję **VSPerfClrEnv/InteractionOff** , aby je usunąć.  
  
 W poniższym przykładzie aplikacja klasyczna systemu Windows jest profilowana przy użyciu metody instrumentacji, a dane interakcji warstwy są zbierane.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Przykład profilowania aplikacji klasycznych systemu Windows  
  
1. Otwórz okno wiersza polecenia z uprawnieniami administratora. Kliknij przycisk **Start**, wskaż pozycję **Wszystkie programy**, a następnie wskaż pozycję **akcesoria**. Kliknij prawym przyciskiem myszy **wiersz polecenia**, a następnie kliknij polecenie **Uruchom jako administrator**.  
  
2. Zainicjuj profilowanie .NET i zmienne środowiskowe TIP. Wpisz następujące polecenia:  
  
   ```  
   vsperfclrenv /traceon  
   vsperfclrenv /interactionon  
   ```  
  
3. Uruchom Profiler. Wpisz następujące polecenie:  
  
   ```  
   vsperfcmd /start:trace /output:Desktop_tip.vsp   
   ```  
  
4. Uruchom aplikację z VSPerfCmd. Wpisz następujące polecenie:  
  
   ```  
   vsperfcmd /launch:DesktopApp.exe  
   ```  
  
5. Wykorzystaj aplikację do zbierania danych profilowania, a następnie zamknij aplikację w zwykły sposób.  
  
6. Wyczyść zmienne środowiskowe TIP. Wpisz następujące polecenie:  
  
   ```  
   vsperfclrenv /off  
   ```  
  
   Aby uzyskać więcej informacji, zobacz [profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Usługi profilowania  
 Aby profilować usługi, w tym [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacje, użyj opcji **VSPerfCLREnv/GlobalInteractionOn** , aby ustawić zmienne środowiskowe, i opcję **VSPerfCLREnv/GlobalInteractionOff** , aby je usunąć.  
  
 Podczas profilowania usług, w tym [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, często konieczne jest ponowne uruchomienie komputera w celu włączenia profilowania.  
  
 W poniższym przykładzie usługa systemu Windows jest profilowana przy użyciu metody instrumenation, a dane interakcji warstwy są zbierane.  
  
##### <a name="profiling-a-windows-service-example"></a>Przykład profilowania usługi systemu Windows  
  
1. W razie potrzeby zainstaluj usługę.  
  
2. Otwórz okno wiersza polecenia z uprawnieniami administratora. Kliknij przycisk **Start**, wskaż pozycję **Wszystkie programy**, a następnie wskaż pozycję **akcesoria**. Kliknij prawym przyciskiem myszy **wiersz polecenia**, a następnie kliknij polecenie **Uruchom jako administrator**.  
  
3. Zainicjuj zmienne środowiskowe profilowania platformy .NET. Wpisz następujące polecenie:  
  
   ```  
   vsperfclrenv /globaltraceon  
   ```  
  
4. Zainicjuj zmienne środowiskowe TIP. Wpisz następujące polecenie  
  
   ```  
   vsperfclrenv /globalinteractionon  
   ```  
  
5. Uruchom ponownie komputer, aby zarejestrować zmienne środowiskowe.  
  
6. Otwórz okno wiersza polecenia z uprawnieniami administratora.  
  
7. Uruchom Profiler. Wpisz następujące polecenie:  
  
   ```  
   vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
   ```  
  
8. W razie potrzeby uruchom usługę.  
  
9. Dołącz profiler do usługi. Wpisz następujące polecenie:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Wykonywanie usługi i zbieranie danych profilowania.  
  
11. Zatrzymaj program profilujący. Wpisz następujące polecenie:  
  
     `vsperfcmd /detach`  
  
12. Wyczyść zmienne środowiskowe profilowania .NET i TIP. Wpisz następujące polecenie:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Uruchom ponownie komputer, aby zarejestrować wyczyszczone zmienne środowiskowe.  
  
    Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:  
  
    [Profilowanie aplikacji internetowej ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
    [Usługi profilowania](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>Dodawanie danych interakcji warstwy z VSPerfASPNETCmd  
 Narzędzie wiersza polecenia VSPerfASPNETCmd umożliwia łatwe profilowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web. W porównaniu z narzędziem wiersza polecenia **VSPerfCmd** opcje są skracane, nie ma potrzeby ustawiania zmiennych środowiskowych ani ponownego uruchamiania komputera. Te funkcje programu VSPerfASPNETCmd sprawiają, że zbieranie danych o interakcji między warstwami jest wyjątkowo łatwe.  
  
 Aby dodać interakcję warstwy do profilowania danych zbieranych przy użyciu VSPerfASPNETCmd, Dodaj opcję **/TIP** do wiersza polecenia. Na przykład użyj następującego wiersza polecenia, aby zebrać dane dotyczące interakcji warstwy dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web za pomocą metody instrumentacji:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Aby uzyskać więcej informacji na temat VSPerfASPNETCmd, zobacz [szybkie profilowanie witryny sieci Web za pomocą usługi VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
