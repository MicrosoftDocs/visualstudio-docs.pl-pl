---
title: Uruchamianie procesu roboczego w ramach konta użytkownika | Microsoft Docs
description: Skonfiguruj komputer tak, aby można było uruchomić proces roboczy ASP.NET (aspnet_wp.exe lub w3wp.exe) w ramach konta użytkownika w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 752d09a0d0c6fe49e49e1298d475c90c86991836
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384645"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Porady: uruchamianie procesu roboczego z konta użytkownika
Aby skonfigurować komputer tak, aby można było uruchomić proces roboczy (aspnet_wp.exe lub w3wp.exe) w ramach konta [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] użytkownika, wykonaj następujące kroki.

 > [!IMPORTANT]
 > Począwszy od systemu Windows Server 2008 R2, zalecamy używanie [applicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) jako tożsamości dla każdej puli aplikacji.

## <a name="procedure"></a>Procedura

#### <a name="to-run-aspnet_wpexe-under-a-user-account"></a>Aby uruchomić aspnet_wp.exe w ramach konta użytkownika

1. Otwórz plik machine.config znajdujący się na komputerze w folderze CONFIG w ścieżce, w której zainstalowano środowisko uruchomieniowe.

2. Znajdź sekcję processModel i zmień atrybuty użytkownika i hasła na nazwę i hasło konta użytkownika, &lt; &gt; w aspnet_wp.exe chcesz uruchomić.

3. Zapisz machine.config plik.

4. W [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)] programie program IIS 6.0 jest instalowany domyślnie. Odpowiedni proces roboczy jest w3wp.exe. Aby uruchomić program w trybie usług IIS 6.0 aspnet_wp.exe proces roboczy, należy wykonać następujące kroki:

   1. Kliknij **przycisk Start,** kliknij **pozycję Narzędzia administracyjne,** a następnie **wybierz Internet Information Services**.

   2. W **oknie Internet Information Services** kliknij prawym przyciskiem myszy folder Witryny sieci **Web** i wybierz polecenie **Właściwości.**

   3. W **oknie dialogowym Właściwości** witryn sieci Web wybierz pozycję **Usługa**.

   4. Wybierz **pozycję Uruchom usługę WWW w trybie izolacji usług IIS 6.0.**

   5. Zamknij okno **dialogowe** Właściwości i **menedżer usług internetowych**.

5. Otwórz wiersz polecenia systemu Windows i zresetuj serwer, uruchamiając polecenie:

   ```cmd
   iisreset
   ```

   — lub —

   ```cmd
   net stop iisadmin /y
   net start w3svc
   ```

6. Znajdź folder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Pliki tymczasowe, który powinien znajdować się w tej samej ścieżce co folder CONFIG. Kliknij prawym przyciskiem myszy folder Pliki [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tymczasowe i wybierz polecenie **Właściwości** w menu skrótów.

7. W **oknie dialogowym Właściwości ASP.NET plików** tymczasowych kliknij **kartę** Zabezpieczenia.

8. Kliknij pozycję **Zaawansowane**.

9. W **oknie dialogowym Zaawansowane ustawienia zabezpieczeń ASP.Net plików** kliknij przycisk **Dodaj**.

    Zostanie **wyświetlone okno dialogowe Wybieranie użytkownika, komputera lub** grupy.

10. Wpisz nazwę użytkownika w polu Wprowadź nazwę obiektu do **wybrania,** a następnie kliknij przycisk **OK.** Nazwa użytkownika musi być w tym formacie: Nazwa_domeny\Nazwa_użytkownika.

11. W **Wpis uprawnień dla** tymczasowych plików ASP.NET okna dialogowego nadaj użytkownikowi pełną **kontrolę,** a następnie kliknij przycisk **OK,** aby **zamknąć** okno dialogowe Wpis tymczasowych ASP.NET plików.

12. Zostanie **wyświetlone** okno dialogowe Zabezpieczenia z pytaniem, czy naprawdę chcesz zmienić uprawnienia w folderze systemowym. Kliknij przycisk **Yes** (Tak).

13. Kliknij **przycisk OK,** aby zamknąć **okno dialogowe Właściwości ASP.NET plików** tymczasowych.

## <a name="see-also"></a>Zobacz też
- [Debugowanie ASP.NET aplikacji](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [ASP.NET debugowania: wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)
