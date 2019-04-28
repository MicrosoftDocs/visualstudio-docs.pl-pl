---
title: Zabezpieczanie rozwiązań pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 31a17fdf51e838405c93efca79d7994cd40ece5c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978608"
---
# <a name="secure-office-solutions"></a>Zabezpieczanie rozwiązań pakietu Office
  Model zabezpieczeń dla rozwiązań pakietu Office obejmuje kilka technologii: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], Centrum zaufania w programie Microsoft Office i strefy witryn z ograniczeniami programu Internet Explorer. W poniższych sekcjach opisano, jak działają funkcje zabezpieczeń:

- [Udzielanie zaufania do rozwiązań pakietu Office](#GrantingTrustToSolutions)

- [Udzielanie zaufania do dokumentów](#GrantingTrustToDocuments)

- [Udzielanie zaufania przy użyciu Instalatora Windows](#GrantingTrustWindowsInstaller)

- [Zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office](#Security)

- [Zabezpieczeń w czasie projektowania](#SecurityDuringDeployment)

- [Visual Studio Tools dla pakietu Office runtime](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="GrantingTrustToSolutions"></a> Udzielanie zaufania do rozwiązań pakietu Office
 Udzielanie zaufania do rozwiązań pakietu Office oznacza modyfikowanie zasad zabezpieczeń każdego użytkownika końcowego można ufać rozwiązania dla pakietu Office na podstawie dowodów następujące:

- Certyfikat użyty do podpisania manifestu wdrażania.

- Adres URL pliku manifestu wdrożenia.

  Aby uzyskać więcej informacji, zobacz [udzielenia zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md).

## <a name="GrantingTrustToDocuments"></a> Udzielanie zaufania do dokumentów
 Dostosowania poziomu dokumentu wymaga, aby dokument w katalogu, który jest wyznaczone jako zaufaną lokalizację. Aby uzyskać więcej informacji, zobacz [udzielenia zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

## <a name="GrantingTrustWindowsInstaller"></a> Udzielanie zaufania przy użyciu Instalatora Windows
 Instalator Windows można użyć do utworzenia pliku MSI do zainstalowania rozwiązań pakietu Office do katalogu Program Files, co wymaga uprawnień administratora. Dla rozwiązań pakietu Office w katalogu Program Files Visual Studio 2010 Tools dla pakietu Office runtime uwzględnia tych rozwiązań dla pakietu Office jest zaufany, a nie jest wyświetlany monit o udzielenie zaufania ClickOnce.

## <a name="Security"></a> Zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office
 Funkcjach zabezpieczeń zapewnianych przez [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], i Microsoft Office może pomóc w ochronie przed różne potencjalne zagrożenia w rozwiązaniach pakietu Office. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md).

## <a name="SecurityDuringDeployment"></a> Zabezpieczeń w czasie projektowania
 Aby ułatwić proces programowania, program Visual Studio ustawia zasady zabezpieczeń, która jest wymagana do uruchamiania i debugowania rozwiązania na komputerze za każdym razem, gdy kompilujesz projekt. W niektórych scenariuszach może być konieczne podjąć kroki dodatkowe zabezpieczenia, aby tworzenie projektu.

### <a name="document-level-solutions"></a>Rozwiązaniach na poziomie dokumentu
 W pełni kwalifikowaną ścieżkę dokumentu muszą być dodane do listy zaufanych lokalizacji w aplikacji Microsoft Office, jeśli tworzysz następujące typy projektów:

- Poziomu dokumentu rozwiązań, które są w sieciowym udziale plików, takich jak  *\\\servername\sharename*.

- Poziomu dokumentu rozwiązań dla programu Word, używanego przez *doc* lub *docm* plików.

  Uwzględnij podkatalogi, przy Dodaj lokalizację dokumentu do listy zaufanych lokalizacji lub specjalnie obejmują debugowania i tworzenia folderów. Aby uzyskać więcej informacji, zobacz artykuł pomocy Online pakietu Office Microsoft [Utwórz, usuń lub zmień zaufanej lokalizacji plików](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

### <a name="temporary-certificates"></a>Tymczasowe certyfikaty
 Visual Studio tworzy tymczasowy certyfikat, jeśli certyfikat podpisywania jeszcze nie istnieje. Należy użyć tego certyfikatu tymczasowe tylko podczas programowania i zakupu oficjalnych certyfikatów dla wdrożenia.

 Tymczasowy certyfikat jest generowany po pierwszym utworzeniu projektu pakietu Office. Następnym naciśnięciu klawisza **F5**, projekt zostanie ponownie skompilowany, ponieważ projekt jest oznaczony jako zmienione po dodaniu certyfikatu.

 Może istnieć wiele certyfikatów tymczasowych jakiś czas, dlatego należy wyczyścić certyfikatów tymczasowych od czasu do czasu.

## <a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools dla pakietu Office runtime
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zawiera funkcje, aby zweryfikować tożsamość wydawcy i uprawnień, które są przypisywane do dostosowania. Weryfikuje tych uprawnień za pośrednictwem sekwencji sprawdzanie zabezpieczeń.

### <a name="security-during-customization-loading"></a>Zabezpieczeń podczas dostosowywania ładowania
 Po załadowaniu dostosowania poziomu dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zawsze sprawdzają, czy dokument jest na liście zaufanych lokalizacji. Ponadto środowisko uruchomieniowe sprawdza, czy rozwiązanie żądań FullTrust w manifeście aplikacji. Podczas ładowania dostosowania, wykonuje nie dodatkowe kontrole zabezpieczeń.

### <a name="sequence-of-security-checks-during-installation"></a>Sekwencja kontrole zabezpieczeń podczas instalacji
 Po zainstalowaniu lub zaktualizowaniu rozwiązań pakietu Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wykonuje zbiór testów kontrolnych zabezpieczeń w określonej kolejności do podjęcia decyzji o zaufaniu. To rozwiązanie zainstalowaniu lub zaktualizowaniu tylko wtedy, gdy środowisko wykonawcze określa, że rozwiązanie jest zaufany.

 Można uruchomić procesu instalacji w jeden z czterech sposobów: przez uruchomienie programu instalacyjnego, przez otwarcie manifestu wdrażania, otwierając host aplikacji programu Microsoft Office lub uruchamiając *VSTOInstaller.exe*.

 Pierwsze sprawdzanie zabezpieczeń dotyczy tylko rozwiązaniach na poziomie dokumentu. Dokumentu rozwiązania na poziomie dokumentu musi być w zaufanej lokalizacji. Jeśli dokument znajduje się w udziale plików sieci zdalnej lub ma *doc* lub *docm* rozszerzenie nazwy pliku lokalizacji tego dokumentu, należy dodać do listy zaufanych lokalizacji. Aby uzyskać więcej informacji, zobacz [udzielenia zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

 ![Zabezpieczenia VSTO — instalowanie z Microsoft Office](../vsto/media/host-install.png "zabezpieczenia VSTO — instalowanie z Microsoft Office")

 Następny zestaw kontrole zabezpieczeń, które pochodzą z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i ClickOnce. Aby przekazać te testy, rozwiązań pakietu Office muszą zażądać uprawnień FullTrust, być podpisane przy użyciu certyfikatu, który nie znajduje się na liście niezaufanych wydawcy i znajdować się w lokalizacji, która nie znajduje się w strefie Internet Explorer z ograniczeniami. Jeśli certyfikat jest na liście zaufanego wydawcy, to rozwiązanie jest instalowana natychmiast. W przeciwnym razie jeśli go nie zakończyła się niepowodzeniem jeden kontroli, rozwiązanie w dalszym ciągu ostatecznego zestawu testów.

 ![VSTO zabezpieczeń dotyczące instalowania rozwiązań](../vsto/media/installing.png "VSTO zabezpieczeń dotyczące instalowania rozwiązań")

 Jeśli [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monit o udzielenie zaufania jest dozwolone i rozwiązania nie ma jeszcze udzielonego zaufania, środowisko uruchomieniowe umożliwi decyzji zaufania, który ma zostać wykonane przez użytkownika końcowego. Jeśli użytkownik udziela zaufanie do rozwiązania, wpis zostanie dodany do listy dołączania użytkowników. Wszystkie rozwiązania na liście dołączania użytkowników mają pełnego zaufania i można instalować i uruchom.

 Począwszy od programu Visual Studio 2010, lista dołączania jest pomijany, jeśli zainstalowano rozwiązania dla pakietu Office przy użyciu Instalatora Windows (MSI) do katalogu Program Files. Aby uzyskać więcej informacji, zobacz [zaufania rozwiązań pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![Zabezpieczenia VSTO — przy użyciu Instalatora, aby zainstalować](../vsto/media/setup-vstoinstaller.png "zabezpieczenia VSTO — instalowanie za pomocą Instalatora")

## <a name="see-also"></a>Zobacz także

- [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)
- [Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md)
- [Zaufanie rozwiązań pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Instrukcje: Konfigurowanie zabezpieczeń listy dołączania](../vsto/how-to-configure-inclusion-list-security.md)
- [Instrukcje: Podpisywanie rozwiązań pakietu Office](../vsto/how-to-sign-office-solutions.md)
- [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)
- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce — odwołanie](../deployment/clickonce-reference.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
