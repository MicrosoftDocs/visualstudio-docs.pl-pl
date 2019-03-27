---
title: Instalowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zainstalować program Visual Studio, krok po kroku.
ms.date: 02/11/2019
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
ms.openlocfilehash: 659f220936bd1a6273a27d63642534955a48c7aa
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515262"
---
# <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

Nowy sposób instalowania programu Visual Studio — Zapraszamy! W tej wersji wprowadziliśmy je łatwiej można wybierać i instalować tylko funkcje, których potrzebujesz. Również zmniejszyliśmy minimalnego śladu programu Visual Studio, tak aby zainstalował szybciej i z mniejszym wpływem na system niż kiedykolwiek wcześniej.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [Zainstaluj program Visual Studio dla komputerów Mac](/visualstudio/mac/installation).

Chcesz dowiedzieć się więcej na temat inne nowości w tej wersji? Zobacz nasze [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).

Gotowe do zainstalowania? Przeprowadzimy Cię przez nią krok po kroku.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1 — Upewnij się, że Twój komputer jest gotowy dla programu Visual Studio

Przed rozpoczęciem instalowania programu Visual Studio:

1. Sprawdź [wymagania systemowe](/visualstudio/productinfo/vs2017-system-requirements-vs). Te wymagania ułatwiają określenie, czy komputer obsługuje program Visual Studio 2017.
2. Zastosowanie najnowszych aktualizacji Windows. Te aktualizacje upewnij się, że komputer ma najnowsze aktualizacje zabezpieczeń i wymagane składniki systemowe dla programu Visual Studio.
3. Ponowne uruchomienie komputera. Ponowne uruchomienie gwarantuje, że żadne oczekujące instalacje lub aktualizacje nie zakłócą instalacji programu Visual Studio.
4. Zwolnij miejsce. Usuń niepotrzebne pliki i aplikacje z usługi % SystemDrive %, na przykład uruchamianie aplikacji Oczyszczanie dysku.

Masz pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok siebie przy użyciu programu Visual Studio 2017, zobacz [informacjami o zgodności programu Visual Studio](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Krok 2 — pobieranie programu Visual Studio

Następnie należy pobrać plik inicjujący programu Visual Studio. Aby to zrobić, kliknij poniższy przycisk, wybierz wersję programu Visual Studio 2017, należy wybrać **Zapisz**, a następnie wybierz **Otwórz folder**.

 > [!div class="button"]
 > [Pobierz program Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

## <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 — instalowanie Instalatora programu Visual Studio

Następnie uruchom plik inicjujący, aby zainstalować Instalatora programu Visual Studio. Tego nowego, lekkiego Instalatora zawiera wszystko, czego potrzebujesz do instalowania i dostosowywania programu Visual Studio 2017.

1. Z usługi **pliki do pobrania** folderu, kliknij dwukrotnie program inicjujący, który jest zgodny lub podobny do jednego z następujących plików:

   * **vs_enterprise.exe** programu Visual Studio Enterprise
   * **vs_professional.exe** for Visual Studio Professional
   * **vs_community.exe** dla Visual Studio Community  <br><br>

   Jeśli pojawi się powiadomienie Kontrola konta użytkownika, wybierz opcję **tak**.

2. Poprosimy Cię potwierdzić Microsoft [postanowienia licencyjne](https://visualstudio.microsoft.com/license-terms/) i Microsoft [zasady zachowania poufności informacji](https://privacy.microsoft.com/privacystatement). Wybierz **nadal**.

   ![Licencja warunki i zasady zachowania poufności informacji](media/vs2017-privacy-and-license-terms.PNG "postanowienia licencyjne firmy Microsoft oraz zasady zachowania poufności informacji")

## <a name="step-4---select-workloads"></a>Krok 4 — Wybierz obciążeń

Po zainstalowaniu Instalatora, można go dostosować instalację, wybierając zestawy funkcji — lub obciążeń — przewidzianą. Poniżej przedstawiono sposób.

1. Znajdź obciążenie w **Instalowanie programu Visual Studio** ekranu.

   ![Wybierz obciążenie w oknie dialogowym Instalator programu Visual Studio 2017](../install/media/install-visual-studio-community.png)

     Na przykład wybierz obciążenie "Programowanie aplikacji klasycznych .NET". Dołączono edytora podstawowych domyślny, który zawiera podstawowe obsługę edytowania kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności korzystania z projektu i zintegrowane kontroli kodu źródłowego.

2. Po zaznaczeniu workload(s) chcesz, aby wybrać **zainstalować**.

    Następnie ekranów statusu pojawiają się pokazujących postęp instalacji programu Visual Studio.

3. Po zainstalowaniu nowych obciążeń i składników, wybierz **Uruchom**.

> [!TIP]
> W dowolnym momencie po zakończeniu instalacji można zainstalować obciążeń lub składników, które nie są początkowo zainstalowano. Jeśli masz program Visual Studio, Otwórz, przejdź do strony **narzędzia** > **Pobierz narzędzia i funkcje...**  która otwiera Instalatora programu Visual Studio. Lub Otwórz **Instalatora programu Visual Studio** z Start menu. Z tego miejsca możesz wybrać obciążeń lub składników, które chcesz zainstalować, a następnie wybierz **Modyfikuj**.

## <a name="step-5---select-individual-components-optional"></a>Krok 5 — wybierz poszczególne składniki (opcjonalnie)

Jeśli nie chcesz korzystać z funkcji obciążeń dostosować instalację programu Visual Studio, możesz to zrobić, instalując zamiast pojedynczych składników. Aby wybrać poszczególne składniki, wybierz **poszczególne składniki** za pomocą Instalatora programu Visual Studio, wybierz co, a następnie postępuj zgodnie z monitami.

  ![Visual Studio 2017 — instalowanie poszczególne składniki](media/vs2017-components.PNG "poszczególne składniki Zainstaluj program Visual Studio")

## <a name="step-6---install-language-packs-optional"></a>Krok 6 — instalowanie pakietów językowych (opcjonalnie)

Domyślnie program instalacyjny próbuje jest zgodny z językiem systemu operacyjnego, gdy jest uruchamiany po raz pierwszy. Aby zainstalować program Visual Studio 2017 w języku wybrane, wybierz **pakiety językowe** opcji za pomocą Instalatora programu Visual Studio, a następnie postępuj zgodnie z monitami.

  ![Visual Studio 2017 — instalowanie pakietów językowych](media/vs2017-languages.PNG "pakiety językowe Zainstaluj program Visual Studio")

### <a name="change-the-installer-language-from-the-command-line"></a>Zmień język Instalatora z poziomu wiersza polecenia

Inny sposób, można zmienić domyślny język jest, uruchamiając Instalatora z poziomu wiersza polecenia. Na przykład, możesz wymusić Instalatora Aby uruchomić w języku angielskim, za pomocą następującego polecenia: `vs_installer.exe --locale en-US`. Instalator zapamięta to ustawienie po jej uruchomieniu następnym razem. Instalator obsługuje następujące generatory kodów języka: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru i tr-tr.

## <a name="step-7---change-the-installation-location-optional"></a>Krok 7 — zmiana lokalizacji instalacji (opcjonalnie)

**Nowość w wersji 15.7**: Teraz można zmniejszyć miejsca zajmowanego przez instalację programu Visual Studio na dysku systemowym. Można przenieść pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach i zachować programu Visual Studio na dysku, na której działa najszybszej.

  ![Program Visual Studio 2017 — zmiana lokalizacji instalacji](media/installation-options-by-location.png "zmiana lokalizacji instalacji")

Aby uzyskać więcej informacji, zobacz [zmiana lokalizacji instalacji programu Visual Studio](change-installation-locations.md) strony.

## <a name="step-8---start-developing"></a>Krok 8 — zacznij programować

::: moniker range="vs-2017"

1. Po zakończeniu instalacji programu Visual Studio wybierz **Uruchom** przycisk, aby rozpocząć tworzenie aplikacji za pomocą programu Visual Studio.

2. Wybierz **pliku**, a następnie wybierz **nowy projekt**.

3. Wybierz typ projektu.

   Na przykład, aby [kompilacji aplikacji w języku C++](../ide/getting-started-with-cpp-in-visual-studio.md), wybierz **zainstalowane**, rozwiń węzeł **Visual C++**, a następnie wybierz typ projektu C++, który chcesz skompilować.

   Do [kompilacji C# aplikacji](../get-started/csharp/tutorial-wpf.md), wybierz **zainstalowane**, rozwiń węzeł **Visual C#** , a następnie wybierz pozycję C# typ, który chcesz skompilować projektu.

::: moniker-end

::: moniker range="vs-2019"

1. Po zakończeniu instalacji programu Visual Studio wybierz **Uruchom** przycisk, aby rozpocząć tworzenie aplikacji za pomocą programu Visual Studio.

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

1. W polu wyszukiwania wprowadź typ aplikacji, którą chcesz utworzyć, aby wyświetlić listę szablonów. (Na przykład, wprowadź *WFP*.)

  > [!TIP]
  > Możesz filtrować wyniki wyszukiwania dla określonego języka programowania przy użyciu **języka** listy rozwijanej. Można również filtrować za pomocą **platformy** listy i **typ projektu** listy. 

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