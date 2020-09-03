---
title: Znajdowanie i używanie rozszerzeń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: df6219a66b0f6c85e197b209741706abc7ce3d06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655879"
---
# <a name="finding-and-using-visual-studio-extensions"></a>Znajdowanie rozszerzeń programu Visual Studio i korzystanie z nich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozszerzenia programu Visual Studio to pakiety kodu, które działają w programie Visual Studio i udostępniają nowe lub udoskonalone funkcje programu Visual Studio. Więcej informacji na temat rozszerzeń programu Visual Studio można znaleźć tutaj: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Można użyć okna dialogowego **rozszerzenia i aktualizacje** , aby zainstalować rozszerzenia programu Visual Studio i przykłady z witryn sieci Web i innych lokalizacji, a następnie włączyć, wyłączyć, zaktualizować lub odinstalować je. (**Narzędzia/rozszerzenia i aktualizacje**lub **rozszerzenia** typu w oknie **Szybkie uruchamianie** ). W oknie dialogowym są również wyświetlane aktualizacje zainstalowanych przykładów i rozszerzeń. Możesz również pobrać rozszerzenia z witryn sieci Web lub pobrać je od innych deweloperów.

> [!NOTE]
> Począwszy od programu Visual Studio 2015, rozszerzenia hostowane w galerii programu Visual Studio zostaną automatycznie zaktualizowane.  To ustawienie można zmienić za pomocą okna dialogowego **rozszerzenia i aktualizacje** .  Aby uzyskać szczegółowe informacje, zobacz sekcję dotyczącą **automatycznych aktualizacji rozszerzeń** poniżej.

## <a name="finding-visual-studio-extensions"></a>Znajdowanie rozszerzeń programu Visual Studio
 Możesz zainstalować rozszerzenia z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub z [galerii przykładów](https://code.msdn.microsoft.com/vstudio) w witrynie sieci Web firmy Microsoft. Rozszerzeniami mogą być formanty, przykłady, szablony, narzędzia lub inne składniki, które dodają nowe funkcjonalności do programu Visual Studio. Program Visual Studio obsługuje rozszerzenia w formacie pakietu VSIX — obejmują one szablony projektów, szablony elementów, elementy **przybornika** , składniki Managed Extension Framework (MEF) i pakietów VSPackage. Można również pobrać i zainstalować rozszerzenia oparte na MSI, ale okno dialogowe **rozszerzenia i aktualizacje** nie może włączać ani wyłączać. Galeria programu Visual Studio zawiera rozszerzenia VSIX i MSI.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Instalowanie lub odinstalowywanie rozszerzeń programu Visual Studio
 W obszarze **rozszerzenia i aktualizacje**Znajdź rozszerzenie, które chcesz zainstalować. (Jeśli znasz nazwę lub część nazwy rozszerzenia, możesz wyszukać w oknie **Galeria wyszukiwania programu Visual Studio** ). Kliknij przycisk **Pobierz**, a następnie **Zainstaluj**. Aby załadować rozszerzenie, należy ponownie uruchomić program Visual Studio.

 Podczas próby instalacji rozszerzenia, które ma zależności, instalator sprawdza, czy są one już zainstalowane. Jeśli nie są zainstalowane, okno dialogowe **rozszerzenia i aktualizacje** zawiera listę zależności, które należy zainstalować przed zainstalowaniem rozszerzenia.

 Jeśli nie chcesz już dłużej używać rozszerzenia, możesz je wyłączyć lub odinstalować. Wyłączone rozszerzenie jest wciąż zainstalowane, ale nie jest załadowane. Można wyłączyć tylko rozszerzenia VSIX; rozszerzenia, które zostały zainstalowane przy użyciu pliku MSI, można odinstalować tylko. Znajdź rozszerzenie, a następnie kliknij przycisk **Odinstaluj** lub **Wyłącz**. Musisz ponownie uruchomić program Visual Studio, aby zwolnić wyłączone rozszerzenie.

## <a name="per-user-and-administrative-extensions"></a>Rozszerzenia administracyjne i dla poszczególnych użytkowników
 Większość rozszerzeń jest rozszerzeniami poszczególnych użytkowników i są instalowane w folderze **%LocalAppData%\Microsoft\VisualStudio \\<programu Visual Studio w wersji \> \Extensions \\ ** . Niektóre rozszerzenia są rozszerzeniami administracyjnymi i są zainstalowane w folderze ** \<Visual Studio installation folder> \Common7\IDE\Extensions \\ ** .

 Aby chronić system przed rozszerzeniami, które mogą zawierać błędy lub złośliwy kod, można ograniczyć rozszerzenia dla poszczególnych użytkowników tylko wtedy, gdy program Visual Studio jest uruchamiany z normalnymi uprawnieniami użytkownika. Oznacza to, że rozszerzenia dla poszczególnych użytkowników są wyłączone, gdy program Visual Studio jest uruchamiany z uprawnieniami użytkownika administracyjnego. W tym celu przejdź do strony opcje **rozszerzeń i aktualizacji** (**Narzędzia/Opcje**, **środowisko**, **rozszerzenia i aktualizacje**lub po prostu wpisz **rozszerzenie** w oknie **Szybkie uruchamianie** ). Wyczyść pole wyboru **Załaduj rozszerzenia na użytkownika podczas uruchamiania jako administrator** , a następnie uruchom ponownie program Visual Studio.

## <a name="automatic-extension-updates"></a>Automatyczne aktualizacje rozszerzeń
 Rozszerzenia dla poszczególnych użytkowników są automatycznie aktualizowane, gdy nowa wersja jest dostępna w galerii programu Visual Studio.  Nowa wersja rozszerzenia zostanie wykryta i zainstalowana w tle, a po następnym ponownym uruchomieniu programu Visual Studio zostanie uruchomiona nowa wersja rozszerzenia.

 Tylko rozszerzenia poszczególnych użytkowników mogą być aktualizowane automatycznie.  Rozszerzenia administracyjne, które są zainstalowane dla wszystkich użytkowników, nie będą aktualizowane i nadal ręcznie instalują nowe wersje za pomocą węzła **aktualizacje** okna dialogowego **rozszerzenia i aktualizacje** . Możesz zobaczyć, które rozszerzenia zostaną automatycznie zaktualizowane w okienku szczegółów rozszerzenia okna dialogowego **rozszerzenia i aktualizacje** .

 Jeśli chcesz wyłączyć aktualizacje automatyczne, możesz wyłączyć tę funkcję dla wszystkich rozszerzeń lub tylko określonych rozszerzeń.

- Aby wyłączyć aktualizacje automatyczne dla wszystkich rozszerzeń, kliknij link **Zmień ustawienia rozszerzeń i aktualizacji** w oknie dialogowym **rozszerzenia i aktualizacje** , a następnie usuń zaznaczenie pola **automatycznie Aktualizuj rozszerzenia**.

- Aby wyłączyć aktualizacje automatyczne dla określonego rozszerzenia, usuń zaznaczenie pola wyboru **automatycznie Aktualizuj to rozszerzenie** w okienku szczegółów rozszerzenia po prawej stronie okna dialogowego **rozszerzenia i aktualizacje** .

> [!NOTE]
> Począwszy od programu Visual Studio 2015 Update 2, można określić (w obszarze **Narzędzia/Opcje/środowisko/rozszerzenia i aktualizacje**), czy aktualizacje automatyczne mają być ustawiane dla rozszerzeń dla poszczególnych użytkowników, wszystkich rozszerzeń użytkowników, czy obu (ustawienie domyślne).

## <a name="sample-master-copies-and-working-copies"></a>Przykładowe kopie główne i kopie robocze
 Po zainstalowaniu przykładu online, rozwiązanie jest przechowywane w dwóch miejscach:

- Kopia robocza jest przechowywana w lokalizacji określonej w oknie dialogowym **Nowy projekt** .

- Oddzielna kopia główna jest przechowywana na komputerze.

  Za pomocą okna dialogowego **rozszerzenia i aktualizacje** można wykonywać następujące zadania związane z przykładami:

- Wypisanie listy kopii głównych przykładów, które zostały zainstalowane.

- Wyłączenie lub odinstalowanie kopii głównej przykładu.

- Zainstalowanie pakietów przykładów, które są zbiorami przykładów odnoszących się do technologii lub funkcji.

- Instalowanie pojedynczych przykładów online. (Można to również zrobić w oknie dialogowym **Nowy projekt** ).

- Wyświetlanie powiadomień o aktualizacjach, gdy zostaną opublikowane zmiany kodu źródłowego dla zainstalowanych przykładów.

- Zaktualizuj główną kopię zainstalowanego przykładu w przypadku powiadomienia o aktualizacji.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalowanie bez używania okna dialogowego Rozszerzenia i aktualizacje
 Rozszerzenia, które zostały spakowane do plików .vsix, mogą być dostępne w lokalizacjach innych niż galeria programu Visual Studio. Okna dialogowego **rozszerzenia i aktualizacje** nie mogą wykryć tych plików, ale można zainstalować plik. vsix, klikając dwukrotnie plik lub wybierając plik i naciskając klawisz ENTER. Następnie postępuj zgodnie z instrukcjami. Po zainstalowaniu rozszerzenia można użyć okna dialogowego **rozszerzenia i aktualizacje** , aby je włączyć, wyłączyć lub odinstalować.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Typy rozszerzeń nieobsługiwane przez okno dialogowe rozszerzenia i aktualizacje
 Program Visual Studio w dalszym ciągu obsługuje rozszerzenia, które są instalowane przez Instalatora Microsoft (MSI), ale nie za pomocą okna dialogowego **rozszerzenia i aktualizacje** bez żadnych modyfikacji.

> [!TIP]
> Jeśli rozszerzenie programu MSI zawiera plik rozszerzenia. vsixmanifest, rozszerzenie pojawi się w oknie dialogowym **rozszerzenia i aktualizacje** .
