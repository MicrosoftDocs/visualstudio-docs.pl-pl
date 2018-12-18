---
title: Dodawanie danych interakcji z wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3912e823a6e6ee32488fcda94616aef414d3d22
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775306"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Dodawanie danych o interakcji między warstwami za pośrednictwem wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje dotyczące czasu wykonania synchroniczne [!INCLUDE[vstecado](../includes/vstecado-md.md)] wywołań funkcji aplikacji wielowarstwowych, które komunikują się z co najmniej jednej bazy danych.  
  
 **System Windows 8 i Windows Server 2012**  
  
 Aby zbierać dane interakcji między warstwami na aplikacje pulpitu systemu Windows 8 i aplikacje systemu Windows Server 2012 należy użyć metody instrumentacji. Zbieranie danych o interakcji między warstwami aplikacji Windows Store nie jest obsługiwane.  
  
 **Wersje programu Visual Studio**  
  
 Informacje o profilowaniu interakcji między warstwami można zbierać w programach [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] i [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)], Natomiast obejrzeć takie dane można wyświetlić tylko w [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] i [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Zbieranie danych Porada na komputerze zdalnym**  
  
 Aby zebrać dane interakcji między warstwami na komputerze zdalnym, należy skopiować **vs\_profiler\_**_\<platformy >_ **\_**  _\<Języka >_**.exe** plik wchodzącej w skład _VSInstallDir %_**tools\performance Tools\Setups**folder programu Visual Studio komputera na komputerze zdalnym i zainstaluj go. Nie można użyć narzędzi profilowania w [narzędzia zdalne programu Visual Studio](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) Pobieranie pakietu.  
  
 **Porada raportów**  
  
 Dane interakcji między warstwami można wyświetlić tylko w [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] IDE. Interakcje między warstwami plikowym raportów za pośrednictwem [VSPerfReport](../profiling/vsperfreport.md) nie są dostępne.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>Dodawanie danych interakcji między warstwami przy użyciu narzędzia VSPerfCmd  
 Narzędzie wiersza polecenia VSPerfASPNETCmd pozwala uzyskiwać dostęp do pełną funkcjonalność dostępna w narzędziach profilowania. Aby dodać funkcję tier interaction dane zbierane za pomocą narzędzia VSPerfCmd profilowania, należy użyć **VSPerfCLREnv** narzędzie ustawiania i usuwania zmiennych środowiskowych, które umożliwia dane interakcji między warstwami. Opcje, które określisz i procedur wymaganych w celu zbierania danych są zależne od typu aplikacji, który jest profilowany.  
  
### <a name="profiling-stand-alone-applications"></a>Profilowanie aplikacji autonomicznych  
 Aby dodać dane interakcji między warstwami aplikacji, która nie jest uruchamiane przez inny proces, takich jak Windows aplikacja komputerowa, która sprawia, że synchroniczne [!INCLUDE[vstecado](../includes/vstecado-md.md)] używać wywołania do bazy danych programu SQLServer **VSPerfClrEnv /InteractionOn** opcję, aby ustawić zmienne środowiskowe i **VSPerfClrEnv /InteractionOff** możliwość ich usunięcia.  
  
 W poniższym przykładzie aplikacji pulpitu Windows jest profilowana przy użyciu metody instrumentacji, i są zbierane dane interakcji między warstwami.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Przykład aplikacji pulpitu Windows profilowania  
  
1. Otwórz okno wiersza polecenia z uprawnieniami administratora. Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Akcesoria**. Kliknij prawym przyciskiem myszy **polecenia**, a następnie kliknij przycisk **Uruchom jako Administrator**.  
  
2. Zainicjuj profilowanie platformy .NET i zmiennych środowiskowych porada. Wpisz następujące polecenia:  
  
   ```  
   vsperfclrenv /traceon  
   vsperfclrenv /interactionon  
   ```  
  
3. Uruchom program profiler. Wpisz następujące polecenie:  
  
   ```  
   vsperfcmd /start:trace /output:Desktop_tip.vsp   
   ```  
  
4. Uruchom aplikację za pomocą narzędzia VSPerfCmd. Wpisz następujące polecenie:  
  
   ```  
   vsperfcmd /launch:DesktopApp.exe  
   ```  
  
5. Wykonywanie aplikacji do zbierania danych profilowania, a następnie zamknij aplikację w zwykły sposób.  
  
6. Wyczyść zmienne środowiskowe porada. Wpisz następujące polecenie:  
  
   ```  
   vsperfclrenv /off  
   ```  
  
   Aby uzyskać więcej informacji, zobacz [profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Usługi profilowania  
 Do profilu usługi, w tym [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji, używa **VSPerfClrEnv /GlobalInteractionOn** opcję, aby ustawić zmienne środowiskowe i **VSPerfClrEnv /GlobalInteractionOff** możliwość ich usunięcia.  
  
 Jeśli profilowany usług, takich jak [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, często konieczne będzie ponowne uruchomienie komputera, aby włączyć profilowanie.  
  
 W poniższym przykładzie Usługa Windows jest profilowana przy użyciu metody instrumenation i są zbierane dane interakcji między warstwami.  
  
##### <a name="profiling-a-windows-service-example"></a>Przykład usługi Windows profilowania  
  
1. Jeśli to konieczne, zainstaluj usługę.  
  
2. Otwórz okno wiersza polecenia z uprawnieniami administratora. Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Akcesoria**. Kliknij prawym przyciskiem myszy **polecenia**, a następnie kliknij przycisk **Uruchom jako Administrator**.  
  
3. Zainicjuj profilowanie zmiennych środowiskowych .NET. Wpisz następujące polecenie:  
  
   ```  
   vsperfclrenv /globaltraceon  
   ```  
  
4. Inicjowanie zmiennych środowiskowych porada. Wpisz następujące polecenie  
  
   ```  
   vsperfclrenv /globalinteractionon  
   ```  
  
5. Uruchom ponownie komputer, aby zarejestrować zmienne środowiskowe.  
  
6. Otwórz okno wiersza polecenia z uprawnieniami administratora.  
  
7. Uruchom program profiler. Wpisz następujące polecenie:  
  
   ```  
   vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
   ```  
  
8. Jeśli to konieczne, uruchom usługę.  
  
9. Dołącz profiler do usługi. Wpisz następujące polecenie:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Wykonuje usługi i zbierania danych profilowania.  
  
11. Zatrzymywanie profilera. Wpisz następujące polecenie:  
  
     `vsperfcmd /detach`  
  
12. Usuń zaznaczenie platformy .NET i Porada zmiennych środowiskowych profilowania. Wpisz następujące polecenie:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Uruchom ponownie komputer, aby zarejestrować zmienne środowiskowe wyczyszczone.  
  
    Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:  
  
    [Profilowanie aplikacji internetowej ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
    [Usługi profilowania](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>Dodawanie danych o interakcji między warstwami za pomocą polecenia VSPerfASPNETCmd  
 Narzędzie wiersza polecenia VSPerfASPNETCmd umożliwia łatwe profilu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web. W porównaniu z **VSPerfCmd** narzędzia wiersza polecenia, opcje są mniejsze, żadne zmienne środowiskowe muszą być ustawione i ponowne uruchomienie komputera nie jest wymagane. Te funkcje VSPerfASPNETCmd ułatwić zbierania danych o interakcji między warstwami wyjątkowo.  
  
 Aby dodać funkcję tier interaction do profilowania danych zebranych za pomocą VSPerfASPNETCmd **/Porada** opcji wiersza polecenia. Na przykład użyć poniższego polecenia do zbierania danych o interakcji między warstwy dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web przy użyciu metody Instrumentacji:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Aby uzyskać więcej informacji na temat VSPerfASPNETCmd zobacz [szybkie profilowanie witryny sieci Web za pomocą polecenia VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).



