---
title: Dodawanie danych interakcji warstwy z wiersza polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 20b8438243382b28cccb510894d1674aa5872946
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779873"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Dodawanie danych o interakcji między warstwami za pośrednictwem wiersza polecenia

Profilowanie interakcji warstwy zawiera dodatkowe informacje na [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] temat czasów wykonywania wywołań synchronicznych w funkcjach aplikacji wielowarstwowych, które komunikują się z jedną lub kilkoma bazami danych.

**Windows 8 i Windows Server 2012**

Aby zbierać dane interakcji warstwy w aplikacjach klasycznych systemu Windows 8 i aplikacjach systemu Windows Server 2012, należy użyć metody instrumentacji. Zbieranie danych interakcji warstwy w aplikacjach platformy uniwersalnej systemu Windows nie jest obsługiwane.

**Wersje programu Visual Studio**

Profilowanie interakcji warstwy mogą być zbierane przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji warstwy można wyświetlać tylko w programie Visual Studio Enterprise.

**Zbieranie danych TIP na komputerze zdalnym**

Aby zbierać dane interakcji warstwy na **\_** komputerze zdalnym, należy skopiować vs_profiler_\<>_ **\_** _ \<plik language>_ **.exe** z folderu _%VSInstallDir%_**\Team Tools\Performance Tools\Setups** komputera programu Visual Studio na komputer zdalny i zainstalować go. Nie można używać narzędzi profilowania w pakiecie pobierania [zdalnego debugowania.](../debugger/remote-debugging.md)

**Raporty TIP**

Dane interakcji warstwy można wyświetlać tylko w programie Visual Studio Enterprise. Raporty interakcji warstwy opartej na plikach za pośrednictwem [programu VSPerfReport](../profiling/vsperfreport.md) nie są dostępne.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>Dodawanie danych interakcji warstwy za pomocą programu VSPerfCmd

Narzędzie wiersza polecenia VSPerfASPNETCmd umożliwia dostęp do pełnej funkcjonalności dostępnej w narzędziach profilowania. Aby dodać interakcję warstwy do profilowania danych zebranych przy użyciu vsperfCmd, należy użyć **narzędzia VSPerfCLREnv,** aby ustawić i usunąć zmienne środowiskowe, które umożliwia dane interakcji warstwy. Opcje, które określisz i procedury wymagane do zbierania danych zależą od typu aplikacji, która jest profilowanie.

## <a name="profile-stand-alone-applications"></a>Aplikacje autonomiczne profilu

Aby dodać dane interakcji warstwy do aplikacji, która nie jest uruchamiana przez inny [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] proces, taki jak aplikacja klasyczna systemu Windows, która wykonuje synchroniczne wywołania do bazy danych SQLServer, użyj opcji **VSPerfClrEnv /InteractionOn,** aby ustawić zmienne środowiskowe, a **vsPerfClrEnv /InteractionOff** opcja, aby je usunąć.

W poniższym przykładzie aplikacja klasyczna systemu Windows jest profilowana przy użyciu metody instrumentacji i dane interakcji warstwy są zbierane.

### <a name="profile-a-windows-desktop-application-example"></a>Profiluj przykład aplikacji klasycznej systemu Windows

1. Otwórz okno wiersza polecenia z uprawnieniami Administratora. Kliknij **przycisk Start**, wskaż pozycję Wszystkie **programy**, a następnie wskaż polecenie **Akcesoria**. Kliknij prawym przyciskiem myszy **wiersz polecenia**, a następnie kliknij polecenie Uruchom **jako administrator**.

2. Inicjuj profilowanie .NET i zmienne środowiskowe TIP. Wpisz następujące polecenia:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Uruchom profiler. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. Uruchom aplikację za pomocą programu VSPerfCmd. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Wyćmij aplikację, aby zebrać dane profilowania, a następnie zamknij aplikację w regularny sposób.

6. Wyczyść zmienne środowiskowe TIP. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /off
    ```

Aby uzyskać więcej informacji, zobacz [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Usługi profilowania

Aby skonfigurować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zmienne środowiskowe, a następnie opcję **VSPerfClrEnv /GlobalInteractionOff,** należy użyć opcji **VSPerfClrEnv /GlobalInteractionOn.**

Podczas profilowania usług, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] w tym aplikacji sieci Web, często trzeba będzie ponownie uruchomić komputer, aby włączyć profilowanie.

W poniższym przykładzie usługa systemu Windows jest profilowane przy użyciu metody instrumentacji i dane interakcji warstwy są zbierane.

### <a name="profile-a-windows-service-example"></a>Profiluj przykład usługi systemu Windows

1. W razie potrzeby zainstaluj usługę.

2. Otwórz okno wiersza polecenia z uprawnieniami Administratora. Kliknij **przycisk Start**, wskaż pozycję Wszystkie **programy**, a następnie wskaż polecenie **Akcesoria**. Kliknij prawym przyciskiem myszy **wiersz polecenia**, a następnie kliknij polecenie Uruchom **jako administrator**.

3. Inicjowanie zmiennych środowiskowych profilowania .NET. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. Inicjuj zmienne środowiskowe TIP. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Uruchom ponownie komputer, aby zarejestrować zmienne środowiskowe.

6. Otwórz okno wiersza polecenia z uprawnieniami Administratora.

7. Uruchom profiler. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. W razie potrzeby uruchom usługę.

9. Dołącz profiler do usługi. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. Wykonywanie usługi i zbieranie danych profilowania.

11. Zatrzymaj profiler. Wpisz następujące polecenie:

     `vsperfcmd /detach`

12. Wyczyść zmienne środowiskowe profilowania .NET i TIP. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Uruchom ponownie komputer, aby zarejestrować wyczyszczone zmienne środowiskowe.

Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:

[Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Usługi profilowania](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>Dodawanie danych interakcji warstwy za pomocą programu VSPerfASPNETCmd

Narzędzie wiersza polecenia VSPerfASPNETCmd umożliwia [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] łatwe profilowanie aplikacji sieci Web. W porównaniu z narzędziem wiersza polecenia **VSPerfCmd** opcje są zmniejszone, nie trzeba ustawiać żadnych zmiennych środowiskowych, a ponowne uruchomienie komputera nie jest wymagane. Te funkcje VSPerfASPNETCmd sprawiają, że zbieranie danych interakcji warstwy wyjątkowo łatwe.

Aby dodać interakcję warstwy do danych profilowania zebranych przy użyciu programu VSPerfASPNETCmd, dodaj opcję **/TIP** do wiersza polecenia. Na przykład użyj następującego wiersza polecenia do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zbierania danych interakcji warstwy dla aplikacji sieci Web przy użyciu metody instrumentacji:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

Aby uzyskać więcej informacji na temat programu VSPerfASPNETCmd, zobacz [Szybkie profilowanie witryny sieci Web za pomocą programu VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
