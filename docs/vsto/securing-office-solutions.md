---
title: Zabezpieczanie rozwiązań pakietu Office
description: Dowiedz się, jak model zabezpieczeń dla rozwiązań pakietu Office obejmuje kilka technologii, w tym Visual Studio Tools dla środowiska uruchomieniowego pakietu Office i technologii ClickOnce.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3576bdc41f25b95b68230e09e07b1a5ed97016c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906653"
---
# <a name="secure-office-solutions"></a>Zabezpieczanie rozwiązań pakietu Office
  Model zabezpieczeń dla rozwiązań pakietu Office obejmuje kilka technologii: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] , Centrum zaufania w Microsoft Office i strefy witryn z ograniczeniami programu Internet Explorer. W poniższych sekcjach opisano, jak działają różne funkcje zabezpieczeń:

- [Udzielanie zaufania do rozwiązań pakietu Office](#GrantingTrustToSolutions)

- [Udzielanie zaufania do dokumentów](#GrantingTrustToDocuments)

- [Udzielanie zaufania przy użyciu Instalator Windows](#GrantingTrustWindowsInstaller)

- [Szczególne zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office](#Security)

- [Bezpieczeństwo podczas opracowywania](#SecurityDuringDeployment)

- [Visual Studio Tools for Office Runtime](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="grant-trust-to-office-solutions"></a><a name="GrantingTrustToSolutions"></a> Udzielanie zaufania do rozwiązań pakietu Office
 Przyznanie zaufania do rozwiązań pakietu Office oznacza modyfikację zasad zabezpieczeń każdego użytkownika końcowego w celu zaufania rozwiązania pakietu Office w oparciu o następujące dowody:

- Certyfikat używany do podpisywania manifestu wdrożenia.

- Adres URL manifestu wdrożenia.

  Aby uzyskać więcej informacji, zobacz [udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md).

## <a name="grant-trust-to-documents"></a><a name="GrantingTrustToDocuments"></a> Udzielanie zaufania do dokumentów
 Dostosowanie na poziomie dokumentu wymaga, aby dokument znajdował się w katalogu wyznaczyć jako zaufaną lokalizację. Aby uzyskać więcej informacji, zobacz [przyznawanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

## <a name="grant-trust-when-using-windows-installer"></a><a name="GrantingTrustWindowsInstaller"></a> Udzielanie zaufania przy użyciu Instalator Windows
 Za pomocą Instalator Windows można utworzyć plik MSI w celu zainstalowania rozwiązań pakietu Office w katalogu Program Files, który wymaga uprawnień administratora. W przypadku rozwiązań pakietu Office w katalogu Program Files środowisko uruchomieniowe programu Visual Studio 2010 Tools for Office uważa, że te rozwiązania pakietu Office są zaufane i nie wyświetlają monitu zaufania ClickOnce.

## <a name="specific-security-considerations-for-office-solutions"></a><a name="Security"></a> Szczególne zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office
 Funkcje zabezpieczeń zapewniane przez [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] i Microsoft Office mogą pomóc w ochronie przed różnymi zagrożeniami bezpieczeństwa w rozwiązaniach pakietu Office. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md).

## <a name="security-during-development"></a><a name="SecurityDuringDeployment"></a> Bezpieczeństwo podczas opracowywania
 Aby ułatwić proces opracowywania, program Visual Studio ustawia zasady zabezpieczeń wymagane do uruchamiania i debugowania rozwiązania na komputerze za każdym razem, gdy kompilujesz projekt. W niektórych scenariuszach może być konieczne wykonanie dodatkowych czynności w celu utworzenia projektu.

### <a name="document-level-solutions"></a>Rozwiązania na poziomie dokumentu
 W pełni kwalifikowana ścieżka dokumentu musi zostać dodana do listy zaufanych lokalizacji w aplikacji Microsoft Office, jeśli tworzysz następujące typy projektów:

- Rozwiązania na poziomie dokumentu, które znajdują się w sieciowym udziale plików, np. *\\ \servername\sharename*.

- Rozwiązania na poziomie dokumentu dla programu Word, które używają plików *doc* lub *docm* .

  Uwzględnij podkatalogi po dodaniu lokalizacji dokumentu do listy zaufanych lokalizacji lub w specjalnym folderze debugowania i kompilacji. Aby uzyskać więcej informacji, zobacz artykuł pomocy online Microsoft Office [tworzenia, usuwania lub zmieniania zaufanej lokalizacji plików](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

### <a name="temporary-certificates"></a>Certyfikaty tymczasowe
 Program Visual Studio tworzy certyfikat tymczasowy, jeśli certyfikat podpisywania jeszcze nie istnieje. Tego certyfikatu tymczasowego należy używać tylko podczas opracowywania i zakupić oficjalny certyfikat do wdrożenia.

 Tymczasowy certyfikat jest generowany po pierwszym skompilowaniu projektu pakietu Office. Przy następnym naciśnięciu klawisza **F5** projekt zostanie odbudowany, ponieważ projekt jest oznaczony jako zmieniony podczas dodawania certyfikatu.

 Za chwilę może istnieć wiele certyfikatów tymczasowych, dlatego należy wyczyścić tymczasowe certyfikaty sporadycznie.

## <a name="visual-studio-tools-for-office-runtime"></a><a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools dla środowiska uruchomieniowego pakietu Office
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Program zawiera funkcje służące do weryfikowania tożsamości wydawcy i uprawnień, które są udzielane dostosowaniu. Weryfikuje te uprawnienia za pomocą sekwencji kontroli zabezpieczeń.

### <a name="security-during-customization-loading"></a>Zabezpieczenia podczas ładowania dostosowania
 Po załadowaniu dostosowania na poziomie dokumentu program sprawdza, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] czy dokument znajduje się na liście zaufanych lokalizacji. Ponadto środowisko uruchomieniowe sprawdza, czy rozwiązanie zażąda FullTrust w manifeście aplikacji. Podczas ładowania dostosowania nie wykonuje żadnych dodatkowych kontroli zabezpieczeń.

### <a name="sequence-of-security-checks-during-installation"></a>Sekwencja kontroli zabezpieczeń podczas instalacji
 Po zainstalowaniu lub zaktualizowaniu rozwiązania pakietu Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wykonuje zestaw kontroli zabezpieczeń w określonej kolejności, aby przeprowadzić decyzję zaufania. Rozwiązanie jest instalowane lub aktualizowane tylko wtedy, gdy środowisko uruchomieniowe ustali, że rozwiązanie jest zaufane.

 Proces instalacji można rozpocząć na jeden z czterech sposobów: uruchamiając program instalacyjny, otwierając manifest wdrożenia, otwierając hosta aplikacji Microsoft Office lub uruchamiając polecenie *VSTOInstaller.exe*.

 Pierwsze sprawdzenie zabezpieczeń dotyczy tylko rozwiązań na poziomie dokumentu. Dokument rozwiązania poziomu dokumentu musi znajdować się w zaufanej lokalizacji. Jeśli dokument znajduje się w zdalnym udziale plików lub ma rozszerzenie nazwy pliku *. doc* lub *. docm* , należy dodać lokalizację dokumentu do listy zaufanych lokalizacji. Aby uzyskać więcej informacji, zobacz [przyznawanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

 ![Zabezpieczenia programu VSTO — Instalowanie z Microsoft Office](../vsto/media/host-install.png "Zabezpieczenia programu VSTO — Instalowanie z Microsoft Office")

 Następny zestaw kontroli zabezpieczeń należy do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i ClickOnce. Aby przekazać te testy, rozwiązania pakietu Office muszą żądać uprawnień FullTrust, być podpisane przy użyciu certyfikatu, który nie znajduje się na liście niezaufanych wydawców, i znajdować się w lokalizacji, która nie znajduje się w strefie ograniczonej programu Internet Explorer. Jeśli certyfikat znajduje się na liście zaufanych wydawców, rozwiązanie zostanie zainstalowane natychmiast. W przeciwnym razie, jeśli nie wystąpił błąd jednego z testów, rozwiązanie przejdzie do końcowego zestawu kontroli.

 ![Zabezpieczenia narzędzia VSTO dotyczące instalowania rozwiązań](../vsto/media/installing.png "Zabezpieczenia narzędzia VSTO dotyczące instalowania rozwiązań")

 Jeśli [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monit zaufania jest dozwolony i rozwiązanie nie zostało jeszcze przyznane zaufanie, środowisko uruchomieniowe zezwoli na podejmowanie decyzji zaufania przez użytkownika końcowego. Jeśli użytkownik przyznaje zaufanie do rozwiązania, wpis zostanie dodany do listy dołączania użytkowników. Wszystkie rozwiązania na liście dołączania użytkowników mają pełne zaufanie i można je zainstalować i uruchomić.

 Począwszy od programu Visual Studio 2010, lista dołączania jest pomijana, jeśli rozwiązanie pakietu Office zostanie zainstalowane przy użyciu Instalator Windows (MSI) w katalogu Program Files. Aby uzyskać więcej informacji, zobacz artykuł dotyczący [zaufanych rozwiązań pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![Zabezpieczenia programu VSTO — Używanie Instalatora do instalacji](../vsto/media/setup-vstoinstaller.png "Zabezpieczenia programu VSTO — Używanie Instalatora do instalacji")

## <a name="see-also"></a>Zobacz też

- [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)
- [Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md)
- [Ufanie rozwiązaniom pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Instrukcje: Konfigurowanie zabezpieczeń listy dołączania](../vsto/how-to-configure-inclusion-list-security.md)
- [Instrukcje: podpisywanie rozwiązań pakietu Office](../vsto/how-to-sign-office-solutions.md)
- [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)
- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Dokumentacja technologii ClickOnce](../deployment/clickonce-reference.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
