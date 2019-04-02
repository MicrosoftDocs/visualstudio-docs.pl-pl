---
title: Instalowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zainstalować program Visual Studio, krok po kroku.
ms.date: 03/30/2019
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
ms.openlocfilehash: c76f7f151d10de791a8bcd0c50418d8775f51737
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790722"
---
# <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

::: moniker range="vs-2019"

Witamy w programie Visual Studio 2019 r! W tej wersji jest można łatwo wybrać i zainstalować tylko funkcje, których potrzebujesz. Ze względu na zmniejszenie rozmiaru minimalnej instalacji szybko i przy mniejszym wpływem na system i.

::: moniker-end

::: moniker range="vs-2017"

Nowy sposób instalowania programu Visual Studio — Zapraszamy! W tej wersji wprowadziliśmy je łatwiej można wybrać i zainstalować tylko funkcje, których potrzebujesz. Również zmniejszyliśmy minimalnego śladu programu Visual Studio, tak aby zainstalował szybciej i z mniejszym wpływem na system niż kiedykolwiek wcześniej.

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

1. Sprawdź [wymagania systemowe](/visualstudio/releases/2019/system-requirements). Te wymagania ułatwiają określenie, czy komputer obsługuje program Visual Studio 2019 r.

1. Zastosowanie najnowszych aktualizacji Windows. Te aktualizacje upewnij się, że komputer ma najnowsze aktualizacje zabezpieczeń i wymagane składniki systemowe dla programu Visual Studio.

1. Ponowne uruchomienie komputera. Ponowne uruchomienie gwarantuje, że żadne oczekujące instalacje lub aktualizacje nie zakłócą instalacji programu Visual Studio.

1. Zwolnij miejsce. Usuń niepotrzebne pliki i aplikacje z usługi % SystemDrive %, na przykład uruchamianie aplikacji Oczyszczanie dysku. 

::: moniker-end

::: moniker range="vs-2017"

Masz pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok siebie przy użyciu programu Visual Studio 2017, zobacz [informacjami o zgodności programu Visual Studio](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases/).

::: moniker-end

::: moniker range="vs-2019"

Masz pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok siebie przy użyciu programu Visual Studio 2019 r, zobacz [Visual Studio 2019 r i zgodności platformy](/visualstudio/releases/2019/compatibility/) strony.

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Krok 2 — pobieranie programu Visual Studio

Następnie należy pobrać plik inicjujący programu Visual Studio. Aby to zrobić, kliknij poniższy przycisk, wybierz wydanie programu Visual Studio, której potrzebujesz, następnie wybierz **Zapisz**, a następnie wybierz **Otwórz folder**.

::: moniker range="vs-2017"

 > [!div class="button"]
 > [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

::: moniker-end

::: moniker range="vs-2019"

 > [!div class="button"]
 > [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 — instalowanie Instalatora programu Visual Studio

Uruchom plik inicjujący, aby zainstalować Instalatora programu Visual Studio. Tego nowego, lekkiego Instalatora zawiera wszystko, co jest potrzebne do zainstalowania i Dostosuj program Visual Studio.

1. Z usługi **pliki do pobrania** folderu, kliknij dwukrotnie program inicjujący, który jest zgodny lub podobny do jednego z następujących plików:

   * **vs_community.exe** dla Visual Studio Community
   * **vs_professional.exe** for Visual Studio Professional
   * **vs_enterprise.exe** programu Visual Studio Enterprise

   Jeśli pojawi się powiadomienie Kontrola konta użytkownika, wybierz opcję **tak**.

2. Poprosimy Cię potwierdzić Microsoft [postanowienia licencyjne](https://visualstudio.microsoft.com/license-terms/) i Microsoft [zasady zachowania poufności informacji](https://privacy.microsoft.com/privacystatement). Wybierz **nadal**.

   ![Licencja warunki i zasady zachowania poufności informacji](media/privacy-and-license-terms.png "postanowienia licencyjne firmy Microsoft oraz zasady zachowania poufności informacji")

## <a name="step-4---choose-workloads"></a>Krok 4 — Wybieranie obciążeń

Po zainstalowaniu Instalatora, można go dostosować instalację, wybierając zestawy funkcji — lub obciążeń — przewidzianą. Poniżej przedstawiono sposób.

 ::: moniker range="vs-2017"

1. Znajdź obciążenie w **Instalowanie programu Visual Studio** ekranu.

   ![Visual Studio 2017: Zainstaluj obciążenie](../install/media/vs-installer-installing-workloads.png)

     Na przykład wybierz obciążenie "Programowanie aplikacji klasycznych .NET". Dołączono edytora podstawowych domyślny, który zawiera podstawowe obsługę edytowania kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności korzystania z projektu i zintegrowane kontroli kodu źródłowego.

1. Po wybraniu workload(s) należy wybrać **zainstalować**.

    Następnie ekranów statusu pojawiają się pokazujących postęp instalacji programu Visual Studio.

 ::: moniker-end

::: moniker range="vs-2019"

1. Po zainstalowaniu nowych obciążeń i składników, wybierz **Uruchom**.

   ![Visual Studio 2019: Zainstaluj obciążenie](../install/media/vs-2019/vs-installer-workloads.png)

     Na przykład wybierz obciążenie "opracowywanie zawartości platformy ASP.NET i sieci web". Dołączono edytora podstawowych domyślny, który zawiera podstawowe obsługę edytowania kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności korzystania z projektu i zintegrowane kontroli kodu źródłowego.

1. Po wybraniu workload(s) należy wybrać **zainstalować**.

    Następnie ekranów statusu pojawiają się pokazujących postęp instalacji programu Visual Studio.

 ::: moniker-end

> [!TIP]
> W dowolnym momencie po zakończeniu instalacji można zainstalować obciążeń lub składników, które nie są początkowo zainstalowano. Jeśli masz program Visual Studio, Otwórz, przejdź do strony **narzędzia** > **Pobierz narzędzia i funkcje...**  która otwiera Instalatora programu Visual Studio. Lub Otwórz **Instalatora programu Visual Studio** z Start menu. Z tego miejsca możesz wybrać obciążeń lub składników, które chcesz zainstalować. Następnie wybierz **Modyfikuj**.

## <a name="step-5---choose-individual-components-optional"></a>Krok 5 — wybieranie poszczególnych składników (opcjonalnie)

Jeśli nie chcesz dostosować instalację programu Visual Studio za pomocą funkcji obciążeń lub chcesz dodać więcej składników nie instaluje obciążenia, możesz to zrobić poprzez zainstalowanie lub dodanie poszczególne składniki z **poszczególne składniki** kartę. Wybierz co, a następnie postępuj zgodnie z monitami.

::: moniker range="vs-2017"

  ![Visual Studio 2017 — instalowanie poszczególne składniki](media/vs-installer-installing-components.png "poszczególne składniki Zainstaluj program Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 - instalacji poszczególnych składników](media/vs-2019/vs-installer-individual-components.png "poszczególne składniki Zainstaluj program Visual Studio")

::: moniker-end


## <a name="step-6---install-language-packs-optional"></a>Krok 6 — instalowanie pakietów językowych (opcjonalnie)

Domyślnie program instalacyjny próbuje jest zgodny z językiem systemu operacyjnego, gdy jest uruchamiany po raz pierwszy. Aby zainstalować program Visual Studio w języku wybrane, wybierz opcję **pakiety językowe** kartę za pomocą Instalatora programu Visual Studio, a następnie postępuj zgodnie z monitami.

::: moniker range="vs-2017"

  ![Visual Studio 2017 — instalowanie pakietów językowych](media/vs-installer-installing-language-packs.png "pakiety językowe Zainstaluj program Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 - Zainstaluj pakiety językowe](media/vs-2019/vs-installer-language-packs.png "pakiety językowe Zainstaluj program Visual Studio")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Zmień język Instalatora z poziomu wiersza polecenia

Inny sposób, można zmienić domyślny język jest, uruchamiając Instalatora z poziomu wiersza polecenia. Na przykład, możesz wymusić Instalatora Aby uruchomić w języku angielskim, za pomocą następującego polecenia: `vs_installer.exe --locale en-US`. Instalator zapamięta to ustawienie po jej uruchomieniu następnym razem. Instalator obsługuje następujące generatory kodów języka: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru i tr-tr.

## <a name="step-7---change-the-installation-location-optional"></a>Krok 7 — zmiana lokalizacji instalacji (opcjonalnie)

::: moniker range="vs-2017"

**Nowość w wersji 15.7**: Teraz można zmniejszyć miejsca zajmowanego przez instalację programu Visual Studio na dysku systemowym. Można przenieść pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach i zachować programu Visual Studio na dysku, na której działa najszybszej.

  ![Visual Studio 2017 — Zmień lokalizacje instalacji](media/installation-options-by-location.png "zmiana lokalizacji instalacji")

::: moniker-end

::: moniker range="vs-2019"

Możliwe jest zmniejszenie miejsca zajmowanego przez instalację programu Visual Studio na dysku systemowym. Można przenieść pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach i zachować programu Visual Studio na dysku, na której działa najszybszej.

  ![Visual Studio 2019 - Zmień lokalizacje instalacji](media/vs-2019/vs-installer-installation-locations.png "zmiana lokalizacji instalacji")

::: moniker-end

> [!IMPORTANT]
> Możesz wybrać inny dysk tylko wtedy, gdy najpierw zainstalować program Visual Studio. Jeśli już został zainstalowany i chcesz zmienić dysków, należy odinstalować program Visual Studio i zainstaluj go ponownie.

Aby uzyskać więcej informacji, zobacz [wybierz lokalizacje instalacji](change-installation-locations.md) strony.

## <a name="step-8---start-developing"></a>Krok 8 — zacznij programować

::: moniker range="vs-2017"

1. Po zakończeniu instalacji programu Visual Studio wybierz **Uruchom** przycisk, aby rozpocząć tworzenie aplikacji za pomocą programu Visual Studio.

2. Wybierz **pliku**, a następnie wybierz **nowy projekt**.

3. Wybierz typ projektu.

   Na przykład, aby [kompilacji aplikacji w języku C++](../ide/getting-started-with-cpp-in-visual-studio.md), wybierz **zainstalowane**, rozwiń węzeł **Visual C++**, a następnie wybierz typ projektu C++, który chcesz skompilować.

   Do [kompilacji C# aplikacji](../get-started/csharp/tutorial-console.md), wybierz **zainstalowane**, rozwiń węzeł **Visual C#** , a następnie wybierz C# typ, który chcesz skompilować projektu.

::: moniker-end

::: moniker range="vs-2019"

1. Po zakończeniu instalacji programu Visual Studio wybierz **Uruchom** przycisk, aby rozpocząć tworzenie aplikacji za pomocą programu Visual Studio.

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

1. W polu wyszukiwania wprowadź typ aplikacji, którą chcesz utworzyć, aby wyświetlić listę dostępnych szablonów. Na liście szablonów, zależy od workload(s), która została wybrana podczas instalacji. Aby wyświetlić różne szablony, wybierz różnych obciążeń.

   Można także filtrować wyszukiwania dla określonego języka programowania przy użyciu **języka** listy rozwijanej. Można filtrować przy użyciu **platformy** listy i **typ projektu** listy zbyt. 

1. Visual Studio otwiera nowy projekt i wszystko jest gotowe do kodu.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Zainstaluj program Visual Studio dla komputerów Mac](/visualstudio/mac/installation)