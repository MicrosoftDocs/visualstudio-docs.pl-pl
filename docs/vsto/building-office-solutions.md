---
title: Tworzenie rozwiązań pakietu Office
ms.date: 08/14/2019
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3f89e20b710584c678c035f4d85034e90bb11323
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551844"
---
# <a name="build-office-solutions"></a>Tworzenie rozwiązań pakietu Office
  Ogólnie rzecz biorąc, kompilowanie i Debugowanie projektów pakietu Office jest takie samo jak Kompilowanie i debugowanie innych typów projektów w programie Visual Studio, takich jak Windows Forms. W tematach w tej sekcji opisano różnice, które istnieją. Aby uzyskać ogólne informacje o sposobie tworzenia aplikacji, zobacz [Kompilowanie i kompilowanie w programie Visual Studio](../ide/compiling-and-building-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="project-output-for-office-projects"></a>Dane wyjściowe projektu dla projektów pakietu Office
 Lokalizacją wyjściową dla projektów pakietu Office jest *ProjectName*\bin\Release lub *ProjectName*\bin\debug. Nie można skompilować do katalogu wdrożenia.

### <a name="document-level-projects"></a>Projekty na poziomie dokumentu
 Podczas kompilowania projektu na poziomie dokumentu w danych wyjściowych projektu zawarte są następujące elementy:

- Kopia dokumentu projektu.

- Zestaw projektu i wszystkie zestawy, do których istnieją odwołania, których właściwość **copy Local** ma ustawioną **wartość true**.

- Manifest aplikacji, który ma rozszerzenie nazwy pliku *. manifest*. Aby uzyskać więcej informacji, zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

- Manifest wdrożenia, który ma rozszerzenie nazwy pliku *VSTO*. Aby uzyskać więcej informacji, zobacz [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).

- Plik bazy danych programu (*PDB*).

> [!NOTE]
> Jeśli tworzysz rozwiązanie na poziomie dokumentu do lokalizacji zdalnej, a nie na komputerze lokalnym, Dodaj w pełni kwalifikowaną ścieżkę do listy zaufanych lokalizacji w centrum zaufania aplikacji. Aby uzyskać więcej informacji, zobacz sekcję o nazwie przyznawania zaufania do dokumentów w [bezpiecznych rozwiązaniach pakietu Office](../vsto/securing-office-solutions.md).

### <a name="application-level-projects"></a>Projekty na poziomie aplikacji
 Podczas kompilowania projektu dodatku VSTO następujące elementy są zawarte w danych wyjściowych projektu:

- Zestaw projektu i wszystkie zestawy, do których istnieją odwołania, których właściwość **copy Local** ma ustawioną **wartość true**.

- Manifest aplikacji, który ma rozszerzenie nazwy pliku *. manifest*. Aby uzyskać więcej informacji, zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

- Manifest wdrożenia, który ma rozszerzenie nazwy pliku *VSTO*. Aby uzyskać więcej informacji, zobacz [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).

- Plik bazy danych programu (*PDB*) dla zestawu projektu.

  Proces kompilacji dla projektów dodatków VSTO tworzy również zestaw wpisów rejestru na komputerze deweloperskim, który jest wymagany do załadowania dodatku VSTO. Aby uzyskać więcej informacji, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

  Jeśli kompilujesz projekt dodatku VSTO programu Outlook zawierający regiony formularzy, proces kompilacji dodaje do rejestru następujące informacje dodatkowe:

- Klucz dla każdej klasy komunikatów, która jest skojarzona z co najmniej jednym regionem formularza.

- Wpis dla każdego regionu formularza i skojarzona wartość, która reprezentuje nazwę dodatku narzędzi VSTO dla programu Outlook.

  Program Outlook potrzebuje tych informacji do załadowania regionów formularza.

## <a name="referenced-assemblies"></a>Przywoływane zestawy
 Można odwoływać się do zestawów (łącznie z projektami biblioteki klas) z projektu tworzenia rozwiązań pakietu Office. Każdy przywoływany zestaw ma właściwość o nazwie **copy Local**. **Copy Local** wskazuje, czy zestaw jest kopiowany do katalogu wyjściowego. Domyślnie jest ustawiona **wartość true**. Każdy przywoływany zestaw, który ma **kopię lokalną** ustawioną na **wartość true** , jest kopiowany do katalogu wyjściowego.

## <a name="security-during-the-build-process"></a>Zabezpieczenia w procesie kompilacji
 Program Visual Studio automatycznie skonfiguruje ustawienia zabezpieczeń na komputerze deweloperskim, aby przyznać zaufanie do rozwiązania podczas procesu kompilacji. Pozwala to na uruchamianie rozwiązania podczas jego debugowania.

 Projekty pakietu Office używają certyfikatów do zweryfikowania wydawcy. Program Visual Studio automatycznie tworzy tymczasowy certyfikat do identyfikowania rozwiązań pakietu Office i konfiguruje komputer deweloperski, aby ufać certyfikatowi tymczasowemu.

 Aby uzyskać więcej informacji, zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).

### <a name="network-projects"></a>Projekty sieciowe
 Jeśli lokalizacja zestawu lub dokumentu znajduje się w udziale sieciowym, aktualizacja zasad zabezpieczeń lokalnych (na poziomie użytkownika) nie jest wystarczająca, aby można było uruchomić rozwiązanie. Przed uruchomieniem rozwiązania administrator musi udzielić pełnemu zaufania na poziomie komputera do zestawów i dokumentów znajdujących się w udziale sieciowym. Aby uzyskać więcej informacji na temat sposobu ustawiania zasad zabezpieczeń, zobacz [Secure Solutions Office](../vsto/securing-office-solutions.md).

 W przypadku projektów na poziomie dokumentu należy również dodać w pełni kwalifikowaną lokalizację dokumentu do listy zaufanych folderów pakietu Office. Aby uzyskać więcej informacji, zobacz [przyznawanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

## <a name="change-the-platform-target"></a>Zmień obiekt docelowy platformy
 Domyślnie platforma docelowa platformy dla projektów pakietu Office to **dowolny procesor**. Zazwyczaj nie należy zmieniać tego ustawienia. Rozwiązania pakietu Office utworzone przy użyciu dowolnego ustawienia docelowej platformy **procesora CPU** działają w 32-bitowych i 64-bitowych wersjach firmy Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].

 Należy ustawić platformę docelową na x64 tylko wtedy, gdy tworzysz rozwiązanie, które będzie działać tylko w 64-bitowych wersjach firmy [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] Microsoft [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]lub, a rozwiązanie wywoła natywne, 64-bitowe interfejsy API. Aby uzyskać więcej informacji na temat zmiany ustawienia obiektu docelowego platformy [, zobacz How to: Skonfiguruj projekty na platformach](../ide/how-to-configure-projects-to-target-platforms.md)docelowych.

 Jeśli ustawisz platformę docelową x64, rozwiązanie nie będzie działać w 32-bitowych wersjach systemu Windows lub Office. Obiekt docelowy platformy x64 wymaga, aby rozwiązanie było uruchamiane w procesie 64-bitowym.

## <a name="use-the-clean-command"></a>Użyj czystego polecenia
 Aby usunąć skompilowane pliki projektu z komputera deweloperskiego, można użyć polecenia **Oczyść** w menu **kompilacja** w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Polecenie **Clean** usuwa wszystkie pliki w lokalizacji danych wyjściowych kompilacji. W przypadku projektów na poziomie aplikacji **czyste** polecenie usuwa również wpisy rejestru, które są tworzone przez proces kompilacji.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Debugowanie projektów pakietu Office](../vsto/debugging-office-projects.md)|Przedstawia problemy związane z debugowaniem projektów pakietu Office.|
|[Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Pokazuje, jak utworzyć podstawowe dostosowanie poziomu dokumentu dla programu Excel.|
|[Instrukcje: Ponownie włącz dodatek narzędzi VSTO, który został wyłączony](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|W tym artykule opisano, jak ponownie włączyć dodatek narzędzi VSTO, który jest trwały lub elastyczny.|
|[Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)|Zawiera łącza do informacji na temat tworzenia rozwiązań pakietu Office oraz o roli zestawów w rozwiązaniu.|