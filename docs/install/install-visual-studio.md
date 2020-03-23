---
title: Instalacja programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zainstalować program Visual Studio krok po kroku.
ms.date: 12/13/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d8e6e3a857c9bbf5577cf395f698f64cfb11bddc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302995"
---
# <a name="install-visual-studio"></a>Instalacja programu Visual Studio

::: moniker range="vs-2019"

Witamy w programie Visual Studio 2019! W tej wersji łatwo jest wybrać i zainstalować tylko te funkcje, których potrzebujesz. A ze względu na zmniejszony minimalny zasięg instalacji, instaluje się szybko i przy mniejszym wpływie na system.

::: moniker-end

::: moniker range="vs-2017"

Witamy w nowym sposobie instalowania programu Visual Studio! W tej wersji ułatwiliśmy ci wybór i zainstalowanie tylko tych funkcji, których potrzebujesz. Firma Ve również zmniejszyć minimalny rozmiar programu Visual Studio, dzięki czemu instaluje się szybciej i mniej wpływu na system niż kiedykolwiek wcześniej.

::: moniker-end

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. Aby zapoznać się z programem Visual Studio dla komputerów Mac, zobacz [Instalowanie programu Visual Studio dla komputerów Mac](/visualstudio/mac/installation/).

::: moniker range="vs-2019"

Chcesz dowiedzieć się więcej o tym, co jeszcze jest nowe w tej wersji? Zobacz nasze [informacje o wersji](/visualstudio/releases/2019/release-notes/).

::: moniker-end

::: moniker range="vs-2017"

Chcesz dowiedzieć się więcej o tym, co jeszcze jest nowe w tej wersji? Zobacz nasze [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).

::: moniker-end

Gotowy do instalacji? Przejdziemy przez to krok po kroku.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1 - Upewnij się, że komputer jest gotowy do programu Visual Studio

Przed rozpoczęciem instalowania programu Visual Studio:

::: moniker range="vs-2017"

1. Sprawdź [wymagania systemowe](/visualstudio/productinfo/vs2017-system-requirements-vs). Te wymagania pomagają sprawdzić, czy komputer obsługuje program Visual Studio 2017.

1. Zastosuj najnowsze aktualizacje systemu Windows. Te aktualizacje zapewniają, że komputer ma zarówno najnowsze aktualizacje zabezpieczeń, jak i wymagane składniki systemu dla programu Visual Studio.

1. Ponownie obuwać. Ponowne uruchomienie gwarantuje, że wszelkie oczekujące instalacje lub aktualizacje nie utrudniają instalacji programu Visual Studio.

1. Zwolnić miejsce. Usuń niepotrzebne pliki i aplikacje z %SystemDrive% na przykład przez uruchomienie aplikacji Oczyszczanie dysku.

::: moniker-end

::: moniker range="vs-2019"

1. Sprawdź [wymagania systemowe](/visualstudio/releases/2019/system-requirements). Te wymagania pomagają sprawdzić, czy komputer obsługuje program Visual Studio 2019.

1. Zastosuj najnowsze aktualizacje systemu Windows. Te aktualizacje zapewniają, że komputer ma zarówno najnowsze aktualizacje zabezpieczeń, jak i wymagane składniki systemu dla programu Visual Studio.

1. Ponownie obuwać. Ponowne uruchomienie gwarantuje, że wszelkie oczekujące instalacje lub aktualizacje nie utrudniają instalacji programu Visual Studio.

1. Zwolnić miejsce. Usuń niepotrzebne pliki i aplikacje z %SystemDrive% na przykład przez uruchomienie aplikacji Oczyszczanie dysku.

::: moniker-end

::: moniker range="vs-2017"

Aby uzyskać pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok programu Visual Studio 2017, zobacz [szczegóły zgodności programu Visual Studio.](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases)

::: moniker-end

::: moniker range="vs-2019"

Aby uzyskać pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok programu Visual Studio 2019, zobacz stronę [Kierowania i zgodność platformy programu Visual Studio 2019.](/visualstudio/releases/2019/compatibility/)

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Krok 2 - Pobierz program Visual Studio

Następnie pobierz plik programu Visual Studio.

::: moniker range="vs-2017"

Aby uzyskać program uruchamiany dla programu Visual Studio 2017, zobacz stronę pobierania [poprzednich wersji programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/) aby uzyskać szczegółowe informacje na ten temat.

::: moniker-end

::: moniker range="vs-2019"

Aby to zrobić, wybierz następujący przycisk, wybierz odpowiednią wersję programu Visual Studio, wybierz pozycję **Zapisz**, a następnie wybierz pozycję **Otwórz folder**.

 > [!div class="button"]
 > [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 - Instalowanie instalatora programu Visual Studio

Uruchom plik programu bootstrapper, aby zainstalować Instalatora programu Visual Studio. Ten nowy lekki instalator zawiera wszystko, czego potrzebujesz do instalowania i dostosowywania programu Visual Studio.

1. W folderze **Pobrane** kliknij dwukrotnie program uruchamiany, który pasuje lub jest podobny do jednego z następujących plików:

   * **vs_community.exe** dla społeczności programu Visual Studio
   * **vs_professional.exe** dla programu Visual Studio Professional
   * **vs_enterprise.exe** dla programu Visual Studio Enterprise

   Jeśli otrzymasz powiadomienie o kontroli konta użytkownika, wybierz opcję **Tak**.

2. Prosimy o uznanie [postanowień licencyjnych](https://visualstudio.microsoft.com/license-terms/) firmy Microsoft i [Zasad zachowania poufności informacji firmy](https://privacy.microsoft.com/privacystatement)Microsoft. Wybierz pozycję **Kontynuuj**.

   ![Postanowienia licencyjne i Zasady zachowania poufności informacji](media/privacy-and-license-terms.png "Postanowienia licencyjne i zasady zachowania poufności informacji firmy Microsoft")

## <a name="step-4---choose-workloads"></a>Krok 4 - Wybieranie obciążeń

Po zainstalowaniu instalatora można go użyć do dostosowania instalacji, wybierając zestawy funkcji lub obciążenia, które mają być. Oto jak to zrobić.

 ::: moniker range="vs-2017"

1. Znajdź żądane obciążenie w **Instalatorze programu Visual Studio**.

   ![Visual Studio 2017: instalowanie obciążenia](../install/media/vs-installer-installing-workloads.png)

     Na przykład wybierz ".NET rozwoju pulpitu" obciążenia. Jest wyposażony w domyślny edytor rdzenia, który zawiera podstawową obsługę edycji kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności tworzenia projektu oraz zintegrowaną kontrolę kodu źródłowego.

1. Po wybraniu żądanych obciążeń wybierz pozycję **Zainstaluj**.

    Następnie pojawiają się ekrany stanu, które pokazują postęp instalacji programu Visual Studio.

 ::: moniker-end

::: moniker range="vs-2019"

1. Znajdź żądane obciążenie w **Instalatorze programu Visual Studio**.

   ![Visual Studio 2019: instalowanie obciążenia](../install/media/vs-2019/vs-installer-workloads.png)

     Na przykład wybierz obciążenie "ASP.NET i tworzenia sieci Web". Jest wyposażony w domyślny edytor rdzenia, który zawiera podstawową obsługę edycji kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności tworzenia projektu oraz zintegrowaną kontrolę kodu źródłowego.

1. Po wybraniu żądanych obciążeń wybierz pozycję **Zainstaluj**.

    Następnie pojawiają się ekrany stanu, które pokazują postęp instalacji programu Visual Studio.

 ::: moniker-end

> [!TIP]
> W dowolnym momencie po instalacji można zainstalować obciążenia lub składniki, które nie zostały zainstalowane początkowo. Jeśli masz otwarty program Visual Studio, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje ...** który otwiera Instalatora programu Visual Studio. Lub otwórz **Instalatora programu Visual Studio** z menu Start. W tym miejscu można wybrać obciążenia lub składniki, które chcesz zainstalować. Następnie wybierz pozycję **Modyfikuj**.

## <a name="step-5---choose-individual-components-optional"></a>Krok 5 - Wybór poszczególnych komponentów (opcjonalnie)

Jeśli nie chcesz używać funkcji Obciążenia, aby dostosować instalację programu Visual Studio lub chcesz dodać więcej składników niż instaluje obciążenie, można to zrobić, instalując lub dodając poszczególne składniki z karty **Poszczególne składniki.**

::: moniker range="vs-2017"

  ![Visual Studio 2017 — instalowanie poszczególnych składników](media/vs-installer-installing-components.png "Instalowanie poszczególnych składników programu Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 — instalowanie poszczególnych składników](media/vs-2019/vs-installer-individual-components.png "Instalowanie poszczególnych składników programu Visual Studio")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>Krok 6 - Instalowanie pakietów językowych (opcjonalnie)

Domyślnie program instalacyjny próbuje dopasować język systemu operacyjnego, gdy działa po raz pierwszy. Aby zainstalować program Visual Studio w wybranym języku, wybierz kartę **Pakiety językowe** z Instalatora programu Visual Studio, a następnie postępuj zgodnie z instrukcjami.

::: moniker range="vs-2017"

  ![Visual Studio 2017 — instalowanie pakietów językowych](media/vs-installer-installing-language-packs.png "Instalowanie pakietów językowych programu Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 — instalowanie pakietów językowych](media/vs-2019/vs-installer-language-packs.png "Instalowanie pakietów językowych programu Visual Studio")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Zmienianie języka instalatora z wiersza polecenia

Innym sposobem zmiany języka domyślnego jest uruchomienie instalatora z wiersza polecenia. Na przykład można wymusić uruchomienie instalatora w języku angielskim `vs_installer.exe --locale en-US`za pomocą następującego polecenia: . Instalator zapamięta to ustawienie, gdy zostanie uruchomione następnym razem. Instalator obsługuje następujące tokeny językowe: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru i tr-tr.

## <a name="step-7---select-the-installation-location-optional"></a>Krok 7 - Wybierz miejsce instalacji (opcjonalnie)

::: moniker range="vs-2017"

**Nowość w wersji 15.7**: Można teraz zmniejszyć rozmiar instalacji programu Visual Studio na dysku systemowym. Można przenieść pamięć podręczną pobierania, składniki udostępnione, zestawY SDK i narzędzia na różne dyski i zachować program Visual Studio na dysku, który uruchamia go najszybciej.

  ![Visual Studio 2017 — zmienianie lokalizacji instalacji](media/installation-options-by-location.png "Zmienianie lokalizacji instalacji")

::: moniker-end

::: moniker range="vs-2019"

Można zmniejszyć rozmiar instalacji programu Visual Studio na dysku systemowym. Można przenieść pamięć podręczną pobierania, składniki udostępnione, zestawY SDK i narzędzia na różne dyski i zachować program Visual Studio na dysku, który uruchamia go najszybciej.

  ![Visual Studio 2019 — wybieranie lokalizacji instalacji](media/vs-2019/vs-installer-installation-locations.png "Wybierz lokalizację instalacji")

::: moniker-end

> [!IMPORTANT]
> Inny dysk można wybrać tylko przy pierwszej instalacji programu Visual Studio. Jeśli masz już zainstalowany i chcesz zmienić dyski, należy odinstalować program Visual Studio, a następnie ponownie zainstalować go.

Aby uzyskać więcej informacji, zobacz stronę [Wybieranie lokalizacji instalacji.](change-installation-locations.md)

## <a name="step-8---start-developing"></a>Krok 8 - Rozpoczęcie tworzenia

::: moniker range="vs-2017"

1. Po zakończeniu instalacji programu Visual Studio wybierz przycisk **Uruchom,** aby rozpocząć tworzenie za pomocą programu Visual Studio.

2. Wybierz **pozycję Plik**, a następnie wybierz pozycję Nowy **projekt**.

3. Wybierz typ projektu.

   Na przykład, aby [utworzyć aplikację Języka C++,](/cpp/get-started/tutorial-console-cpp)wybierz pozycję **Zainstalowano,** rozwiń **język Visual C++,** a następnie wybierz typ projektu C++, który chcesz utworzyć.

   Aby [utworzyć aplikację języka C#,](../get-started/csharp/tutorial-console.md)wybierz pozycję **Zainstalowano,** rozwiń **pozycję Visual C#,** a następnie wybierz typ projektu C#, który chcesz utworzyć.

::: moniker-end

::: moniker range="vs-2019"

1. Po zakończeniu instalacji programu Visual Studio wybierz przycisk **Uruchom,** aby rozpocząć tworzenie za pomocą programu Visual Studio.

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

1. W polu wyszukiwania wprowadź typ aplikacji, którą chcesz utworzyć, aby wyświetlić listę dostępnych szablonów. Lista szablonów zależy od obciążenia wybranego podczas instalacji. Aby wyświetlić różne szablony, wybierz różne obciążenia.

   Wyszukiwanie w poszukiwaniu określonego języka programowania można również filtrować za pomocą listy rozwijanej **Język.** Można filtrować przy użyciu **platformy** listy i listy **typu projektu,** zbyt.

1. Visual Studio otwiera nowy projekt i jesteś gotowy do kodu!

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
* [Tworzenie instalacji programu Visual Studio w trybie offline](create-an-offline-installation-of-visual-studio.md)
* [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md)
* [Instalowanie programu Visual Studio dla komputerów Mac](/visualstudio/mac/installation)
