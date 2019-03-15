---
title: Znajdowanie rozszerzeń i korzystanie z | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bae12b01a8fc1c879526bbf5df568c9ec40041c9
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867764"
---
# <a name="finding-and-using-visual-studio-extensions"></a>Znajdowanie rozszerzeń programu Visual Studio i korzystanie z nich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozszerzenia programu Visual Studio są pakiety kodu, które są uruchamiane w programie Visual Studio i udostępnia nowe i ulepszone funkcje programu Visual Studio. Można znaleźć więcej informacji na temat rozszerzeń programu Visual Studio tutaj: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Możesz użyć **rozszerzenia i aktualizacje** okno dialogowe, aby zainstalować rozszerzenia programu Visual Studio i przykłady z witryn sieci Web i innych lokalizacji, a następnie włączyć, wyłączyć, aktualizacji lub odinstaluj je. (**Narzędzia / rozszerzenia i aktualizacje**, lub typu **rozszerzenia** w **Szybkie uruchamianie** okno). Okno dialogowe zawiera również aktualizacje do zainstalowanych przykładów i rozszerzenia. Można również pobrać rozszerzenia z witryny sieci Web lub pobrać je z innymi deweloperami.

> [!NOTE]
>  Począwszy od programu Visual Studio 2015, rozszerzenia w galerii Visual Studio w serwisie zostaną automatycznie zaktualizowane.  Można zmienić tego ustawienia za pomocą **rozszerzenia i aktualizacje** okna dialogowego.  Zobacz sekcję dotyczącą **automatyczne aktualizacje rozszerzeń** poniżej szczegółowe informacje.

## <a name="finding-visual-studio-extensions"></a>Znajdowanie rozszerzeń programu Visual Studio
 Można zainstalować rozszerzenia z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub [galerii przykładów](https://code.msdn.microsoft.com/vstudio) w witrynie internetowej firmy Microsoft. Rozszerzeniami mogą być formanty, przykłady, szablony, narzędzia lub inne składniki, które dodają nowe funkcjonalności do programu Visual Studio. Program Visual Studio obsługuje rozszerzenia w formacie pakietu VSIX — te obejmują szablony projektów, szablony elementów, elementy **przybornika** elementów, składniki zarządzane rozszerzenia Framework (MEF) i pakiety VSPackages. Można również pobrać i zainstalować rozszerzenia na podstawie tożsamości usługi Zarządzanej, ale **rozszerzenia i aktualizacje** okno dialogowe nie można je włączyć lub wyłączyć. W galerii Visual Studio zawiera rozszerzenia MSI i VSIX.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Instalowanie lub odinstalowywanie rozszerzenia programu Visual Studio
 W **rozszerzenia i aktualizacje**, znaleźć rozszerzenia, którą chcesz zainstalować. (Jeśli znasz nazwę lub część nazwy rozszerzenia, możesz wyszukiwać w **wyszukiwania galerii programu Visual Studio** okna.) Kliknij przycisk **Pobierz**, następnie **zainstalować**. Aby załadować rozszerzenie, należy ponownie uruchomić program Visual Studio.

 Podczas próby instalacji rozszerzenia, które ma zależności, instalator sprawdza, czy są one już zainstalowane. Jeśli nie są zainstalowane, **rozszerzenia i aktualizacje** okno dialogowe zawiera listę zależności, które muszą być zainstalowane, zanim będzie można zainstalować rozszerzenia.

 Jeśli nie chcesz już dłużej używać rozszerzenia, możesz je wyłączyć lub odinstalować. Wyłączone rozszerzenie jest wciąż zainstalowane, ale nie jest załadowane. Można wyłączyć tylko rozszerzenia VSIX; rozszerzenia, które zostały zainstalowane za pomocą Instalatora MSI można tylko odinstalować. Znaleźć rozszerzenia, a następnie kliknij przycisk **Odinstaluj** lub **wyłączyć**. Aby zwolnić wyłączone rozszerzenie, należy ponownie uruchomić program Visual Studio.

## <a name="per-user-and-administrative-extensions"></a>Rozszerzenia administracyjne i dla poszczególnych użytkowników
 Większość rozszerzeń to rozszerzenia dla poszczególnych użytkowników i są instalowane w **%LocalAppData%\Microsoft\VisualStudio\\< wersja programu Visual Studio\>\Extensions\\**  folderu. Kilka rozszerzeń to rozszerzenia administracyjne i są instalowane w **\<folder instalacji programu Visual Studio > \Common7\IDE\Extensions\\** folderu.

 Aby chronić system przed rozszerzeniami, które mogą zawierać błędy lub złośliwy kod, można ograniczyć rozszerzenia dla poszczególnych użytkowników można załadować tylko wtedy, gdy program Visual Studio jest uruchamiany z uprawnieniami zwykłego użytkownika. Oznacza to, że rozszerzenia dla poszczególnych użytkowników są wyłączone, po uruchomieniu programu Visual Studio z uprawnieniami administratora. Aby to zrobić, przejdź do **rozszerzenia i aktualizacje** Strona opcji (**narzędzia / Opcje**, **środowiska**, **rozszerzenia i aktualizacje**, lub po prostu Typ **rozszerzenia** w **Szybkie uruchamianie** okno). Wyczyść **obciążenia rozszerzenia dla poszczególnych użytkowników podczas uruchamiania jako administrator** pole wyboru, a następnie uruchom ponownie program Visual Studio.

## <a name="automatic-extension-updates"></a>Aktualizacje automatyczne rozszerzenia
 Rozszerzenia dla poszczególnych użytkowników są automatycznie aktualizowane, gdy nowa wersja jest dostępna w galerii Visual Studio.  Nowa wersja rozszerzenia są wykrywane i zainstalowane w tle, a przy następnym ponownym uruchomieniu programu Visual Studio, nowa wersja rozszerzenia zostanie uruchomiona.

 Tylko rozszerzenia dla poszczególnych użytkowników można automatycznie aktualizować.  Rozszerzenia administracyjne, które są instalowane dla wszystkich użytkowników nie będzie aktualizowana i nadal ręcznie zainstalować nowe wersje za pośrednictwem **rozszerzenia i aktualizacje** okna dialogowego **aktualizacje** węzła. Możesz zobaczyć, jakie rozszerzenia zostaną automatycznie zaktualizowane w okienku szczegółów rozszerzenia **rozszerzenia i aktualizacje** okna dialogowego.

 Jeśli chcesz wyłączyć automatyczne aktualizacje, można wyłączyć funkcję dla wszystkich rozszerzeń lub tylko określone rozszerzenia.

-   Aby wyłączyć aktualizacje automatyczne dla wszystkich rozszerzeń, kliknij przycisk **zmiany ustawień rozszerzenia i aktualizacje** link **rozszerzenia i aktualizacje** okna dialogowego i usuń zaznaczenie pola wyboru **automatycznego aktualizowania rozszerzenia**.

-   Aby wyłączyć automatyczne aktualizacje dla określonego rozszerzenia, usuń zaznaczenie pola wyboru **automatycznie Aktualizuj to rozszerzenie** opcji w okienku szczegółów rozszerzenia na prawej krawędzi **rozszerzenia i aktualizacje** okna dialogowego.

> [!NOTE]
>  Począwszy od programu Visual Studio 2015 Update 2, można określić (w **narzędzia / Opcje / środowisko / rozszerzenia i aktualizacje**) czy będzie automatyczne aktualizacje dla rozszerzenia dla poszczególnych użytkowników, wszystkie rozszerzenia użytkowników lub obie (ustawienie domyślne).

## <a name="sample-master-copies-and-working-copies"></a>Kopie główne próbki i kopie robocze
 Po zainstalowaniu przykładu online, rozwiązanie jest przechowywane w dwóch miejscach:

- Kopia robocza jest przechowywany w lokalizacji określonej w **nowy projekt** okno dialogowe.

- Oddzielna kopia główna jest przechowywana na komputerze.

  Możesz użyć **rozszerzenia i aktualizacje** okno dialogowe do wykonania tych zadań związanych z przykładami:

- Wypisanie listy kopii głównych przykładów, które zostały zainstalowane.

- Wyłączenie lub odinstalowanie kopii głównej przykładu.

- Zainstalowanie pakietów przykładów, które są zbiorami przykładów odnoszących się do technologii lub funkcji.

- Instalowanie pojedynczych przykładów online. (Można to również zrobić w **nowy projekt** okno dialogowe.)

- Wyświetlanie powiadomień o aktualizacjach, gdy zostaną opublikowane zmiany kodu źródłowego dla zainstalowanych przykładów.

- Aktualizowanie kopii głównej zainstalowanego przykładu, po powiadomienie o aktualizacji.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalowanie bez używania okna dialogowego Rozszerzenia i aktualizacje
 Rozszerzenia, które zostały spakowane do plików .vsix, mogą być dostępne w lokalizacjach innych niż galeria programu Visual Studio. **Rozszerzenia i aktualizacje** okno dialogowe nie może wykryć tych plików, ale można zainstalować plik .vsix, klikając dwukrotnie plik, lub wybierając plik i naciskając klawisz ENTER. Następnie postępuj zgodnie z instrukcjami. Jeśli rozszerzenie jest zainstalowane, możesz użyć **rozszerzenia i aktualizacje** okno dialogowe, aby ją włączyć, wyłączyć lub odinstaluj je.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Typy rozszerzeń, które nie są obsługiwane przez rozszerzenia i aktualizacje okno dialogowe
 Program Visual Studio w dalszym ciągu obsługuje rozszerzenia, które są instalowane przez Instalator (MSI) programu Microsoft ale nie za pomocą **rozszerzenia i aktualizacje** okno dialogowe bez żadnych modyfikacji.

> [!TIP]
>  Jeśli rozszerzenie opartym na MSI zawierają pliku extension.vsixmanifest, rozszerzenia pojawią się w **rozszerzenia i aktualizacje** okno dialogowe.
