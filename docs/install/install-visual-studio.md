---
title: Instalowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zainstalować program Visual Studio, krok po kroku.
ms.date: 05/07/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2e01f51bd94f14b5f78ab26d452be6a100e4fd50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961887"
---
# <a name="install-visual-studio-2017"></a>Instalowanie programu Visual Studio 2017

Nowy sposób instalowania programu Visual Studio — Zapraszamy! W naszych najnowszych wersji wprowadziliśmy je łatwiej można wybierać i instalować tylko funkcje, których potrzebujesz. Również zmniejszyliśmy minimalnego śladu programu Visual Studio, tak aby zainstalował szybciej i z mniejszym wpływem na system niż kiedykolwiek wcześniej.

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

Następnie należy pobrać plik inicjujący programu Visual Studio. Aby to zrobić, kliknij poniższy przycisk, wybierz wersję programu Visual Studio 2017, który ma, kliknij przycisk **Zapisz**, a następnie kliknij przycisk **Otwórz folder**.

 > [!div class="button"]
 > [Pobierz program Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](media/video-icon.png "Obejrzyj klip wideo")  |    [Obejrzyj film wideo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) o tym, jak pobrać plik inicjujący programu Visual Studio i wybierz wersję programu Visual Studio, który jest odpowiedni dla Ciebie. |

## <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 — instalowanie Instalatora programu Visual Studio

Następnie uruchom plik inicjujący, aby zainstalować Instalatora programu Visual Studio. Tego nowego, lekkiego Instalatora zawiera wszystko, czego potrzebujesz do instalowania i dostosowywania programu Visual Studio 2017.

1. Z usługi **pliki do pobrania** folderu, kliknij dwukrotnie program inicjujący, który jest zgodny lub podobny do jednego z następujących plików:

   * **vs_enterprise.exe** programu Visual Studio Enterprise
   * **vs_professional.exe** for Visual Studio Professional
   * **vs_community.exe** dla Visual Studio Community  <br><br>

   Jeśli pojawi się powiadomienie Kontrola konta użytkownika, kliknij przycisk **tak**.

2. Poprosimy Cię potwierdzić Microsoft [postanowienia licencyjne](https://visualstudio.microsoft.com/license-terms/) i Microsoft [zasady zachowania poufności informacji](https://privacy.microsoft.com/privacystatement). Kliknij przycisk **Kontynuuj**.

   ![Licencja warunki i zasady zachowania poufności informacji](media/vs2017-privacy-and-license-terms.PNG "postanowienia licencyjne firmy Microsoft oraz zasady zachowania poufności informacji")

## <a name="step-4---select-workloads"></a>Krok 4 — Wybierz obciążeń

Po zainstalowaniu Instalatora, można go dostosować instalację, wybierając zestawy funkcji — lub obciążeń — przewidzianą. Poniżej przedstawiono sposób.

1. Znajdź obciążenie w **Instalowanie programu Visual Studio** ekranu.

   ![Wybierz obciążenie w oknie dialogowym Instalator programu Visual Studio 2017](../install/media/install-visual-studio-community.png)

     Na przykład wybierz obciążenie "Programowanie aplikacji klasycznych .NET". Dołączono edytora podstawowych domyślny, który zawiera podstawowe obsługę edytowania kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności korzystania z projektu i zintegrowane kontroli kodu źródłowego.

2. Po wybraniu workload(s) ma, kliknij przycisk **zainstalować**.

    Następnie ekranów statusu pojawiają się pokazujących postęp instalacji programu Visual Studio.

3. Po zainstalowaniu nowych obciążeń i składników, kliknij przycisk **Uruchom**.

> [!TIP]
> W dowolnym momencie po zakończeniu instalacji można zainstalować obciążeń lub składników, które nie są początkowo zainstalowano. Jeśli masz program Visual Studio, Otwórz, przejdź do strony **narzędzia** > **Pobierz narzędzia i funkcje...**  która otwiera Instalatora programu Visual Studio. Lub Otwórz **Instalatora programu Visual Studio** z Start menu. Z tego miejsca możesz wybrać obciążeń lub składników, które chcesz zainstalować, a następnie kliknij przycisk **Modyfikuj**.

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](media/video-icon.png "Obejrzyj klip wideo")  |    [Obejrzyj film wideo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) na temat instalowania Instalatora programu Visual Studio, a następnie zainstaluj obciążenia. |

## <a name="step-5---select-individual-components-optional"></a>Krok 5 — wybierz poszczególne składniki (opcjonalnie)

Jeśli nie chcesz korzystać z funkcji obciążeń dostosować instalację programu Visual Studio, możesz to zrobić, instalując zamiast pojedynczych składników. Aby wybrać poszczególne składniki, kliknij przycisk **poszczególne składniki** za pomocą Instalatora programu Visual Studio, wybierz co, a następnie postępuj zgodnie z monitami.

  ![Visual Studio 2017 — instalowanie poszczególne składniki](media/vs2017-components.PNG "poszczególne składniki Zainstaluj program Visual Studio")

  |         |         |
  |---------|---------|
  |  ![Ikona aparatu film wideo](media/video-icon.png "Obejrzyj klip wideo")  |   [Obejrzyj film wideo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) na temat sposobu instalacji poszczególnych składników za pomocą Instalatora programu Visual Studio. |

## <a name="step-6---install-language-packs-optional"></a>Krok 6 — instalowanie pakietów językowych (opcjonalnie)

Domyślnie program instalacyjny próbuje jest zgodny z językiem systemu operacyjnego, gdy jest uruchamiany po raz pierwszy. Aby zainstalować program Visual Studio 2017 w języku wybrane, kliknij przycisk **pakiety językowe** opcji za pomocą Instalatora programu Visual Studio, a następnie postępuj zgodnie z monitami.

  ![Visual Studio 2017 — instalowanie pakietów językowych](media/vs2017-languages.PNG "pakiety językowe Zainstaluj program Visual Studio")

  |         |         |
  |---------|---------|
  |  ![Ikona aparatu film wideo](media/video-icon.png "Obejrzyj klip wideo")  |   [Obejrzyj film wideo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) na temat zainstalować pakiet językowy przy użyciu Instalatora programu Visual Studio. |

### <a name="change-the-installer-language-from-the-command-line"></a>Zmień język Instalatora z poziomu wiersza polecenia

Inny sposób, można zmienić domyślny język jest, uruchamiając Instalatora z poziomu wiersza polecenia. Na przykład, możesz wymusić Instalatora Aby uruchomić w języku angielskim, za pomocą następującego polecenia: `vs_installer.exe --locale en-US`. Instalator zapamięta to ustawienie po jej uruchomieniu następnym razem. Instalator obsługuje następujące generatory kodów języka: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru i tr-tr.

## <a name="step-7---change-the-installation-location-optional"></a>Krok 7 — zmiana lokalizacji instalacji (opcjonalnie)

**Nowość w wersji 15.7**: Teraz można zmniejszyć miejsca zajmowanego przez instalację programu Visual Studio na dysku systemowym. Można przenieść pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach i zachować programu Visual Studio na dysku, na której działa najszybszej.

  ![Program Visual Studio 2017 — zmiana lokalizacji instalacji](media/installation-options-by-location.png "zmiana lokalizacji instalacji")

Aby uzyskać więcej informacji, zobacz [zmiana lokalizacji instalacji programu Visual Studio](change-installation-locations.md) strony.

## <a name="step-8---start-developing"></a>Krok 8 — zacznij programować

1. Po zakończeniu instalacji programu Visual Studio kliknij **Uruchom** przycisk, aby rozpocząć tworzenie aplikacji za pomocą programu Visual Studio.

2. Kliknij przycisk **pliku**, a następnie kliknij przycisk **nowy projekt**.

3. Wybierz typ projektu.

   Na przykład, aby [kompilacji aplikacji w języku C++](../ide/getting-started-with-cpp-in-visual-studio.md), kliknij przycisk **zainstalowane**, rozwiń węzeł **Visual C++**, a następnie wybierz typ projektu C++, który chcesz skompilować.

   Do [kompilacji C# aplikacji](../get-started/csharp/tutorial-wpf.md), kliknij przycisk **zainstalowane**, rozwiń węzeł **Visual C#** , a następnie wybierz pozycję C# typ, który chcesz skompilować projektu.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Update Visual Studio 2017](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio 2017](modify-visual-studio.md)
* [Odinstaluj program Visual Studio 2017](uninstall-visual-studio.md)
* [Tworzenie instalacji offline programu Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Użyj parametrów wiersza polecenia, aby zainstalować program Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Zainstaluj program Visual Studio dla komputerów Mac](/visualstudio/mac/installation)