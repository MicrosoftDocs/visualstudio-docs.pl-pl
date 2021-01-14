---
title: Dodawanie danych interakcji między warstwami z wiersza polecenia | Microsoft Docs
description: W przypadku aplikacji wielowarstwowych, które komunikują się z co najmniej jedną bazą danych, należy zastosować profilowanie interakcji między warstwami dla wywołań synchronicznych.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e5e3dc7fc3ebbb3d06e85f7322237ecb72b22b0e
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205544"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Dodawanie danych o interakcji między warstwami za pośrednictwem wiersza polecenia

Profilowanie interakcji między warstwami zawiera dodatkowe informacje o czasach wykonywania [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] wywołań synchronicznych w funkcjach aplikacji wielowarstwowych, które komunikują się z co najmniej jedną bazą danych.

**Windows 8 i Windows Server 2012**

Aby zbierać dane interakcji warstwy w aplikacjach klasycznych systemu Windows 8 i aplikacjach systemu Windows Server 2012, należy użyć metody instrumentacji. Zbieranie danych o interakcji między warstwami w aplikacjach platformy UWP nie jest obsługiwane.

**Wersje programu Visual Studio**

Profilowanie interakcji między warstwami można zbierać przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji między warstwami mogą być wyświetlane tylko w Visual Studio Enterprise.

**Zbieranie danych TIP na komputerze zdalnym**

Aby zebrać dane dotyczące interakcji warstwy na komputerze zdalnym, należy skopiować plik **vs_profiler \_** _\<Platform>_ **\_** _\<Language>_ **. exe** z folderu _% VSInstallDir%_**\Team Tools\Performance Tools\Setups** maszyny programu Visual Studio na komputerze zdalnym i zainstalować go. Nie można używać narzędzi profilowania w pakiecie pobierania [debugowania zdalnego](../debugger/remote-debugging.md) .

**Raporty TIP**

Dane interakcji warstwy można wyświetlać tylko w Visual Studio Enterprise. Raporty interakcji z warstwą opartą na plikach za pośrednictwem [VSPerfReport](../profiling/vsperfreport.md) są niedostępne.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>Dodawanie danych interakcji warstwy z VSPerfCmd

Narzędzie wiersza polecenia VSPerfASPNETCmd umożliwia dostęp do pełnych funkcji dostępnych w narzędzia profilowania. Aby dodać interakcję warstwy do profilowania danych zbieranych przy użyciu VSPerfCmd, należy użyć narzędzia **VSPerfCLREnv** , aby ustawić i usunąć zmienne środowiskowe, które umożliwiają współdziałanie danych między warstwami. Określone opcje i procedury wymagane do zbierania danych zależą od typu aplikacji, która jest profilowania.

## <a name="profile-stand-alone-applications"></a>Profile aplikacji autonomicznych

Aby dodać dane interakcji warstwy do aplikacji, która nie jest uruchamiana przez inny proces, taki jak aplikacja klasyczna systemu Windows, która wykonuje wywołania synchroniczne [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] do bazy danych programu SqlServer, użyj opcji **VSPerfClrEnv/InteractionOn** , aby ustawić zmienne środowiskowe, i opcję **VSPerfClrEnv/InteractionOff** , aby je usunąć.

W poniższym przykładzie aplikacja klasyczna systemu Windows jest profilowana przy użyciu metody instrumentacji, a dane interakcji warstwy są zbierane.

### <a name="profile-a-windows-desktop-application-example"></a>Przykład profilowania aplikacji klasycznych systemu Windows

1. Otwórz okno wiersza polecenia z uprawnieniami administratora. Kliknij przycisk **Start**, wskaż pozycję **Wszystkie programy**, a następnie wskaż pozycję **akcesoria**. Kliknij prawym przyciskiem myszy **wiersz polecenia**, a następnie kliknij polecenie **Uruchom jako administrator**.

2. Zainicjuj profilowanie .NET i zmienne środowiskowe TIP. Wpisz następujące polecenia:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Uruchom Profiler. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. Uruchom aplikację z VSPerfCmd. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Wykorzystaj aplikację do zbierania danych profilowania, a następnie zamknij aplikację w zwykły sposób.

6. Wyczyść zmienne środowiskowe TIP. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /off
    ```

Aby uzyskać więcej informacji, zobacz [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Usługi profilu

Aby profilować usługi, w tym [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacje, użyj opcji **VSPerfCLREnv/GlobalInteractionOn** , aby ustawić zmienne środowiskowe, i opcję **VSPerfCLREnv/GlobalInteractionOff** , aby je usunąć.

Podczas profilowania usług, w tym [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, często konieczne jest ponowne uruchomienie komputera w celu włączenia profilowania.

W poniższym przykładzie usługa systemu Windows jest profilowana przy użyciu metody instrumentacji, a dane interakcji warstwy są zbierane.

### <a name="profile-a-windows-service-example"></a>Przykład profilowania usługi systemu Windows

1. W razie potrzeby zainstaluj usługę.

2. Otwórz okno wiersza polecenia z uprawnieniami administratora. Kliknij przycisk **Start**, wskaż pozycję **Wszystkie programy**, a następnie wskaż pozycję **akcesoria**. Kliknij prawym przyciskiem myszy **wiersz polecenia**, a następnie kliknij polecenie **Uruchom jako administrator**.

3. Zainicjuj zmienne środowiskowe profilowania platformy .NET. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. Zainicjuj zmienne środowiskowe TIP. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Uruchom ponownie komputer, aby zarejestrować zmienne środowiskowe.

6. Otwórz okno wiersza polecenia z uprawnieniami administratora.

7. Uruchom Profiler. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. W razie potrzeby uruchom usługę.

9. Dołącz profiler do usługi. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. Wykonywanie usługi i zbieranie danych profilowania.

11. Zatrzymaj program profilujący. Wpisz następujące polecenie:

     `vsperfcmd /detach`

12. Wyczyść zmienne środowiskowe profilowania .NET i TIP. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Uruchom ponownie komputer, aby zarejestrować wyczyszczone zmienne środowiskowe.

Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:

[Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Usługi profilu](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>Dodawanie danych interakcji warstwy z VSPerfASPNETCmd

Narzędzie wiersza polecenia VSPerfASPNETCmd umożliwia łatwe profilowanie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. W porównaniu z narzędziem wiersza polecenia **VSPerfCmd** opcje są skracane, nie ma potrzeby ustawiania zmiennych środowiskowych ani ponownego uruchamiania komputera. Te funkcje programu VSPerfASPNETCmd sprawiają, że zbieranie danych o interakcji między warstwami jest wyjątkowo łatwe.

Aby dodać interakcję warstwy do profilowania danych zbieranych przy użyciu VSPerfASPNETCmd, Dodaj opcję **/TIP** do wiersza polecenia. Na przykład użyj następującego wiersza polecenia, aby zebrać dane dotyczące interakcji warstwy dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web za pomocą metody instrumentacji:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

Aby uzyskać więcej informacji na temat VSPerfASPNETCmd, zobacz [szybkie profilowanie witryny sieci Web za pomocą usługi VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
