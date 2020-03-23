---
title: Zdalne debugowanie | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302078"
---
# <a name="remote-debugging"></a>Debugowanie zdalne
Można debugować aplikację programu Visual Studio, która została wdrożona na innym komputerze. Aby to zrobić, należy użyć zdalnego debugera programu Visual Studio.

Aby uzyskać szczegółowe instrukcje dotyczące zdalnego debugowania, zobacz te tematy.

|Scenariusz|Link|
|-|-|-|
|Azure App Service|[Debuger migawki](../debugger/debug-live-azure-applications.md) lub [zdalne ASP.NET debugowania na platformie Azure](../debugger/remote-debugging-azure.md)|
|Maszyna wirtualna platformy Azure|[Platforma ASP.NET debugowania zdalnego na platformie Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Debugowanie aplikacji sieci szkieletowej usług Azure](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Zdalne ASP.NET debugowania ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) lub [zdalnego debugowania](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# lub Visual Basic|[Zdalne debugowanie projektu w języku C# lub Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Zdalne debugowanie projektu języka C++](../debugger/remote-debugging-cpp.md)|
|Uniwersalne aplikacje systemu Windows (UWP)|[Uruchamianie aplikacji platformy uniwersalnej systemu Windows na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md) lub [debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md)|

Jeśli chcesz tylko pobrać i zainstalować debuger zdalny i nie potrzebujesz żadnych dodatkowych instrukcji dla scenariusza, wykonaj kroki opisane w tym artykule.

## <a name="download-and-install-the-remote-tools"></a>Pobieranie i instalowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a>Wymagania

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a>(Opcjonalnie) Aby uruchomić debuger zdalny z udziału plików

Debuger zdalny *(msvsmon.exe)* można znaleźć na komputerze z już zainstalowanym programem Visual Studio Community, Professional lub Enterprise. W niektórych scenariuszach najprostszym sposobem skonfigurowania zdalnego debugowania jest uruchomienie zdalnego debugera (msvsmon.exe) z udziału plików. Aby uzyskać ograniczenia użycia, zobacz stronę Pomocy debugera zdalnego (**Pomoc > użycie** w debugerze zdalnym).

1. Znajdź *program msvsmon.exe* w katalogu odpowiadającym twojej wersji programu Visual Studio:

   ::: moniker range=">=vs-2019"

   *Pliki programów (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Pliki programów (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Pliki programów (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Pliki programów (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Udostępnianie **folderu Debuger zdalny** na komputerze z programem Visual Studio.

3. Na komputerze zdalnym uruchom *program msvsmon.exe* z folderu udostępnionego. Postępuj zgodnie z [instrukcjami konfiguracji](#bkmk_setup).

> [!TIP]
> Aby uzyskać informacje dotyczące instalacji wiersza polecenia i odwołania do wiersza polecenia, zobacz stronę Pomocy dla *programu msvsmon.exe,* wpisując ``msvsmon.exe /?`` wiersz polecenia na komputerze z zainstalowanym programem Visual Studio (lub przejdź do **Pomocy > użycie** w debugerze zdalnym).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a>Konfigurowanie zdalnego debugera
Niektóre aspekty konfiguracji debugera zdalnego można zmienić po pierwszym uruchomieniu.

- Jeśli chcesz dodać uprawnienia innych użytkowników do łączenia się z debugerem zdalnym, wybierz polecenie **Narzędzia > uprawnienia**. Musisz mieć uprawnienia administratora, aby udzielić lub odmówić uprawnień.

     > [!IMPORTANT]
     > Debuger zdalny można uruchomić w ramach konta użytkownika, który różni się od konta użytkownika, którego używasz na komputerze programu Visual Studio, ale należy dodać inne konto użytkownika do uprawnień debugera zdalnego.

     Alternatywnie można uruchomić debuger zdalny z wiersza polecenia z **parametrem /allow \<username>:** **msvsmon \< username@computer /allow>**.

- Jeśli chcesz zmienić tryb uwierzytelniania lub numer portu lub określić wartość limitu czasu dla narzędzi zdalnych: wybierz **opcję Narzędzia > Opcje**.

     Aby uzyskać listę numerów portów używanych domyślnie, zobacz [Przydziały portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Istnieje możliwość uruchomienia narzędzi zdalnych w trybie Bez uwierzytelnienia, ale używanie tego trybu jest zdecydowanie odradzane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb Brak uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwy lub wrogi ruch.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a>(Opcjonalnie) Konfigurowanie zdalnego debugera jako usługi
W przypadku debugowania w ASP.NET i innych środowiskach serwera należy uruchomić debuger zdalny jako administrator lub, jeśli chcesz, aby był zawsze uruchomiony, uruchom debuger zdalny jako usługę.

 Jeśli chcesz skonfigurować debuger zdalny jako usługę, wykonaj następujące kroki.

1. Znajdź **Kreator konfiguracji zdalnego debugera** (rdbgwiz.exe). (Jest to oddzielna aplikacja od zdalnego debugera). Jest on dostępny tylko podczas instalowania narzędzi zdalnych. Nie jest zainstalowany w programie Visual Studio.

2. Rozpocznij uruchamianie kreatora konfiguracji. Gdy pojawi się pierwsza strona, kliknij przycisk **Dalej**.

3. Zaznacz pole wyboru **Uruchom debuger zdalny programu Visual Studio 2015 jako usługę.**

4. Dodaj nazwę konta użytkownika i hasło.

    Może być konieczne dodanie prawa **użytkownika logowania jako usługi** do tego konta (Znajdź lokalne zasady **zabezpieczeń** (secpol.msc) na stronie **startowej** lub oknie (lub wpisz **secpol** w wierszu polecenia). Po wyświetleniu okna kliknij dwukrotnie pozycję **Przypisanie praw użytkownika,** a następnie znajdź **pozycję Zaloguj jako usługę** w prawym okienku. Kliknij go dwukrotnie. Dodaj konto użytkownika do okna **Właściwości** i kliknij przycisk **OK**). Kliknij przycisk **alej**.

5. Wybierz typ sieci, z którą mają komunikować się narzędzia zdalne. Należy wybrać co najmniej jeden typ sieci. Jeśli komputery są połączone za pośrednictwem domeny, należy wybrać pierwszy element. Jeśli komputery są połączone za pośrednictwem grupy roboczej lub grupy domowej, należy wybrać drugi lub trzeci element. Kliknij przycisk **alej**.

6. Jeśli usługę można uruchomić, zostanie wyświetlony **23-ty Kreator konfiguracji zdalnego debugera programu Visual Studio**. Jeśli nie można uruchomić usługi, zostanie wyświetlony **przypadek nieukończonego wykonania Kreatora konfiguracji zdalnego debugera programu Visual Studio**. Strona zawiera również kilka wskazówek do naśladowania, aby uruchomić usługę.

7. Kliknij przycisk **Zakończ**.

   W tym momencie debuger zdalny jest uruchomiony jako usługa. Można to sprawdzić, przechodząc do **Panelu sterowania > usług** i poszukając **zdalnego debugera programu Visual Studio 2015**.

   Usługę zdalnego debugera można zatrzymać i uruchomić w **Panelu sterowania > Services**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania za pomocą symboli zdalnych

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Zobacz też

- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Konfigurowanie Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remote Debugger Port Assignments (Przypisania portów zdalnego debugera)](../debugger/remote-debugger-port-assignments.md)
- [Zdalne debugowanie ASP.NET rdzenia na zdalnym komputerze usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)