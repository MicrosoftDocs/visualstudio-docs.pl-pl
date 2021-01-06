---
title: Instalowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zainstalować program Visual Studio, krok po kroku.
ms.date: 12/13/2019
ms.custom: contperf-fy21q1
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
ms.openlocfilehash: 2c3302499ec44d7a97ca66532428e0af117e3a7e
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903782"
---
# <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

::: moniker range="vs-2019"

Witamy w programie Visual Studio 2019! W tej wersji można łatwo wybrać i zainstalować tylko te funkcje, które są potrzebne. I ze względu na obniżoną minimalną wartość, jest ona instalowana szybko i z mniejszym wpływem na system.

::: moniker-end

::: moniker range="vs-2017"

Witamy w nowym sposobie instalacji programu Visual Studio! W tej wersji Ułatwiamy Wybieranie i Instalowanie tylko potrzebnych funkcji. Zmniejszono również minimalny zasięg programu Visual Studio, dzięki czemu jest on szybciej instalowany i z mniejszym wpływem na system niż kiedykolwiek wcześniej.

::: moniker-end

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Install Visual Studio dla komputerów Mac](/visualstudio/mac/installation/).

::: moniker range="vs-2019"

Chcesz dowiedzieć się więcej na temat Nowości w tej wersji? Zapoznaj się z naszymi [informacjami o wersji](/visualstudio/releases/2019/release-notes/).

::: moniker-end

::: moniker range="vs-2017"

Chcesz dowiedzieć się więcej na temat Nowości w tej wersji? Zapoznaj się z naszymi [informacjami o wersji](/visualstudio/releasenotes/vs2017-relnotes).

::: moniker-end

Jesteś gotowy do instalacji? Przeprowadzimy Cię przez ten krok po kroku.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1. Upewnij się, że komputer jest gotowy do programu Visual Studio

Przed rozpoczęciem instalacji programu Visual Studio:

::: moniker range="vs-2017"

1. Sprawdź [wymagania systemowe](/visualstudio/productinfo/vs2017-system-requirements-vs). Te wymagania pomagają sprawdzić, czy komputer obsługuje program Visual Studio 2017.

1. Zastosuj najnowsze aktualizacje systemu Windows. Te aktualizacje zapewniają, że komputer ma zarówno najnowsze aktualizacje zabezpieczeń, jak i wymagane składniki systemowe dla programu Visual Studio.

1. Ponowne uruchomienie. Ponowny rozruch zapewnia, że wszystkie oczekujące instalacje lub aktualizacje nie zakłócają instalacji programu Visual Studio.

1. Zwolnij miejsce. Usuń niepotrzebne pliki i aplikacje z dysku% SystemDrive%, na przykład uruchamiając aplikację Oczyszczanie dysku.

::: moniker-end

::: moniker range="vs-2019"

1. Sprawdź [wymagania systemowe](/visualstudio/releases/2019/system-requirements). Te wymagania pomagają sprawdzić, czy komputer obsługuje program Visual Studio 2019.

1. Zastosuj najnowsze aktualizacje systemu Windows. Te aktualizacje zapewniają, że komputer ma zarówno najnowsze aktualizacje zabezpieczeń, jak i wymagane składniki systemowe dla programu Visual Studio.

1. Ponowne uruchomienie. Ponowny rozruch zapewnia, że wszystkie oczekujące instalacje lub aktualizacje nie zakłócają instalacji programu Visual Studio.

1. Zwolnij miejsce. Usuń niepotrzebne pliki i aplikacje z dysku% SystemDrive%, na przykład uruchamiając aplikację Oczyszczanie dysku.

::: moniker-end

::: moniker range="vs-2017"

Pytania dotyczące uruchamiania wcześniejszych wersji programu Visual Studio obok programu Visual Studio 2017 zawiera temat [szczegóły zgodności programu Visual Studio](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

::: moniker-end

::: moniker range="vs-2019"

Pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok programu Visual Studio 2019 można znaleźć na stronie programu [Visual studio 2019 platformy docelowej i zgodności](/visualstudio/releases/2019/compatibility/) .

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Krok 2. Pobieranie programu Visual Studio

Następnie Pobierz plik programu inicjującego Visual Studio.

::: moniker range="vs-2017"

Aby uzyskać program inicjujący dla programu Visual Studio 2017, zobacz stronę pobierania [poprzednich wersji programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) , aby uzyskać szczegółowe informacje o tym, jak to zrobić.

::: moniker-end

::: moniker range="vs-2019"

Aby to zrobić, wybierz poniższy przycisk, wybierz wersję programu Visual Studio, a następnie wybierz pozycję **Zapisz**, a następnie wybierz pozycję **Otwórz folder**.

 > [!div class="button"]
 > [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 — Instalowanie Instalatora programu Visual Studio

Uruchom plik programu inicjującego, aby zainstalować Instalator programu Visual Studio. Ten nowy Lightweight Installer zawiera wszystko, czego potrzebujesz do zainstalowania i dostosowania programu Visual Studio.

1. W folderze **pobierania** kliknij dwukrotnie program inicjujący pasujący do jednego z następujących plików lub jest podobny do następującego:

   * **vs_community.exe** dla programu Visual Studio Community
   * **vs_professional.exe** Visual Studio Professional
   * **vs_enterprise.exe** Visual Studio Enterprise

   Jeśli zostanie wyświetlony komunikat Kontrola konta użytkownika, wybierz opcję **tak**.

2. Poprosimy o potwierdzenie [postanowień licencyjnych](https://visualstudio.microsoft.com/license-terms/) firmy Microsoft oraz [zasad zachowania poufności informacji](https://privacy.microsoft.com/privacystatement)firmy Microsoft. Wybierz pozycję **Kontynuuj**.

   ![Postanowienia licencyjne i zasady zachowania poufności informacji](media/privacy-and-license-terms.png "Postanowienia licencyjne i zasady zachowania poufności informacji firmy Microsoft")

## <a name="step-4---choose-workloads"></a>Krok 4. Wybieranie obciążeń

Po zainstalowaniu Instalatora można go użyć do dostosowania instalacji, wybierając zestawy funkcji — lub obciążenia, które chcesz. Oto jak to zrobić.

 ::: moniker range="vs-2017"

1. Znajdź żądane obciążenie w **Instalator programu Visual Studio**.

   ![Visual Studio 2017: Instalowanie obciążenia](../install/media/vs-installer-installing-workloads.png)

     Na przykład wybierz obciążenie "Programowanie aplikacji klasycznych platformy .NET". Jest on dostarczany z domyślnym edytorem podstawowym, który obejmuje podstawową obsługę edycji kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności stosowania projektu i zintegrowanej kontroli kodu źródłowego.

1. Po wybraniu żądanych obciążeń wybierz pozycję **Zainstaluj**.

    Następnie wyświetlane są ekrany stanu pokazujące postęp instalacji programu Visual Studio.

 ::: moniker-end

::: moniker range="vs-2019"

1. Znajdź żądane obciążenie w **Instalator programu Visual Studio**.

   ![Visual Studio 2019: Instalowanie obciążenia](../install/media/vs-2019/vs-installer-workloads.png)

     Na przykład wybierz obciążenie "Programowanie ASP.NET i sieci Web". Jest on dostarczany z domyślnym edytorem podstawowym, który obejmuje podstawową obsługę edycji kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności stosowania projektu i zintegrowanej kontroli kodu źródłowego.

1. Po wybraniu żądanych obciążeń wybierz pozycję **Zainstaluj**.

    Następnie wyświetlane są ekrany stanu pokazujące postęp instalacji programu Visual Studio.

 ::: moniker-end

> [!TIP]
> W dowolnym momencie po zakończeniu instalacji można zainstalować obciążenia lub składniki, które nie zostały wcześniej zainstalowane. Jeśli masz otwarty program Visual Studio, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje...** , co spowoduje otwarcie Instalator programu Visual Studio. Lub Otwórz **Instalator programu Visual Studio** z menu Start. W tym miejscu możesz wybrać obciążenia lub składniki, które chcesz zainstalować. Następnie wybierz **Modyfikuj**.

## <a name="step-5---choose-individual-components-optional"></a>Krok 5. Wybierz poszczególne składniki (opcjonalnie)

Jeśli nie chcesz używać funkcji obciążeń do dostosowywania instalacji programu Visual Studio lub chcesz dodać więcej składników niż w przypadku instalacji obciążeń, możesz to zrobić, instalując lub dodając poszczególne składniki z karty **poszczególne składniki** . Wybierz, co chcesz zrobić, a następnie postępuj zgodnie z monitami.

::: moniker range="vs-2017"

  ![Visual Studio 2017 — Zainstaluj poszczególne składniki](media/vs-installer-installing-components.png "Zainstaluj poszczególne składniki programu Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 — Zainstaluj poszczególne składniki](media/vs-2019/vs-installer-individual-components.png "Zainstaluj poszczególne składniki programu Visual Studio")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>Krok 6. Instalowanie pakietów językowych (opcjonalnie)

Domyślnie program instalacyjny próbuje dopasować język systemu operacyjnego, gdy jest uruchamiany po raz pierwszy. Aby zainstalować program Visual Studio w wybranym języku, wybierz kartę **pakiety językowe** z Instalator programu Visual Studio, a następnie postępuj zgodnie z monitami.

::: moniker range="vs-2017"

  ![Visual Studio 2017 — Zainstaluj pakiety językowe](media/vs-installer-installing-language-packs.png "Zainstaluj pakiety językowe programu Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 — Zainstaluj pakiety językowe](media/vs-2019/vs-installer-language-packs.png "Zainstaluj pakiety językowe programu Visual Studio")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Zmiana języka Instalatora z wiersza polecenia

Innym sposobem zmiany języka domyślnego jest uruchomienie Instalatora z wiersza polecenia. Na przykład można wymusić uruchomienie Instalatora w języku angielskim przy użyciu następującego polecenia: `vs_installer.exe --locale en-US` . Instalator zapamiętaje to ustawienie, gdy zostanie uruchomione następnym razem. Instalator obsługuje następujące tokeny języka: zh-CN, zh-TW, CS-Czechy, en-us, es-ES, fr-fr, de-de, IT-JP, ko-kr, pl-pl, pt-br, ru-RU i TR-tr.

## <a name="step-7---select-the-installation-location-optional"></a>Krok 7 — Wybieranie lokalizacji instalacji (opcjonalnie)

::: moniker range="vs-2017"

**Nowość w 15,7**: można teraz zmniejszyć zasięg instalacji programu Visual Studio na dysku systemowym. Możesz przenieść pamięć podręczną pobierania, składniki współużytkowane, zestawy SDK i narzędzia na inne dyski i pozostawić program Visual Studio na dysku, na którym jest on uruchomiony najszybciej.

  ![Visual Studio 2017 — Zmień lokalizacje instalacji](media/installation-options-by-location.png "Zmień lokalizację instalacji")

::: moniker-end

::: moniker range="vs-2019"

Możesz zmniejszyć zasięg instalacji programu Visual Studio na dysku systemowym. Możesz przenieść pamięć podręczną pobierania, składniki współużytkowane, zestawy SDK i narzędzia na inne dyski i pozostawić program Visual Studio na dysku, na którym jest on uruchomiony najszybciej.

  ![Visual Studio 2019 — Wybieranie lokalizacji instalacji](media/vs-2019/vs-installer-installation-locations.png "Wybierz lokalizację instalacji")

::: moniker-end

> [!IMPORTANT]
> Inny dysk można wybrać tylko podczas pierwszej instalacji programu Visual Studio. Jeśli został już zainstalowany i chcesz zmienić dyski, należy odinstalować program Visual Studio, a następnie zainstalować go ponownie.

Aby uzyskać więcej informacji, zobacz stronę [Wybieranie lokalizacji instalacji](change-installation-locations.md) .

## <a name="step-8---start-developing"></a>Krok 8. Rozpoczynanie tworzenia

::: moniker range="vs-2017"

1. Po zakończeniu instalacji programu Visual Studio wybierz przycisk **Uruchom** , aby rozpocząć programowanie przy użyciu programu Visual Studio.

2. Wybierz pozycję **plik**, a następnie wybierz pozycję **Nowy projekt**.

3. Wybierz typ projektu.

   Na przykład, aby [skompilować aplikację w języku C++](/cpp/get-started/tutorial-console-cpp), wybierz pozycję **zainstalowane**, rozwiń węzeł **Visual C++**, a następnie wybierz typ projektu C++, który chcesz skompilować.

   Aby [skompilować aplikację w języku C#](../get-started/csharp/tutorial-console.md), wybierz pozycję **zainstalowane**, rozwiń pozycję **Visual C#**, a następnie wybierz typ projektu C#, który chcesz skompilować.

::: moniker-end

::: moniker range="vs-2019"

1. Po zakończeniu instalacji programu Visual Studio wybierz przycisk **Uruchom** , aby rozpocząć programowanie przy użyciu programu Visual Studio.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

1. W polu wyszukiwania wprowadź typ aplikacji, którą chcesz utworzyć, aby wyświetlić listę dostępnych szablonów. Lista szablonów zależy od obciążeń, które zostały wybrane podczas instalacji. Aby wyświetlić różne szablony, wybierz różne obciążenia.

   Wyszukiwanie w określonym języku programowania można również filtrować za pomocą listy rozwijanej **Język** . Można również filtrować za pomocą listy **platform** i listy **Typ projektu** .

1. Program Visual Studio otwiera nowy projekt i wszystko jest gotowe do kodu!

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Instalowanie programu Visual Studio dla komputerów Mac](/visualstudio/mac/installation)
 