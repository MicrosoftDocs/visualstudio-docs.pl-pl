---
title: Importowanie projektu Xcode | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 62161b612d6c4583cd2206c3d18dc6606d2d9f0b
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588893"
---
# <a name="import-an-xcode-project"></a>Importowanie projektu Xcode

Visual Studio Tools dla wieloplatformowego opracowywania aplikacji mobilnych C++ z obsługą funkcji przenoszenia projektów Xcode do programu Visual Studio, w którym można tworzyć biblioteki dla wielu platform i udostępniać kod innym projektom. Kreator importu z Xcode upraszcza proces importowania projektów i dzielenia C++ kodu w celu użycia jako biblioteki statycznej lub projektu kodu udostępnionego. Kod specyficzny dla systemu iOS można zarządzać w programie Visual Studio i nadal używać Xcode do tworzenia scenorysów i kompilacji. Aby uzyskać informacje na temat łatwego przenoszenia kodu między programem Visual Studio i Xcode, zobacz [Synchronizacja zmian między Xcode i Visual Studio](sync-changes-between-xcode-and-visual-studio.md).

## <a name="use-the-import-from-xcode-wizard"></a>Korzystanie z Kreatora importowania z Xcode

W tym artykule pokazano, jak przenieść projekt Xcode do programu Visual Studio, aby skorzystać z zalet udostępniania kodu i rozwiązań dla wielu platform. Jako wymaganie wstępne należy sparować komputer Mac z programem Visual Studio, aby importować, eksportować i kompilować projekt. Aby uzyskać instrukcje dotyczące sposobu konfigurowania parowania, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Musisz również udostępnić projekt Xcode za pośrednictwem sieci lub przenieść go na komputer z programem Visual Studio, aby użyć Kreatora importowania z Xcode.

### <a name="import-from-xcode"></a>Importuj z Xcode

1. W menu **plik** wybierz polecenie **Nowy**, **Importuj**, **Importuj z Xcode**. To polecenie uruchamia kreatora **importowania z Xcode** .

   ![Wybierz projekt docelowy Xcode do zaimportowania](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "Wybierz projekt docelowy Xcode do zaimportowania")

1. W okienku **Wybierz projekt** wybierz przycisk Przeglądaj, aby wybrać plik Xcode *. PBXPROJ* . Przejdź do pliku projektu w oknie dialogowym **Wybierz plik projektu Xcode** , a następnie wybierz **Otwórz**.

   ![Wybierz plik projektu w oknie dialogowym Wybierz plik projektu Xcode](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "Wybierz plik projektu w oknie dialogowym Wybierz plik projektu Xcode")

   W Kreatorze importowania z Xcode wybierz przycisk **dalej**.

1. W okienku **docelowe cele** wybierz cele z projektu Xcode, aby zaimportować do projektów programu Visual Studio. Elementy docelowe Xcode są podobne do projektów programu Visual Studio. Większość to zbiór kodu i zasobów, które tworzą dane binarne. Kreator importu z Xcode umożliwia tylko import obiektów docelowych, które tworzą dane binarne, ale nie jako biblioteki statycznej, jako docelowe obiekty docelowe. Elementy docelowe biblioteki statycznej Xcode są podmiotem następnego kroku.

   ![Zaimportuj z okienka obiektów docelowych kreatora Xcode](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "Zaimportuj z okienka obiektów docelowych kreatora Xcode")

   W przypadku każdego elementu docelowego wybranego w **celu zaimportowania**Kreator automatycznie C++ wykrywa pliki kodu, które można podzielić na osobny projekt biblioteki statycznej, i umieścić je w sekcji  **C++ elementy projektu** . Inny kod i zasoby są pozostawione w sekcji **elementy projektu Xcode** . Stają się one oddzielnymi projektami biblioteki statycznej i aplikacji w programie Visual Studio, gdy Kreator ukończy proces importowania. Domyślnie testy jednostkowe i cele struktury nie są podzielone na oddzielne projekty przez kreatora.

   Aby zmienić pliki w każdym projekcie, użyj przycisków w górę i w dół. Gdy pliki w poszczególnych projektach są zadowalające, wybierz pozycję **dalej** , aby kontynuować.

1. W okienku **obiekty docelowe biblioteki** wybierz elementy docelowe biblioteki statycznej z projektu Xcode do zaimportowania do projektów programu Visual Studio. W tym okienku można wybrać, które pliki mają być umieszczane w udostępnionym projekcie kodu, które mają zostać umieszczone w projekcie biblioteki statycznej. W każdym miejscu docelowym listy elementy **docelowe do zaimportowania** można kontrolować, które pliki mają być umieszczane w **elementach projektu współużytkowanego kodu** i **elementy projektu biblioteki statycznej** przy użyciu przycisków w górę i w dół.

   ![Importuj z okienka elementów docelowych biblioteki Xcode](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "Importuj z okienka elementów docelowych biblioteki Xcode")

   Współużytkowany projekt kodu jest sposobem udostępniania zestawu plików źródłowych między projektami w programie Visual Studio. Kod jest tworzony w ramach projektu, który zawiera go, a nie jako projekt własny. Projekty zawierające kod współużytkowany mogą mieć różne architektury i konfiguracje. Współużytkowany projekt kodu jest najlepszym sposobem zapewnienia pojedynczego projektu, który zawiera kod, który może być zbudowany dla wielu rodzajów platform.

   Gdy pliki w poszczególnych projektach są zadowalające, wybierz pozycję **dalej** , aby kontynuować.

1. Użyj okienka **Właściwości globalne** , aby ustawić ścieżkę wyszukiwania struktury i ścieżkę wyszukiwania nagłówka include dla wszystkich projektów systemu iOS w programie Visual Studio. Program Visual Studio używa tych ścieżek do przeglądania kodu źródłowego i funkcji IntelliSense. Te ścieżki globalne są przydatne podczas tworzenia projektów systemu iOS, które korzystają ze wspólnego zestawu nagłówków i struktur.

   ![Importuj z okienka Właściwości globalne Xcode](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "Importuj z okienka Właściwości globalne Xcode")

   Te ścieżki globalne można także ustawić w programie Visual Studio w oknie dialogowym **Opcje** . Aby je znaleźć, w menu **Narzędzia** wybierz polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń pozycję **międzyplatformowe**  > **C++**  > **iOS**  > **Właściwości globalne**.

   Wybierz pozycję **dalej** , aby kontynuować.

1. Okienko **struktury** służy do konfigurowania ścieżek używanych przez program Visual Studio do przeglądania i IntelliSense dla projektu. Ścieżki muszą być dostępne dla programu Visual Studio dla każdej struktury, do której odwołuje się projekt Xcode. Kreator sprawdza odwołania do struktury w projektach Xcode i wyświetla, czy program Visual Studio może znaleźć strukturę. Wszystkie ścieżki, które zostały już skonfigurowane we właściwościach globalnych, powinny być odnajdywane przez program Visual Studio. Wyjątki są wymienione na liście struktury. Dla każdej struktury wymienionej przy użyciu X podaj ścieżkę dostępu do komputera dla programu Visual Studio, aby znaleźć strukturę. Możesz użyć przycisku Przeglądaj, aby użyć okna dialogowego **Wybierz folder** **, aby znaleźć** ścieżkę. Ścieżką struktury może być kopia lokalna lub udział dostępny w sieci na komputerze Mac.

   ![Importuj z okienka Xcode Frameworks](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "Importuj z okienka Xcode Frameworks")

   Wybierz pozycję **dalej** , aby kontynuować.

1. W okienku **Ustawienia projektu** można zmienić strukturę i uwzględnić ustawienia ścieżki wyszukiwania nagłówka dla każdego projektu tworzonego przez kreatora. To okienko służy do ustawiania ścieżek specyficznych dla projektu, które różnią się od ustawień globalnych.

   Aby ustawić ścieżkę dla określonego projektu, na liście rozwijanej **projekt docelowy** wybierz plik projektu. Następnie ustaw wartości w **ścieżce wyszukiwania struktury** i **Uwzględnij kontrolki ścieżki wyszukiwania nagłówka** . Możesz użyć przycisku Przeglądaj **...** obok każdej kontrolki, aby użyć okna dialogowego **Wybierz folder** , aby znaleźć ścieżkę.

   ![Importuj z okienka projektów Xcode](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "Importuj z okienka projektów Xcode")

   Jeśli żaden zdalny komputer Mac nie został sparowany z tym komputerem w programie Visual Studio, zostanie wyświetlony link **Konfiguruj maszynę zdalną** . Aby uzyskać instrukcje dotyczące sposobu konfigurowania parowania, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

   Aby zaimportować projekt Xcode za pomocą ustawień kreatora, wybierz pozycję **Importuj**.

   Kreator importu z Xcode tworzy projekty w programie Visual Studio odpowiadające wybranym obiektom docelowym projektu Xcode. Kod, który może być współużytkowany z innymi C++ projektami, jest podzielony na osobny kod współużytkowany i statyczne projekty biblioteki. Pozostały kod jest umieszczany w projektach biblioteki i aplikacji systemu iOS, które mogą być kompilowane zdalnie przez program Visual Studio. Aby uzyskać więcej informacji na temat przesuwania kodu między programem Visual Studio i Xcode, zobacz [Synchronizacja zmian między Xcode i Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Instalowanie aplikacji mobilnych dla wielu platform za pomocą programuC++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
