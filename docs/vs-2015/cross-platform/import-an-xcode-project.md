---
title: Importowanie projektu XCode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b0e42c167e87f19781f9544e20e7870789af4ef9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754152"
---
# <a name="import-an-xcode-project"></a>Importowanie projektu XCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Microsoft Visual C++ for Cross-Platform Mobile Development obsługuje przenoszenie projektów XCode do Visual Studio, w którym można tworzyć biblioteki Międzyplatformowe i udostępnianie kodu z innymi projektami. Importuj z XCode Kreator upraszcza proces Importowanie projektów i dzielenie się kodu C++ w XCode elementy docelowe dla używany jako biblioteka statyczna lub udostępnionego projektu kodu. Można zarządzać kodem specyficzne dla systemu iOS w programie Visual Studio i nadal korzystania ze środowiska XCode do scenorysów i kompilacji. Aby uzyskać informacje o tym, jak łatwo można przejść kodu i z powrotem między Visual Studio i XCode Zobacz przenoszenia zmian między XCode i Visual Studio.  
  
## <a name="using-the-import-from-xcode-wizard"></a>Za pomocą Kreatora Importuj z XCode  
 W tym temacie dowiesz się, jak przenieść projekt XCode do programu Visual Studio, aby móc korzystać z udostępniania kodu i rozwiązań dla wielu platform. Jako warunek wstępny należy sparować komputer Mac w programie Visual Studio, aby można było importować, eksportować i skompiluj projekt. Aby uzyskać instrukcje dotyczące sposobu konfigurowania parowania, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Należy również Udostępnij swój projekt XCode za pośrednictwem sieci lub przenieś go do Twojego komputera programu Visual Studio Importuj z XCode kreatora.  
  
#### <a name="import-from-xcode"></a>Importuj z XCode  
  
1. Na **pliku** menu, wybierz **New**, **importu**, **Importuj z XCode**. Spowoduje to uruchomienie **Importuj z XCode** Kreator okna dialogowego.  
  
    ![Wybierz projekt docelowy XCode do zaimportowania](../cross-platform/media/cppmdd-u2-importxcode-choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2. W **wybierz projekt** okienku wybierz przycisk Przeglądaj, aby wybrać plik .pbxproj XCode. Przejdź do pliku projektu w **plik projektu XCode wybierz** okno dialogowe, a następnie wybierz **Otwórz**.  
  
    ![Wybierz plik projektu w oknie dialogowym plik projektu Xcode wybierz](../cross-platform/media/cppmdd-u2-importxcode-browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
    W Kreatorze importowania danych z narzędzia XCode, wybierz **dalej**.  
  
3. W **elementy docelowe miejsca docelowego** okienku wybierać elementy docelowe projektu XCode, należy zaimportować do projektów programu Visual Studio. Cele w środowisku XCode są podobne do projektów programu Visual Studio; Większość to zbiór kod i zasoby, które generują dane binarne. Importuj z XCode Kreator może składać się importowanie elementów docelowych, które generują dane binarne, ale nie biblioteki statycznej, jako elementy docelowe miejsca docelowego. Elementy docelowe biblioteki statycznej XCode podlegają następnego kroku.  
  
    ![Importuj z XCode kreatora elementy docelowe miejsca docelowego okienko](../cross-platform/media/cppmdd-u2-importxcode-destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
    Dla każdego obiektu docelowego, które wybrano w **elementy docelowe do zaimportowania**, Kreator automatycznie wykrywa plików kodu C++, które może zostać podzielony na projekt biblioteki statycznej oddzielne i umieszcza je w **elementy projektu C++** sekcji. Inne kod i zasoby są pozostawiane w **elementy projektu XCode** sekcji. Te stają się odrębnych bibliotek statycznych i projektów aplikacji w programie Visual Studio po zakończeniu działania kreatora proces importowania. Domyślnie obiekty docelowe test i struktury jednostki nie są dzielone na oddzielnych projektów przez kreatora.  
  
    Aby zmienić, pliki, które znajdują się w każdym projekcie, górę i w dół przycisków. Gdy jesteś zadowolony z plikami w każdym projekcie, wybierz pozycję **dalej** aby kontynuować.  
  
4. W **elementy docelowe biblioteki** okienku wybierz, które biblioteki statycznej jest przeznaczony dla z projektu XCode, należy zaimportować do projektów programu Visual Studio. W tym okienku możesz wybrać pliki, które są umieszczane w projektu współużytkowanego kodu i które są umieszczone w projekcie biblioteki statycznej. W każdym z elementów docelowych w **elementy docelowe do zaimportowania** listy, możesz kontrolować, które pliki są umieszczane w **elementy projektu współużytkowanego kodu** i **elementy projektu biblioteki statycznej** przy użyciu przyciski w górę i w dół.  
  
    ![Importuj z okienka elementy docelowe biblioteki XCode](../cross-platform/media/cppmdd-u2-importxcode-library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
    Projekt współużytkowanego kodu jest sposób udostępniania zbiór plików kodu źródłowego między projektami w programie Visual Studio. Kod jest kompilowany jako część projektu, który zawiera go, a nie jako swój własny projekt. Ponieważ projekty zawierające kod udostępniony może mieć różne architektury i konfiguracje, jest to najlepszy sposób zgłaszania pojedynczego projektu, który zawiera kod, który może zostać utworzony dla wielu różnych platformach.  
  
    Gdy jesteś zadowolony z plikami w każdym projekcie, wybierz pozycję **dalej** aby kontynuować.  
  
5. **Globalne właściwości** okienku można ustawić ścieżkę wyszukiwania struktury i ścieżka wyszukiwania nagłówków dołączania dla wszystkich projektów systemu iOS w programie Visual Studio. Visual Studio używa tych ścieżek do przeglądania kodu źródłowego, jak i dla technologii IntelliSense. Tych ścieżek globalne są przydatne podczas tworzenia projektów systemu iOS, które korzystają ze wspólnego zestawu nagłówków i struktur.  
  
    ![Importuj z XCode globalne właściwości w okienku](../cross-platform/media/cppmdd-u2-importxcode-global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
    Można również ustawić te ścieżki globalnych w programie Visual Studio w **opcje** okna dialogowego. Aby znaleźć je na **narzędzia** menu, wybierz opcję **opcje**. W **opcje** okna dialogowego, rozwiń węzeł **Międzyplatformowe**, **C++**, **iOS**, **globalne właściwości**.  
  
    Wybierz **dalej** aby kontynuować.  
  
6. **Struktur** okienko służy do konfigurowania ścieżki używany przez program Visual Studio do przeglądania i IntelliSense dla Twojego projektu. Ścieżki muszą być dostępne dla programu Visual Studio dla każdej struktury odwołań w projekcie XCode. Sprawdzanie przez Kreator dostępności ramach odwołuje się w projektach środowiska XCode i wyświetla informację, czy program Visual Studio można znaleźć w ramach. Wszystkie ścieżki, które zostały już skonfigurowane w globalnych właściwości powinny zostać wykryte przez program Visual Studio. Wyjątki są wymienione na liście środowisk. Dla każdej struktury, znakiem X na liście należy podać ścieżkę dostępne komputera dla programu Visual Studio można znaleźć w ramach. Możesz użyć przycisku Przeglądaj [...] do użycia **wybierz Folder** okno dialogowe, aby znaleźć ścieżki. Ścieżka framework może być w lokalnej kopii lub w udziale dostępne w sieci na komputerze Mac.  
  
    ![Importuj z XCode struktur w okienku](../cross-platform/media/cppmdd-u2-importxcode-frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
    Wybierz **dalej** aby kontynuować.  
  
7. **Ustawienia projektu** okienko pozwala zmienić platformę i zawierać nagłówek ustawienia ścieżki wyszukiwania dla każdego projektu, Kreator tworzy. Użyj w tym okienku można ustawić ścieżki specyficzne dla projektu, które różnią się od ustawień globalnych.  
  
    Aby ustawić ścieżkę do określonego projektu w **projekt docelowy** listę rozwijaną, wybierz plik projektu, a następnie ustaw wartości w **ścieżkę wyszukiwania struktury** i **obejmują ścieżka wyszukiwania nagłówków** kontrolki. Możesz użyć przycisku Przeglądaj [...] obok każdej kontrolki do użycia **wybierz Folder** okno dialogowe, aby znaleźć ścieżki.  
  
    ![Importuj z okienka projekty XCode](../cross-platform/media/cppmdd-u2-importxcode-projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
    Jeśli nie zdalnego Mac ma skojarzone z tym Komputerem w programie Visual Studio, konfiguracji, wyświetlany jest link maszyny zdalnej. Aby uzyskać instrukcje dotyczące sposobu konfigurowania parowania, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
    Aby zaimportować projekt XCode przy użyciu ustawień kreatora, wybierz opcję **zaimportować**.  
  
   Importuj z XCode Kreator tworzy projektów w Visual Studio, które odpowiadają wybrane elementy projektu XCode. Kod, który mogą być współużytkowane z innych projektów w języku C++ zostanie podzielona na oddzielne wspólny kod i projekty biblioteki statycznej. Pozostały kod jest umieszczany w systemie iOS projekty biblioteki i aplikacji, które mogą być wbudowane w zdalnie przez program Visual Studio. Aby uzyskać więcej informacji na temat przenoszenia kodu między Visual Studio i XCode, zobacz [synchronizacja zmian między XCode i Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).

