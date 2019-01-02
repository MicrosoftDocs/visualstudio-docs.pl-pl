---
title: Tworzenie rozwiązań pakietu Office
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8733c4e068bd7c4be2674e302707b81cc180cfd8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963246"
---
# <a name="build-office-solutions"></a>Tworzenie rozwiązań pakietu Office
  Ogólnie rzecz biorąc kompilowanie i debugowanie projektów pakietu Office jest taka sama jak kompilowania i debugowania innych rodzajów projektów w programie Visual Studio, takich jak Windows Forms. W tematach w tej sekcji opisano różnice, które istnieją. Aby uzyskać ogólne informacje o sposobie tworzenia aplikacji, zobacz [skompilować i utworzyć w programie Visual Studio](../ide/compiling-and-building-in-visual-studio.md).

> [!NOTE]
>  Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.

## <a name="project-output-for-office-projects"></a>Dane wyjściowe projektu dla projektów pakietu Office
 Lokalizacja danych wyjściowych dla projektów pakietu Office jest *projectname*\bin\release lub *projectname*\bin\debug. Nie można przeprowadzić kompilacji do katalogu wdrażania.

### <a name="document-level-projects"></a>Projektów na poziomie dokumentu
 Podczas tworzenia projektów dokumentów w danych wyjściowych projektu obejmuje następujące elementy:

-   Kopię dokumentu projektu.

-   Zestaw projektu i wszystkie zestawy referencyjne, które mają ich **Kopiuj lokalnie** właściwością **true**.

-   Manifest aplikacji, który ma rozszerzenie nazwy pliku *.manifest*. Aby uzyskać więcej informacji, zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

-   Manifest wdrożenia, który ma rozszerzenie nazwy pliku *.vsto*. Aby uzyskać więcej informacji, zobacz [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).

-   Bazę danych programu (*PDB*) pliku.

> [!NOTE]
>  W przypadku tworzenia rozwiązania poziomu dokumentu do lokalizacji zdalnej, zamiast komputera lokalnego, należy dodać w pełni kwalifikowaną ścieżkę do listy zaufanych lokalizacji w Centrum zaufania w aplikacji. Aby uzyskać więcej informacji, zobacz sekcję o nazwie udzielanie zaufania do dokumentów w [rozwiązań Secure Office](../vsto/securing-office-solutions.md).

### <a name="application-level-projects"></a>Projektów na poziomie aplikacji
 Podczas tworzenia dodatku narzędzi VSTO dla programów project w danych wyjściowych projektu obejmuje następujące elementy:

- Zestaw projektu i wszystkie zestawy referencyjne, które mają ich **Kopiuj lokalnie** właściwością **true**.

- Manifest aplikacji, który ma rozszerzenie nazwy pliku *.manifest*. Aby uzyskać więcej informacji, zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

- Manifest wdrożenia, który ma rozszerzenie nazwy pliku *.vsto*. Aby uzyskać więcej informacji, zobacz [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).

- Bazę danych programu (*PDB*) w pliku zestawu projektu.

  Proces kompilacji w projektach dodatku narzędzi VSTO tworzy również zestaw wpisów rejestru na komputerze deweloperskim, które są wymagane do załadowania dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

  W przypadku tworzenia projektu dodatku narzędzi VSTO dla programu Outlook zawierający regionów formularzy w procesie kompilacji dodaje następujące dodatkowe informacje do rejestru:

- Klucz dla każdej klasy wiadomości, który jest skojarzony z co najmniej jeden region formularza.

- Wpis dla każdego regionu formularza i skojarzoną wartość, która reprezentuje nazwę dodatku narzędzi VSTO dla programu Outlook.

  Program Outlook musi tych informacji, aby załadować regionów formularza.

## <a name="referenced-assemblies"></a>przywoływanych zestawach
 Możesz odwoływać się zestawów (w tym projekty bibliotek klas) z projektu kompilowanie rozwiązań pakietu Office. Co przywoływany zestaw ma właściwość o nazwie **Kopiuj lokalnie**. **Kopia lokalna** wskazuje, czy zestaw jest kopiowany do katalogu wyjściowego. Domyślnie jest ustawiona **true**. Co przywoływany zestaw, który ma **Kopiuj lokalnie** równa **true** jest kopiowany do katalogu wyjściowego.

## <a name="security-during-the-build-process"></a>Zabezpieczenia w procesie kompilacji
 Program Visual Studio automatycznie konfiguruje ustawienia zabezpieczeń na komputerze deweloperskim udzielenia zaufania rozwiązaniu podczas procesu kompilacji. Dzięki temu rozwiązaniu była uruchamiana podczas jej debugowania.

 Projekty pakietu Office za pomocą certyfikatów zweryfikować wydawcy. Program Visual Studio automatycznie tworzy tymczasowy certyfikat, aby zidentyfikować rozwiązań pakietu Office i konfiguruje na komputerze deweloperskim ufać certyfikatowi tymczasowych.

 Aby uzyskać więcej informacji, zobacz [rozwiązań Secure Office](../vsto/securing-office-solutions.md).

### <a name="network-projects"></a>Projekty sieci
 Jeśli lokalizacja zestawu lub dokumentu znajduje się w udziale sieciowym, aktualizacji zasady zabezpieczeń lokalnych (na poziomie użytkownika) nie jest wystarczająco, aby umożliwić uruchomienie rozwiązania. Administrator musi udzielić pełnego zaufania na poziomie komputera do zestawów i dokumenty, które są w udziale sieciowym, zanim rozwiązanie będzie uruchamiany. Aby uzyskać więcej informacji o sposobie ustawiania zasad zabezpieczeń, zobacz [rozwiązań Secure Office](../vsto/securing-office-solutions.md).

 Dla projektów na poziomie dokumentu należy dodać w pełni kwalifikowaną lokalizację dokumentu do listy zaufanych folderów pakietu Office. Aby uzyskać więcej informacji, zobacz [udzielenia zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

## <a name="change-the-platform-target"></a>Zmiana platformy docelowej
 Domyślnie platforma docelowa dla projektów pakietu Office jest **dowolny Procesor**. Zazwyczaj nie należy zmieniać tego ustawienia. Rozwiązań pakietu Office, które są tworzone za pomocą **dowolny Procesor** platformę docelową, ustawienia uruchamiania w 32-bitowych i 64-bitowych wersjach pakietu Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].

 Platforma docelowa x64 należy ustawić tylko wtedy, gdy tworzysz rozwiązanie, które będzie uruchamiane tylko w 64-bitowe wersje programu Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], i rozwiązania wywołań natywnych interfejsów API w 64-bitowych. Aby uzyskać więcej informacji o zmienianiu ustawienie obiektu docelowego platformy, zobacz [jak: Konfigurowanie projektów pod kątem platform docelowych](../ide/how-to-configure-projects-to-target-platforms.md).

 Jeśli ustawisz x64 platformę docelową rozwiązania nie będzie działać w 32-bitowe wersje systemu Windows lub pakietu Office. X64 platformy docelowej wymaga rozwiązanie do uruchamiania w procesie 64-bitowym.

## <a name="use-the-clean-command"></a>Użyj polecenia Wyczyść
 Usuwanie plików projektu utworzonych na komputerze deweloperskim, można użyć **czysty** polecenie **kompilacji** menu w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. **Czysty** polecenie usuwa wszystkie pliki w lokalizacji wyjściowej kompilacji. Dla projektów na poziomie aplikacji **czysty** polecenie również usuwa wpisy z rejestru, które są tworzone przez proces kompilacji.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Debugowanie projektów pakietu Office](../vsto/debugging-office-projects.md)|Przedstawia informacje o zagadnieniach dotyczących debugowanie projektów pakietu Office.|
|[Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Pokazuje, jak utworzyć podstawowe dostosowanie poziomu dokumentu dla programu Excel.|
|[Instrukcje: Ponowne włączanie dodatku narzędzi VSTO dla programów, która została wyłączona](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Opisuje sposób ponownie włączyć dodatek narzędzi VSTO dla programów trudne lub nietrwałe wyłączono.|
|[Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)|Zawiera łącza do informacji o tworzeniu rozwiązań pakietu Office i informacji na temat roli zestawy w rozwiązaniu.|