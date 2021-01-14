---
title: Debugowanie zdalne | Microsoft Docs
description: Debuguj aplikację Visual Studio, która została wdrożona na innym komputerze przy użyciu zdalnego debugera programu Visual Studio.
ms.custom:
- remotedebugging
- seodec18
- SEO-VS-2020
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
ms.openlocfilehash: e97fd8979235f8ea89b43c6466b3119debe5b3ca
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205674"
---
# <a name="remote-debugging"></a>Debugowanie zdalne
Można debugować aplikację Visual Studio, która została wdrożona na innym komputerze. W tym celu należy użyć zdalnego debugera programu Visual Studio.

Szczegółowe instrukcje dotyczące debugowania zdalnego znajdują się w tych tematach.

|Scenariusz|Łącze|
|-|-|-|
|Azure App Service|[Zdalne debugowanie ASP.NET na platformie Azure](../debugger/remote-debugging-azure.md) lub, w przypadku Visual Studio Enterprise, [Snapshot Debugger](../debugger/debug-live-azure-applications.md)|
|Maszyna wirtualna platformy Azure|[Platforma ASP.NET debugowania zdalnego na platformie Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Debugowanie aplikacji Service Fabric platformy Azure](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Zdalne debugowanie ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) lub [zdalne debugowanie ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# lub Visual Basic|[Zdalne debugowanie projektu w języku C# lub Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Debugowanie zdalne projektu C++](../debugger/remote-debugging-cpp.md)|
|Aplikacje uniwersalne systemu Windows (platformy UWP)|[Uruchom aplikacje platformy UWP na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md) lub [Debuguj zainstalowany pakiet aplikacji](../debugger/debug-installed-app-package.md)|

Jeśli chcesz po prostu pobrać i zainstalować zdalny debuger i nie potrzebujesz dodatkowych instrukcji dla danego scenariusza, wykonaj kroki opisane w tym artykule.

## <a name="download-and-install-the-remote-tools"></a>Pobieranie i Instalowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Wymagania

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> Obowiązkowe Aby uruchomić zdalny debuger z udziału plików

Zdalny debuger (*msvsmon.exe*) można znaleźć na komputerze, na którym jest już zainstalowany program Visual Studio Community, Professional lub Enterprise. W niektórych scenariuszach Najprostszym sposobem skonfigurowania zdalnego debugowania jest uruchomienie zdalnego debugera (msvsmon.exe) z udziału plików. Aby uzyskać ograniczenia dotyczące użycia, zobacz stronę pomocy zdalnego debugera (**pomoc > użyciu** w debugerze zdalnym).

1. Znajdź *msvsmon.exe* w katalogu pasującym do używanej wersji programu Visual Studio:

   ::: moniker range=">=vs-2019"

   *Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Udostępnij folder **debugera zdalnego** na komputerze z Visual Studio.

3. Na komputerze zdalnym uruchom *msvsmon.exe* z folderu udostępnionego. Postępuj zgodnie z [instrukcjami instalacji](#bkmk_setup).

> [!TIP]
> Aby uzyskać informacje dotyczące instalacji wiersza polecenia i wiersza polecenia, zobacz stronę pomocy dla *msvsmon.exe* , wpisując ``msvsmon.exe /?`` w wierszu polecenia na komputerze z zainstalowanym programem Visual Studio (lub przejdź do **pomocy > użyciu** w debugerze zdalnym).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Konfigurowanie zdalnego debugera
Niektóre aspekty konfiguracji zdalnego debugera można zmienić po jego po raz pierwszy.

- Jeśli musisz dodać uprawnienia dla innych użytkowników, aby połączyć się ze zdalnym debugerem, wybierz pozycję **narzędzia > uprawnienia**. Musisz mieć uprawnienia administratora, aby udzielić lub odmówić uprawnień.

     > [!IMPORTANT]
     > Zdalny debuger można uruchomić w ramach konta użytkownika, które różni się od konta użytkownika używanego na komputerze z programem Visual Studio, ale należy dodać inne konto użytkownika do uprawnień zdalnego debugera.

     Alternatywnie można uruchomić zdalny debuger z wiersza polecenia z parametrem **\<username> /Allow** : **msvsmon/Allow \<username@computer>**.

- Jeśli trzeba zmienić tryb uwierzytelniania lub numer portu lub określić wartość limitu czasu dla narzędzi zdalnych: Wybierz **narzędzia > opcje**.

     Aby uzyskać listę numerów portów używanych domyślnie, zobacz [zdalne przydziały portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Istnieje możliwość uruchomienia narzędzi zdalnych w trybie Bez uwierzytelnienia, ale używanie tego trybu jest zdecydowanie odradzane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub szkodliwe dane.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> Obowiązkowe Konfigurowanie zdalnego debugera jako usługi
W przypadku debugowania w ASP.NET i innych środowiskach serwerów należy uruchomić zdalny debuger jako administrator lub, jeśli chcesz, aby zawsze działał, uruchom zdalny debuger jako usługę.

 Jeśli chcesz skonfigurować zdalny debuger jako usługę, wykonaj następujące kroki.

1. Znajdź **Kreatora konfiguracji debugera zdalnego** (rdbgwiz.exe). (Jest to oddzielna aplikacja ze zdalnego debugera). Jest ona dostępna tylko podczas instalowania narzędzi zdalnych. Nie jest on instalowany z programem Visual Studio.

2. Rozpocznij pracę z kreatorem konfiguracji. Gdy pierwsza strona zostanie wystawiona, kliknij przycisk **dalej**.

3. Zaznacz pole wyboru **Uruchom Debuger zdalny programu Visual Studio 2015 jako usługę** .

4. Dodaj nazwę konta użytkownika i hasło.

    Może być konieczne dodanie do tego konta uprawnienia **Zaloguj się jako użytkownik usługi** ( **zasady zabezpieczeń lokalnych** (secpol. msc) na stronie lub w oknie **startowym** (lub w wierszu polecenia)  . Po wyświetleniu okna kliknij dwukrotnie pozycję **Przypisywanie praw użytkownika**, a następnie znajdź opcję **Zaloguj się jako usługa** w okienku po prawej stronie. Kliknij go dwukrotnie. Dodaj konto użytkownika do okna **Właściwości** , a następnie kliknij przycisk **OK**. Kliknij przycisk **Dalej**.

5. Wybierz typ sieci, z którą mają się komunikować narzędzia zdalne. Należy wybrać co najmniej jeden typ sieci. Jeśli komputery są połączone za pomocą domeny, należy wybrać pierwszy element. Jeśli komputery są połączone przez grupę roboczą lub grupę domową, należy wybrać drugą lub trzecią pozycję. Kliknij przycisk **Dalej**.

6. Jeśli usługa może zostać uruchomiona, zostanie wyświetlony **Kreator konfiguracji zdalny debuger programu Visual Studio, który pomyślnie ukończył** pracę. Jeśli nie można uruchomić usługi, **nie można ukończyć pracy Kreatora konfiguracji zdalny debuger programu Visual Studio**. Na stronie znajdują się również porady, które należy wykonać, aby rozpocząć pracę usługi.

7. Kliknij przycisk **Finish** (Zakończ).

   W tym momencie zdalny debuger działa jako usługa. Można to sprawdzić, przechodząc do **Panelu sterowania > usługi** i szukając **zdalnego debugera programu Visual Studio 2015**.

   Usługę zdalnego debugera można zatrzymać i uruchomić z poziomu **Panelu sterowania > usług**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania ze zdalnymi symbolami

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Zobacz też

- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Przypisania portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md)
- [Zdalne debugowanie ASP.NET Core na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)