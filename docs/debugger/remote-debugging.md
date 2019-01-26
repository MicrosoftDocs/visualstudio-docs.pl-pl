---
title: Zdalne debugowanie | Dokumentacja firmy Microsoft
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3fdfb851b2fc0fad6e6c394f30697dd39aa078d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961679"
---
# <a name="remote-debugging"></a>Debugowanie zdalne
Można debugować aplikację programu Visual Studio, która została wdrożona na innym komputerze. Aby to zrobić, należy użyć zdalnego debugera programu Visual Studio.

Aby uzyskać szczegółowe instrukcje na temat debugowania zdalnego zobacz następujące tematy.

|Scenariusz|Łącze|
|-|-|-|
|Usługa Azure App Service|[Snapshot Debugger](../debugger/debug-live-azure-applications.md) lub [zdalne debugowanie platformy ASP.NET na platformie Azure](../debugger/remote-debugging-azure.md)|
|Maszyna wirtualna platformy Azure|[Platforma ASP.NET debugowania zdalnego na platformie Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Debugowanie aplikacji usługi Azure Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Zdalne debugowanie platformy ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) lub [ASP.NET debugowania zdalnego](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# lub Visual Basic|[Zdalne debugowanie projektu w języku C# lub Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Debugowanie zdalne projektu C++](../debugger/remote-debugging-cpp.md)|
|Windows Universal Apps (UWP)|[Uruchamianie aplikacji platformy UWP na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md) lub [debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md)|

Jeśli po prostu chcesz pobrać i zainstalować zdalnego debugera i nie ma potrzeby żadnych dodatkowych instrukcji do danego scenariusza, wykonaj kroki opisane w tym artykule.

## <a name="download-and-install-the-remote-tools"></a>Pobieranie i instalowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements_msvsmon"></a> Wymagania

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="fileshare_msvsmon"></a> (Opcjonalnie) Aby uruchomić zdalny debuger z udziału plików

Można znaleźć zdalnego debugera (*msvsmon.exe*) na komputerze przy użyciu programu Visual Studio Community, Professional lub Enterprise już zainstalowane. W niektórych scenariuszach Najprostszym sposobem konfigurowania zdalnego debugowania jest uruchomienie zdalnego debugera (msvsmon.exe) z udziału plików. Dla ograniczenia użycia, zobacz stronę pomocy zdalny debuger (**Pomoc > użycie** w zdalnym debugerze).

1. Znajdź *msvsmon.exe* w katalogu, zgodny z używaną wersją programu Visual Studio. For Visual Studio Enterprise 2017:

      *Program pliki (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

      *Program pliki (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

2. Udostępnij **zdalny debuger** folderu na komputerze programu Visual Studio.

3. Na komputerze zdalnym, uruchom *msvsmon.exe* z folderu udostępnionego. Postępuj zgodnie z [instrukcje instalacji](#bkmk_setup).

> [!TIP]
> Instalacja przy użyciu wiersza polecenia i informacje w wierszu polecenia, zobacz stronę pomocy dla *msvsmon.exe* , wpisując ``msvsmon.exe /?`` w wierszu polecenia na komputerze przy użyciu programu Visual Studio (lub przejdź do **Pomoc > użycie**w zdalnym debugerze).

## <a name="bkmk_setup"></a> Konfigurowanie debugera zdalnego

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a> Konfigurowanie debugera zdalnego
Po uruchomieniu go po raz pierwszy, można zmienić niektóre aspekty konfiguracji zdalnego debugera.

-   Jeśli chcesz dodać uprawnienia dla innych użytkowników połączyć się ze zdalnym debugerem, wybierz opcję **Narzędzia > uprawnienia**. Musisz mieć uprawnienia administratora, aby udzielić lub odmówić uprawnień.

     > [!IMPORTANT]
     > Można uruchomić debugera zdalnego przy użyciu konta użytkownika, który różni się z konta użytkownika, którego używasz na komputerze programu Visual Studio, ale należy dodać konta innego użytkownika do zdalnego debugera uprawnień.

     Alternatywnie można uruchomić zdalnego debugera z wiersza polecenia za pomocą **/ allow \<username >** parametru: **msvsmon / allow \< username@computer>**.

-   Jeśli musisz zmienić tryb uwierzytelniania lub numer portu lub określić wartość limitu czasu dla narzędzi zdalnych: Wybierz **Narzędzia > Opcje**.

     Lista numerów portów, używany domyślnie znajduje się [zdalnego przypisania portów debugera](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     >  Istnieje możliwość uruchomienia narzędzi zdalnych w trybie Bez uwierzytelnienia, ale używanie tego trybu jest zdecydowanie odradzane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożone przez złośliwe lub wrogie działania.

##  <a name="bkmk_configureService"></a> (Opcjonalnie) Konfigurowanie debugera zdalnego jako usługi
Do debugowania na platformie ASP.NET i innych środowisk serwera, należy uruchomić zdalny debuger jako Administrator lub, będzie zawsze działać, należy uruchomić debugera zdalnego jako usługi.

 Jeśli chcesz skonfigurować debugera zdalnego jako usługę, wykonaj następujące kroki.

1. Znajdź **Kreator konfiguracji zdalnego debugera** (rdbgwiz.exe). (Jest oddzielną aplikację z debugera zdalnego). Jest ona dostępna tylko w przypadku instalowania narzędzi zdalnych. Nie zainstalowano programu Visual Studio.

2. Uruchom Kreatora konfiguracji. Gdy pierwsza strona, kliknij przycisk **dalej**.

3. Sprawdź **uruchomić debugera programu Visual Studio 2015 zdalne jako usługę** pola wyboru.

4. Dodaj nazwę konta użytkownika i hasła.

    Może być konieczne dodanie **Zaloguj się jako usługa** użytkownika bezpośrednio do tego konta (Znajdź **zasady zabezpieczeń lokalnych** (secpol.msc) w **Start** strony lub okna (lub typu  **secpol** polecenie w wierszu polecenia). Gdy pojawi się okno, kliknij dwukrotnie **Przypisywanie praw użytkownika**, następnie znajdź **Zaloguj się jako usługa** w okienku po prawej stronie. Kliknij go dwukrotnie. Dodaj konto użytkownika do **właściwości** oknie i kliknij przycisk **OK**). Kliknij przycisk **Dalej**.

5. Wybierz typ sieci, z którą komunikować narzędzia zdalne. Należy wybrać co najmniej jeden typ sieci. Jeśli komputery są połączone za pośrednictwem domeny, wybierz pierwszy element. Jeśli komputery są połączone za pośrednictwem grupy roboczej lub grupa domowa, należy wybrać elementy drugiego i trzeciego. Kliknij przycisk **Dalej**.

6. Jeśli usługa może zostać uruchomiona, zostanie wyświetlony **została pomyślnie ukończona Visual Studio Kreator konfiguracji debugera zdalnego**. Jeśli nie można uruchomić usługi, zostanie wyświetlony **nie można ukończyć Visual Studio Kreator konfiguracji debugera zdalnego**. Strona zawiera także kilka wskazówek dotyczących wykonać, aby usługa zostanie uruchomiona.

7. Kliknij przycisk **Zakończ**.

   W tym momencie zdalny debuger działa jako usługa. Można to sprawdzić, przechodząc do **Panel sterowania > usługi** i szuka **2015 zdalny debuger programu Visual Studio**.

   Można zatrzymać i uruchomić usługę zdalnego debugera z **Panel sterowania > usługi**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania przy użyciu zdalnego symboli

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Zobacz także

- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)
- [Zdalne debugowanie platformy ASP.NET Core na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)