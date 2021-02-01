---
title: Debugowanie aplikacji .NET Core w WSL 2
description: Dowiedz się, jak uruchamiać i debugować aplikacje platformy .NET Core w WSL 2 bez opuszczania programu Visual Studio.
ms.date: 01/25/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 736987a02ca7e2f59ce689b8402d9a6fcd7407e9
ms.sourcegitcommit: 586369f5aa61d4a0330802f718f0ceaa55d7e9c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2021
ms.locfileid: "99227656"
---
# <a name="debug-net-core-apps-in-wsl-2-with-visual-studio"></a>Debugowanie aplikacji .NET Core w programie WSL 2 za pomocą programu Visual Studio

Możesz łatwo uruchamiać i debugować aplikacje platformy .NET Core w systemie Linux bez opuszczania programu Visual Studio przy użyciu WSL 2. Jeśli jesteś deweloperem na wielu platformach, możesz użyć tej metody jako prostego sposobu testowania większej liczby środowisk docelowych.

W przypadku użytkownika systemu Windows .NET ukierunkowanego na system Linux WSL 2 jest w postaci słodkiej, między rzeczywistymi i produktywnością produkcji. W programie Visual Studio można już debugować w zdalnym środowisku systemu Linux przy użyciu [zdalnego debugera](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)lub kontenerów za pomocą narzędzi do [kontenerów](../containers/overview.md). Gdy produkcja rzeczywista jest głównym problemem, należy użyć jednej z tych opcji. Gdy łatwa i szybka pętla wewnętrzna jest bardziej ważna, WSL 2 to świetna opcja.

Nie musisz wybierać tylko jednej metody! Możesz mieć profil uruchamiania platformy Docker i WSL 2 w tym samym projekcie i wybrać, która jest odpowiednia dla określonego uruchomienia. Po wdrożeniu aplikacji zawsze możesz użyć zdalnego debugera, aby dołączyć do niego w przypadku wystąpienia problemu.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio 2019 v 16.9 wersja zapoznawcza 1 lub nowszy z programem .NET Core — debugowaniem z opcjonalnym składnikiem WSL 2.

  Składnik opcjonalny jest domyślnie uwzględniany dla wielu platform .NET Core lub obciążeń ASP.NET i Web Development. Należy zainstalować jedno lub oba te obciążenia.

- Zainstaluj program [WSL 2](/windows/wsl/about).

- Zainstaluj wybraną [dystrybucję](https://aka.ms/wslstore) .

## <a name="start-debugging-with-wsl-2"></a>Rozpocznij debugowanie za pomocą WSL 2

1. Po zainstalowaniu wymaganych składników Otwórz aplikację sieci Web ASP.NET Core lub aplikację konsolową .NET Core w programie Visual Studio zobaczysz nowy profil uruchamiania o nazwie WSL 2:

   ![WSL 2 Uruchom profil na liście profilów uruchamiania](media/linux-wsl2-debugging-select-launch-profile.png)

1. Wybierz ten profil, aby dodać go do *launchSettings.js*.

   Niektóre atrybuty klucza w pliku przedstawiono w poniższym przykładzie.

    ```json
    "WSL 2": {
        "commandName": "WSL2",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```

   Po wybraniu nowego profilu rozszerzenie sprawdza, czy dystrybucja WSL 2 jest skonfigurowana do uruchamiania aplikacji platformy .NET Core i ułatwia instalację wszelkich brakujących zależności. Po zainstalowaniu tych zależności możesz rozpocząć debugowanie w WSL 2.

1. Rozpocznij debugowanie jako normalne, a aplikacja zostanie uruchomiona w domyślnej dystrybucji WSL 2.

   Łatwym sposobem sprawdzenia, czy jest uruchomiony system Linux, jest sprawdzenie wartości `Environment.OSVersion` .

>[!NOTE]
> Przetestowane i obsługiwane są tylko Ubuntu i debian. Inne dystrybucje obsługiwane przez platformę .NET Core powinny funkcjonować, ale wymagają ręcznej instalacji [środowiska uruchomieniowego](https://aka.ms/wsldotnet) i [zwinięcie](https://curl.haxx.se/)środowiska .NET Core.

## <a name="choose-a-specific-distribution"></a>Wybierz określoną dystrybucję

Domyślnie profil uruchamiania WSL 2 używa dystrybucji domyślnej ustawionej w *wsl.exe*. Jeśli chcesz, aby profil uruchamiania został określony jako przeznaczony do określonej dystrybucji, bez względu na to, że domyślne, możesz zmodyfikować profil uruchamiania. Na przykład jeśli debugujesz aplikację sieci Web i chcesz ją przetestować w witrynie Ubuntu 20,04, profil uruchamiania będzie wyglądać następująco:

```json
"WSL 2": {
    "commandName": "WSL2",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```

## <a name="target-multiple-distributions"></a>Kierowanie wielu dystrybucji

Przechodzenie do kolejnego kroku, jeśli pracujesz z aplikacją, która musi działać w wielu dystrybucjach, i chcesz szybko przetestować każdy z nich, możesz mieć wiele profilów uruchamiania. Na przykład jeśli chcesz przetestować aplikację konsolową w systemie Debian, Ubuntu 18,04 i Ubuntu 20,04, możesz użyć następujących profilów uruchamiania:

```json
"WSL 2 : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL 2 : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL 2 : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```

Przy użyciu tych profilów uruchamiania można łatwo przełączać się między dystrybucją docelową i z nich, bez opuszczania komfortu pracy programu Visual Studio.

![Wiele profili uruchamiania w WSL 2 na liście profil uruchamiania](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Ustawienia WSL w profilu uruchamiania

W poniższej tabeli przedstawiono ustawienia, które są obsługiwane w profilu uruchamiania.

|Nazwa|Domyślne|Przeznaczenie|Obsługuje tokeny?|
|-|-|-|-|
|Ścieżka pliku wykonywalnego|dotnet|Plik wykonywalny do uruchomienia|Tak|
|CommandLineArgs —|Wartość właściwości programu MSBuild TargetPath zamapowana na środowisko WSL|Argumenty wiersza polecenia przekazane do ścieżka pliku wykonywalnego|Tak|
|workingDirectory|Dla aplikacji konsoli: {*OutDir*}</br>Dla aplikacji sieci Web: {*ProjectDir*}|Katalog roboczy, w którym ma zostać rozpoczęte debugowanie|Tak|
|environmentVariables||Pary wartości klucza zmiennych środowiskowych, które mają zostać ustawione dla debugowanego procesu.|Tak|
|setupScriptPath||Skrypt, który ma zostać uruchomiony przed debugowaniem. Przydatne do uruchamiania skryptów, takich jak ~/.bash_profile.|Tak|
|Nr dystrybucji||Nazwa dystrybucji WSL do użycia.|Nie|
|launchBrowser|fałsz|Określa, czy ma być uruchamiana przeglądarka|Nie|
|launchUrl||Adres URL do uruchomienia, jeśli launchBrowser ma wartość true|Nie|

Obsługiwane tokeny:

{*ProjectDir*} — ścieżka do katalogu projektu

{*OutDir*} — wartość właściwości MSBuild `OutDir`

>[!NOTE]
> Wszystkie ścieżki są przeznaczone dla WSL nie systemu Windows.
