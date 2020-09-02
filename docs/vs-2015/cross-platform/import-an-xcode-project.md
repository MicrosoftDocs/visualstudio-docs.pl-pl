---
title: Importowanie projektu XCode | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 4faa2ecae7f53d29e6aad92723ca6d12e50e2812
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150983"
---
# <a name="import-an-xcode-project"></a>Importowanie projektu XCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Visual C++ dla wieloplatformowego opracowywania aplikacji mobilnych obejmuje obsługę przenoszenia projektów XCode do programu Visual Studio, w którym można tworzyć biblioteki Międzyplatformowe i udostępniać kod innym projektom. Kreator importu z XCode upraszcza proces importowania projektów i dzielenia kodu C++ w celu użycia jako biblioteki statycznej lub projektu kodu udostępnionego. Kod specyficzny dla systemu iOS można zarządzać w programie Visual Studio i nadal używać XCode do tworzenia scenorysów i kompilacji. Aby uzyskać informacje na temat łatwego przenoszenia kodu między programem Visual Studio i XCode, zobacz Przenoszenie zmian między XCode i Visual Studio.  
  
## <a name="using-the-import-from-xcode-wizard"></a>Korzystanie z Kreatora importowania z XCode  
 W tym temacie pokazano, jak przenieść projekt XCode do programu Visual Studio, aby skorzystać z udostępniania kodu i rozwiązań dla wielu platform. Jako warunek wstępny należy sparować komputer Mac z programem Visual Studio, aby można było importować, eksportować i kompilować projekt. Aby uzyskać instrukcje dotyczące sposobu konfigurowania parowania, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Musisz również udostępnić projekt XCode za pośrednictwem sieci lub przenieść go na komputer z programem Visual Studio, aby użyć Kreatora importowania z XCode.  
  
#### <a name="import-from-xcode"></a>Importuj z XCode  
  
1. W menu **plik** wybierz polecenie **Nowy**, **Importuj**, **Importuj z Xcode**. Spowoduje to uruchomienie kreatora **importowania z Xcode** .  
  
    ![Wybierz projekt docelowy XCode do zaimportowania](../cross-platform/media/cppmdd-u2-importxcode-choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2. W okienku **Wybierz projekt** wybierz przycisk Przeglądaj, aby wybrać plik Xcode. PBXPROJ. Przejdź do pliku projektu w oknie dialogowym **Wybierz plik projektu Xcode** , a następnie wybierz **Otwórz**.  
  
    ![Wybierz plik projektu w oknie dialogowym Wybierz plik projektu Xcode](../cross-platform/media/cppmdd-u2-importxcode-browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
    W Kreatorze importowania z XCode wybierz przycisk **dalej**.  
  
3. W okienku **docelowe cele** wybierz cele z projektu Xcode, aby zaimportować do projektów programu Visual Studio. Elementy docelowe XCode są podobne do projektów programu Visual Studio. Większość to zbiór kodu i zasobów, które tworzą dane binarne. Kreator importu z XCode umożliwia tylko import obiektów docelowych, które tworzą dane binarne, ale nie jako biblioteki statycznej, jako docelowe obiekty docelowe. Elementy docelowe biblioteki statycznej XCode są podmiotem następnego kroku.  
  
    ![Zaimportuj z okienka obiektów docelowych kreatora XCode](../cross-platform/media/cppmdd-u2-importxcode-destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
    W przypadku każdego elementu docelowego wybranego w **celu zaimportowania**Kreator automatycznie wykrywa pliki kodu C++, które mogą zostać podzielone na osobny projekt biblioteki statycznej, i umieszcza je w sekcji **elementy projektu c++** . Inny kod i zasoby są pozostawione w sekcji **elementy projektu Xcode** . Stają się one oddzielnymi projektami biblioteki statycznej i aplikacji w programie Visual Studio, gdy Kreator ukończy proces importowania. Domyślnie testy jednostkowe i cele struktury nie są podzielone na oddzielne projekty przez kreatora.  
  
    Aby zmienić pliki w każdym projekcie, użyj przycisków w górę i w dół. Gdy pliki w każdym projekcie są zadowalające, wybierz przycisk **dalej** , aby kontynuować.  
  
4. W okienku **obiekty docelowe biblioteki** wybierz elementy docelowe biblioteki statycznej z projektu Xcode do zaimportowania do projektów programu Visual Studio. W tym okienku można wybrać, które pliki są umieszczane w projekcie kodu współdzielonego, które są umieszczane w projekcie biblioteki statycznej. W każdym elemencie docelowym listy elementy **docelowe do zaimportowania** można kontrolować, które pliki są umieszczane w **elementach projektu udostępnionego kodu** i **elementy projektu biblioteki statycznej** przy użyciu przycisków w górę i w dół.  
  
    ![Importuj z okienka elementów docelowych biblioteki XCode](../cross-platform/media/cppmdd-u2-importxcode-library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
    Współużytkowany projekt kodu jest sposobem udostępniania zestawu plików kodu źródłowego między projektami w programie Visual Studio. Kod jest tworzony w ramach projektu, który zawiera go, a nie jako projekt własny. Ponieważ projekty, które zawierają udostępniony kod, mogą mieć różne architektury i konfiguracje, jest to najlepszy sposób zapewnienia pojedynczego projektu, który zawiera kod, który może być zbudowany dla wielu rodzajów platform.  
  
    Gdy pliki w każdym projekcie są zadowalające, wybierz przycisk **dalej** , aby kontynuować.  
  
5. Okienko **Właściwości globalne** służy do ustawiania ścieżki wyszukiwania struktury i ścieżki wyszukiwania nagłówka include dla wszystkich projektów systemu iOS w programie Visual Studio. Program Visual Studio używa tych ścieżek do przeglądania kodu źródłowego i funkcji IntelliSense. Te ścieżki globalne są przydatne podczas tworzenia projektów systemu iOS, które korzystają ze wspólnego zestawu nagłówków i struktur.  
  
    ![Importuj z okienka Właściwości globalne XCode](../cross-platform/media/cppmdd-u2-importxcode-global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
    Te ścieżki globalne można także ustawić w programie Visual Studio w oknie dialogowym **Opcje** . Aby je znaleźć, w menu **Narzędzia** wybierz polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń pozycję **Międzyplatformowe**, **C++**, **iOS**, **Właściwości globalne**.  
  
    Wybierz pozycję **Dalej**, aby kontynuować.  
  
6. Okienko **struktury** służy do konfigurowania ścieżek używanych przez program Visual Studio do przeglądania i IntelliSense dla projektu. Ścieżki muszą być dostępne dla programu Visual Studio dla każdej struktury, do której odwołuje się projekt XCode. Kreator sprawdza odwołania do struktury w projektach XCode i wyświetla, czy program Visual Studio może znaleźć strukturę. Wszystkie ścieżki, które zostały już skonfigurowane we właściwościach globalnych, powinny być odnajdywane przez program Visual Studio. Wyjątki są wymienione na liście struktury. Dla każdej struktury wymienionej przy użyciu X podaj ścieżkę dostępu do komputera dla programu Visual Studio, aby znaleźć strukturę. Aby znaleźć ścieżkę, można użyć przycisku przeglądania [...]. **Select Folder** Ścieżką struktury może być kopia lokalna lub udział dostępny w sieci na komputerze Mac.  
  
    ![Importuj z okienka XCode Frameworks](../cross-platform/media/cppmdd-u2-importxcode-frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
    Wybierz pozycję **Dalej**, aby kontynuować.  
  
7. W okienku **Ustawienia projektu** można zmienić strukturę i uwzględnić ustawienia ścieżki wyszukiwania nagłówka dla każdego projektu tworzonego przez kreatora. To okienko służy do ustawiania ścieżek specyficznych dla projektu, które różnią się od ustawień globalnych.  
  
    Aby ustawić ścieżkę dla określonego projektu, na liście rozwijanej **projekt docelowy** wybierz plik projektu, a następnie ustaw wartości w **ścieżce wyszukiwania struktury** i **Uwzględnij kontrolki ścieżki wyszukiwania nagłówka** . Możesz użyć przycisku przeglądania [...] obok każdej kontrolki, aby użyć okna dialogowego **Wybierz folder** , aby znaleźć ścieżkę.  
  
    ![Importuj z okienka projektów XCode](../cross-platform/media/cppmdd-u2-importxcode-projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
    Jeśli żaden zdalny komputer Mac nie został sparowany z tym komputerem w programie Visual Studio, zostanie wyświetlony link Konfiguruj maszynę zdalną. Aby uzyskać instrukcje dotyczące sposobu konfigurowania parowania, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
    Aby zaimportować projekt XCode za pomocą ustawień kreatora, wybierz pozycję **Importuj**.  
  
   Kreator importu z XCode tworzy projekty w programie Visual Studio odpowiadające wybranym obiektom docelowym projektu XCode. Kod, który może być współużytkowany z innymi projektami C++, jest podzielony na osobny kod współużytkowany i statyczne projekty bibliotek. Pozostały kod jest umieszczany w projektach biblioteki i aplikacji systemu iOS, które mogą być kompilowane zdalnie przez program Visual Studio. Aby uzyskać więcej informacji na temat przesuwania kodu między programem Visual Studio i XCode, zobacz [Synchronizacja zmian między Xcode i Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).
