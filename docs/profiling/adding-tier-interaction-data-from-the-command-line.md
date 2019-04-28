---
title: Dodawanie danych interakcji z wiersza polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b04b2d2c3c23b444d011d81002f7f22a12b1ebf0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62777870"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Dodawanie danych o interakcji między warstwami za pośrednictwem wiersza polecenia

Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje dotyczące czasu wykonania synchroniczne [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] wywołań funkcji aplikacji wielowarstwowych, które komunikują się z co najmniej jednej bazy danych.

**System Windows 8 i Windows Server 2012**

Aby zbierać dane interakcji między warstwami na aplikacje pulpitu systemu Windows 8 i aplikacje systemu Windows Server 2012 należy użyć metody instrumentacji. Zbieranie danych o interakcji między warstwami aplikacji platformy uniwersalnej systemu Windows nie jest obsługiwane.

**Visual Studio editions**

Profilowanie interakcji między warstwami można zbierać w programach dowolnej wersji programu Visual Studio. Natomiast obejrzeć takie dane można wyświetlać tylko w programie Visual Studio Enterprise.

**Zbieranie danych Porada na komputerze zdalnym**

Aby zebrać dane interakcji między warstwami na komputerze zdalnym, należy skopiować **vs_profiler\_**_\<platformy >_ **\_**  _\<Języka >_**.exe** plik wchodzącej w skład _VSInstallDir %_**tools\performance Tools\Setups** folderu Visual Studio komputera na komputerze zdalnym i zainstaluj go. Nie można użyć narzędzi profilowania w [zdalne debugowanie](../debugger/remote-debugging.md) Pobieranie pakietu.

**Porada raportów**

Dane interakcji między warstwami można wyświetlić tylko w Visual Studio Enterprise. Interakcje między warstwami plikowym raportów za pośrednictwem [VSPerfReport](../profiling/vsperfreport.md) nie są dostępne.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>Dodaj dane interakcji między warstwami przy użyciu narzędzia VSPerfCmd

Narzędzie wiersza polecenia VSPerfASPNETCmd pozwala uzyskiwać dostęp do pełną funkcjonalność dostępna w narzędziach profilowania. Aby dodać funkcję tier interaction dane zbierane za pomocą narzędzia VSPerfCmd profilowania, należy użyć **VSPerfCLREnv** narzędzie ustawiania i usuwania zmiennych środowiskowych, które umożliwia dane interakcji między warstwami. Opcje, które określisz i procedur wymaganych w celu zbierania danych są zależne od typu aplikacji, który jest profilowany.

## <a name="profile-stand-alone-applications"></a>Profil aplikacji autonomicznych

Aby dodać dane interakcji między warstwami aplikacji, która nie jest uruchamiane przez inny proces, takich jak Windows aplikacja komputerowa, która sprawia, że synchroniczne [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] używać wywołania do bazy danych programu SQLServer **VSPerfClrEnv /InteractionOn** opcję, aby ustawić zmienne środowiskowe i **VSPerfClrEnv /InteractionOff** możliwość ich usunięcia.

W poniższym przykładzie aplikacji pulpitu Windows jest profilowana przy użyciu metody instrumentacji, i są zbierane dane interakcji między warstwami.

### <a name="profile-a-windows-desktop-application-example"></a>Przykład aplikacji pulpitu Windows profilu

1. Otwórz okno wiersza polecenia z uprawnieniami administratora. Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Akcesoria**. Kliknij prawym przyciskiem myszy **polecenia**, a następnie kliknij przycisk **Uruchom jako Administrator**.

2. Zainicjuj profilowanie platformy .NET i zmiennych środowiskowych porada. Wpisz następujące polecenia:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Uruchom program profiler. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. Uruchom aplikację za pomocą narzędzia VSPerfCmd. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Wykonywanie aplikacji do zbierania danych profilowania, a następnie zamknij aplikację w zwykły sposób.

6. Wyczyść zmienne środowiskowe porada. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /off
    ```

Aby uzyskać więcej informacji, zobacz [profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Usługi profilowania

Do profilu usługi, w tym [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji, używa **VSPerfClrEnv /GlobalInteractionOn** opcję, aby ustawić zmienne środowiskowe i **VSPerfClrEnv /GlobalInteractionOff** możliwość ich usunięcia.

Jeśli profilowany usług, takich jak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, często konieczne będzie ponowne uruchomienie komputera, aby włączyć profilowanie.

W poniższym przykładzie Usługa Windows jest profilowana przy użyciu metody instrumentacji, i są zbierane dane interakcji między warstwami.

### <a name="profile-a-windows-service-example"></a>Przykład usługi Windows profilu

1. Jeśli to konieczne, zainstaluj usługę.

2. Otwórz okno wiersza polecenia z uprawnieniami administratora. Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Akcesoria**. Kliknij prawym przyciskiem myszy **polecenia**, a następnie kliknij przycisk **Uruchom jako Administrator**.

3. Zainicjuj profilowanie zmiennych środowiskowych .NET. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. Inicjowanie zmiennych środowiskowych porada. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Uruchom ponownie komputer, aby zarejestrować zmienne środowiskowe.

6. Otwórz okno wiersza polecenia z uprawnieniami administratora.

7. Uruchom program profiler. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. Jeśli to konieczne, uruchom usługę.

9. Dołącz profiler do usługi. Wpisz następujące polecenie:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. Wykonuje usługi i zbierania danych profilowania.

11. Zatrzymywanie profilera. Wpisz następujące polecenie:

     `vsperfcmd /detach`

12. Usuń zaznaczenie platformy .NET i Porada zmiennych środowiskowych profilowania. Wpisz następujące polecenie:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Uruchom ponownie komputer, aby zarejestrować zmienne środowiskowe wyczyszczone.

Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:

[Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Usługi profilowania](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>Dodawanie danych o interakcji między warstwami za pomocą polecenia VSPerfASPNETCmd

Narzędzie wiersza polecenia VSPerfASPNETCmd umożliwia łatwe profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. W porównaniu z **VSPerfCmd** narzędzia wiersza polecenia, opcje są mniejsze, żadne zmienne środowiskowe muszą być ustawione i ponowne uruchomienie komputera nie jest wymagane. Te funkcje VSPerfASPNETCmd ułatwić zbierania danych o interakcji między warstwami wyjątkowo.

Aby dodać funkcję tier interaction do profilowania danych zebranych za pomocą VSPerfASPNETCmd **/Porada** opcji wiersza polecenia. Na przykład użyć poniższego polecenia do zbierania danych o interakcji między warstwy dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web przy użyciu metody Instrumentacji:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

Aby uzyskać więcej informacji na temat VSPerfASPNETCmd zobacz [profilowania szybkie witryn sieci web za pomocą polecenia VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).