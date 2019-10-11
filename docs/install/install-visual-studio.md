---
title: Instalowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zainstalować program Visual Studio, krok po kroku.
ms.date: 10/07/2019
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6cd91fadea397955b756461383ed8e17030b4c3b
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018852"
---
# <a name="install-visual-studio"></a>Instalacja programu Visual Studio

::: moniker range="vs-2019"

Witamy w programie Visual Studio 2019! W tej wersji można łatwo wybrać i zainstalować tylko te funkcje, które są potrzebne. I ze względu na obniżoną minimalną wartość, jest ona instalowana szybko i z mniejszym wpływem na system.

::: moniker-end

::: moniker range="vs-2017"

Nowy sposób instalowania programu Visual Studio — Zapraszamy! W tej wersji Ułatwiamy Wybieranie i Instalowanie tylko potrzebnych funkcji. Również zmniejszyliśmy minimalnego śladu programu Visual Studio, tak aby zainstalował szybciej i z mniejszym wpływem na system niż kiedykolwiek wcześniej.

::: moniker-end

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [Zainstaluj program Visual Studio dla komputerów Mac](/visualstudio/mac/installation/).

::: moniker range="vs-2019"

Chcesz dowiedzieć się więcej na temat inne nowości w tej wersji? Zobacz nasze [informacje o wersji](/visualstudio/releases/2019/release-notes/).

::: moniker-end

::: moniker range="vs-2017"

Chcesz dowiedzieć się więcej na temat inne nowości w tej wersji? Zobacz nasze [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).

::: moniker-end

Gotowe do zainstalowania? Przeprowadzimy Cię przez nią krok po kroku.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1 — Upewnij się, że Twój komputer jest gotowy dla programu Visual Studio

Przed rozpoczęciem instalowania programu Visual Studio:

::: moniker range="vs-2017"

1. Sprawdź [wymagania systemowe](/visualstudio/productinfo/vs2017-system-requirements-vs). Te wymagania ułatwiają określenie, czy komputer obsługuje program Visual Studio 2017.

1. Zastosowanie najnowszych aktualizacji Windows. Te aktualizacje upewnij się, że komputer ma najnowsze aktualizacje zabezpieczeń i wymagane składniki systemowe dla programu Visual Studio.

1. Ponowne uruchomienie komputera. Ponowne uruchomienie gwarantuje, że żadne oczekujące instalacje lub aktualizacje nie zakłócą instalacji programu Visual Studio.

1. Zwolnij miejsce. Usuń niepotrzebne pliki i aplikacje z usługi % SystemDrive %, na przykład uruchamianie aplikacji Oczyszczanie dysku.

::: moniker-end

::: moniker range="vs-2019"

1. Sprawdź [wymagania systemowe](/visualstudio/releases/2019/system-requirements). Te wymagania pomagają sprawdzić, czy komputer obsługuje program Visual Studio 2019.

1. Zastosowanie najnowszych aktualizacji Windows. Te aktualizacje upewnij się, że komputer ma najnowsze aktualizacje zabezpieczeń i wymagane składniki systemowe dla programu Visual Studio.

1. Ponowne uruchomienie komputera. Ponowne uruchomienie gwarantuje, że żadne oczekujące instalacje lub aktualizacje nie zakłócą instalacji programu Visual Studio.

1. Zwolnij miejsce. Usuń niepotrzebne pliki i aplikacje z usługi % SystemDrive %, na przykład uruchamianie aplikacji Oczyszczanie dysku.

::: moniker-end

::: moniker range="vs-2017"

Masz pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok siebie przy użyciu programu Visual Studio 2017, zobacz [informacjami o zgodności programu Visual Studio](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

::: moniker-end

::: moniker range="vs-2019"

Pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok programu Visual Studio 2019 można znaleźć na stronie programu [Visual studio 2019 platformy docelowej i zgodności](/visualstudio/releases/2019/compatibility/) .

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Krok 2 — pobieranie programu Visual Studio

Następnie należy pobrać plik inicjujący programu Visual Studio.

::: moniker range="vs-2017"

Aby uzyskać program inicjujący dla programu Visual Studio 2017, zobacz stronę pobierania [poprzednich wersji programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) , aby uzyskać szczegółowe informacje o tym, jak to zrobić.

::: moniker-end

::: moniker range="vs-2019"

Aby to zrobić, wybierz poniższy przycisk, wybierz wersję programu Visual Studio, a następnie wybierz pozycję **Zapisz**, a następnie wybierz pozycję **Otwórz folder**.

 > [!div class="button"]
 > [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 — instalowanie Instalatora programu Visual Studio

Uruchom plik programu inicjującego, aby zainstalować Instalator programu Visual Studio. Ten nowy Lightweight Installer zawiera wszystko, czego potrzebujesz do zainstalowania i dostosowania programu Visual Studio.

1. Z usługi **pliki do pobrania** folderu, kliknij dwukrotnie program inicjujący, który jest zgodny lub podobny do jednego z następujących plików:

   * **vs_community.exe** dla Visual Studio Community
   * **vs_professional.exe** for Visual Studio Professional
   * **vs_enterprise.exe** programu Visual Studio Enterprise

   Jeśli zostanie wyświetlony komunikat Kontrola konta użytkownika, wybierz opcję **tak**.

2. Poprosimy Cię potwierdzić Microsoft [postanowienia licencyjne](https://visualstudio.microsoft.com/license-terms/) i Microsoft [zasady zachowania poufności informacji](https://privacy.microsoft.com/privacystatement). Wybierz **nadal**.

   ![Licencja warunki i zasady zachowania poufności informacji](media/privacy-and-license-terms.png "postanowienia licencyjne firmy Microsoft oraz zasady zachowania poufności informacji")

## <a name="step-4---choose-workloads"></a>Krok 4. Wybieranie obciążeń

Po zainstalowaniu Instalatora, można go dostosować instalację, wybierając zestawy funkcji — lub obciążeń — przewidzianą. Poniżej przedstawiono sposób.

 ::: moniker range="vs-2017"

1. Znajdź obciążenie w **Instalowanie programu Visual Studio** ekranu.

   ![Visual Studio 2017: Instalowanie obciążenia](../install/media/vs-installer-installing-workloads.png)

     Na przykład wybierz obciążenie "Programowanie aplikacji klasycznych .NET". Dołączono edytora podstawowych domyślny, który zawiera podstawowe obsługę edytowania kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności korzystania z projektu i zintegrowane kontroli kodu źródłowego.

1. Po wybraniu żądanych obciążeń wybierz pozycję **Zainstaluj**.

    Następnie ekranów statusu pojawiają się pokazujących postęp instalacji programu Visual Studio.

 ::: moniker-end

::: moniker range="vs-2019"

1. Po zainstalowaniu nowych obciążeń i składników, wybierz **Uruchom**.

   ![Visual Studio 2019: Instalowanie obciążenia](../install/media/vs-2019/vs-installer-workloads.png)

     Na przykład wybierz obciążenie "Programowanie ASP.NET i sieci Web". Dołączono edytora podstawowych domyślny, który zawiera podstawowe obsługę edytowania kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności korzystania z projektu i zintegrowane kontroli kodu źródłowego.

1. Po wybraniu żądanych obciążeń wybierz pozycję **Zainstaluj**.

    Następnie ekranów statusu pojawiają się pokazujących postęp instalacji programu Visual Studio.

 ::: moniker-end

> [!TIP]
> W dowolnym momencie po zakończeniu instalacji można zainstalować obciążeń lub składników, które nie są początkowo zainstalowano. Jeśli masz program Visual Studio, Otwórz, przejdź do strony **narzędzia** > **Pobierz narzędzia i funkcje...**  która otwiera Instalatora programu Visual Studio. Lub Otwórz **Instalatora programu Visual Studio** z Start menu. W tym miejscu możesz wybrać obciążenia lub składniki, które chcesz zainstalować. Następnie wybierz **Modyfikuj**.

## <a name="step-5---choose-individual-components-optional"></a>Krok 5. Wybierz poszczególne składniki (opcjonalnie)

Jeśli nie chcesz używać funkcji obciążeń do dostosowywania instalacji programu Visual Studio lub chcesz dodać więcej składników niż w przypadku instalacji obciążeń, możesz to zrobić, instalując lub dodając poszczególne składniki z karty **poszczególne składniki** . Wybierz, co chcesz zrobić, a następnie postępuj zgodnie z monitami.

::: moniker range="vs-2017"

  ![Visual Studio 2017 — instalowanie poszczególne składniki](media/vs-installer-installing-components.png "poszczególne składniki Zainstaluj program Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual studio 2019 — Zainstaluj poszczególne składniki](media/vs-2019/vs-installer-individual-components.png "Zainstaluj poszczególne składniki programu Visual Studio")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>Krok 6 — instalowanie pakietów językowych (opcjonalnie)

Domyślnie program instalacyjny próbuje jest zgodny z językiem systemu operacyjnego, gdy jest uruchamiany po raz pierwszy. Aby zainstalować program Visual Studio w wybranym języku, wybierz kartę **pakiety językowe** z Instalator programu Visual Studio, a następnie postępuj zgodnie z monitami.

::: moniker range="vs-2017"

  ![Visual Studio 2017 — instalowanie pakietów językowych](media/vs-installer-installing-language-packs.png "pakiety językowe Zainstaluj program Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual studio 2019 — Zainstaluj pakiety językowe](media/vs-2019/vs-installer-language-packs.png "Zainstaluj pakiety językowe programu Visual Studio")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Zmień język Instalatora z poziomu wiersza polecenia

Inny sposób, można zmienić domyślny język jest, uruchamiając Instalatora z poziomu wiersza polecenia. Na przykład, możesz wymusić Instalatora Aby uruchomić w języku angielskim, za pomocą następującego polecenia: `vs_installer.exe --locale en-US`. Instalator zapamięta to ustawienie po jej uruchomieniu następnym razem. Instalator obsługuje następujące generatory kodów języka: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru i tr-tr.

## <a name="step-7---select-the-installation-location-optional"></a>Krok 7 — Wybieranie lokalizacji instalacji (opcjonalnie)

::: moniker range="vs-2017"

**Nowość w 15,7**: Teraz można zmniejszyć zasięg instalacji programu Visual Studio na dysku systemowym. Można przenieść pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach i zachować programu Visual Studio na dysku, na której działa najszybszej.

  ![Visual Studio 2017 — Zmienianie lokalizacji instalacji](media/installation-options-by-location.png "Zmień lokalizację instalacji")

::: moniker-end

::: moniker range="vs-2019"

Możesz zmniejszyć zasięg instalacji programu Visual Studio na dysku systemowym. Można przenieść pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach i zachować programu Visual Studio na dysku, na której działa najszybszej.

  ![Visual Studio 2019 — Wybierz lokalizacje instalacji](media/vs-2019/vs-installer-installation-locations.png "Wybierz lokalizację instalacji")

::: moniker-end

> [!IMPORTANT]
> Inny dysk można wybrać tylko podczas pierwszej instalacji programu Visual Studio. Jeśli został już zainstalowany i chcesz zmienić dyski, należy odinstalować program Visual Studio, a następnie zainstalować go ponownie.

Aby uzyskać więcej informacji, zobacz stronę [Wybieranie lokalizacji instalacji](change-installation-locations.md) .

## <a name="step-8---start-developing"></a>Krok 8 — zacznij programować

::: moniker range="vs-2017"

1. Po zakończeniu instalacji programu Visual Studio wybierz przycisk **Uruchom** , aby rozpocząć programowanie przy użyciu programu Visual Studio.

2. Wybierz pozycję **plik**, a następnie wybierz pozycję **Nowy projekt**.

3. Wybierz typ projektu.

   Na przykład, aby [skompilować C++ aplikację](/cpp/get-started/tutorial-console-cpp), wybierz pozycję **zainstalowane**, rozwiń **pozycję C++Wizualizacja** , a następnie C++ wybierz typ projektu, który chcesz skompilować.

   Aby [skompilować C# aplikację](../get-started/csharp/tutorial-console.md), wybierz pozycję **zainstalowane**, rozwiń **pozycję C#Wizualizacja** , a następnie C# wybierz typ projektu, który chcesz skompilować.

::: moniker-end

::: moniker range="vs-2019"

1. Po zakończeniu instalacji programu Visual Studio wybierz przycisk **Uruchom** , aby rozpocząć programowanie przy użyciu programu Visual Studio.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

1. W polu wyszukiwania wprowadź typ aplikacji, którą chcesz utworzyć, aby wyświetlić listę dostępnych szablonów. Lista szablonów zależy od obciążeń, które zostały wybrane podczas instalacji. Aby wyświetlić różne szablony, wybierz różne obciążenia.

   Wyszukiwanie w określonym języku programowania można również filtrować za pomocą listy rozwijanej **Język** . Można również filtrować za pomocą listy **platform** i listy **Typ projektu** .

1. Program Visual Studio otwiera nowy projekt i wszystko jest gotowe do kodu!

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Zainstaluj program Visual Studio dla komputerów Mac](/visualstudio/mac/installation)
