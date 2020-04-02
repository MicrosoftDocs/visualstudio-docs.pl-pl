---
title: Omówienie tworzenia rozwiązań pakietu Office (VSTO)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: abb58d30e33ab5cfe713175b40cd32f593921ae9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543947"
---
# <a name="office-solutions-development-overview-vsto"></a>Omówienie tworzenia rozwiązań pakietu Office (VSTO)
  Korzystając z pakietu Microsoft Office jako front-endu dla rozwiązań, można korzystać ze znanych interfejsów i narzędzi użytkownika pakietu Microsoft Office, takich jak funkcje przetwarzania tekstu w programie Word, funkcje analizy danych programu Excel i funkcje zarządzania pocztą e-mail programu Outlook. W programie Visual Studio można tworzyć rozwiązania, aby dostosować aplikacje pakietu Office i dodać określone funkcje potrzebne do procesów biznesowych. Na przykład można przekształcić program Word w generator kontraktów, który montuje kontrakty z wcześniej istniejących części, które mogą być edytowalne lub nie edytowalne. W programie Excel można utworzyć arkusz budżetu zautomatyzowanego dostosowanego do różnych projektów. Użytkownicy mogą również przetraktować rozwiązania biurowe w trybie offline, co sprawia, że złożone rozwiązania są bardziej praktyczne niż w przypadku korzystania z architektury internetowej.

 Ten temat zawiera omówienie typów rozwiązań pakietu Office, które można utworzyć przy użyciu szablonów Narzędzi programu Visual Studio dla pakietu Office (VSTO) dostępnych w narzędziach deweloperskich pakietu Office w programie Visual Studio. Aby uzyskać ogólne informacje dotyczące sposobu tworzenia za pomocą pakietu Office, zobacz [Centrum deweloperów pakietu Office](https://developer.microsoft.com/office).

## <a name="choose-an-office-project-type"></a>Wybieranie typu projektu pakietu Office
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]zawiera następujące typy szablonów projektów dla rozwoju pakietu Office opartego na programie VSTO:

- **Dostosowania na poziomie dokumentu** są skojarzone z określonym dokumentem.

- **Dodatki VSTO** są skojarzone z samą aplikacją.

  Aby zdecydować, który z tych typów projektu jest najlepszy dla danego rozwiązania, zastanów się, czy kod ma być uruchamiany tylko wtedy, gdy określony dokument jest otwarty, czy chcesz, aby kod był dostępny za każdym razem, gdy aplikacja jest uruchomiona. Aby uzyskać więcej informacji na temat szablonów projektów, zobacz [Omówienie szablonów projektów pakietu Office](../vsto/office-project-templates-overview.md).

  Typy projektów, które można utworzyć, zależą od aplikacji pakietu Office zainstalowanych na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [Funkcje dostępne dla aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

### <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentów
 Dostosowania na poziomie dokumentu składają się z zestawu skojarzonego z pojedynczym dokumentem, skoroszytem lub szablonem w programie Microsoft Office Word lub Microsoft Office Excel. Zestaw jest ładowany po otwarciu skojarzonego dokumentu. Funkcje w utworzonych dostosowaniach są dostępne tylko wtedy, gdy skojarzony dokument jest otwarty. Dostosowania nie mogą wprowadzać zmian w całej aplikacji, takich jak wyświetlanie nowego elementu menu lub karty wstążki, gdy dowolny dokument jest otwarty.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]zawiera narzędzia ułatwiające tworzenie dostosowań na poziomie dokumentu. Dostosowany dokument jest hostowany jako powierzchnia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]projektowa, w której można zaprojektować dokument, przeciągając i upuszczając na niego kontrolki. Wiele [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] innych funkcji jest dostępnych w projektach na poziomie dokumentu, takich jak formanty windows forms, powiązanie danych przeciągania i upuszczania oraz zintegrowany debuger.

 Aby uzyskać więcej informacji na temat dostosowań, zobacz następujące tematy:

- [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Architektura dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>Dodatki VSTO
 Dodatki VSTO składają się z zestawu skojarzonego z aplikacją pakietu Microsoft Office. Zazwyczaj dodatek VSTO jest uruchamiany po uruchomieniu skojarzonej aplikacji, chociaż użytkownicy mogą również ładować dodatki VSTO po uruchomieniu aplikacji. Funkcje w dodatkach VSTO, które tworzysz są dostępne dla samej aplikacji, niezależnie od tego, które dokumenty są otwarte.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]zawiera narzędzia ułatwiające tworzenie dodatków VSTO. Ta klasa zawiera właściwości i zdarzenia, których można użyć do uzyskania dostępu do modelu obiektu aplikacji hosta i uruchomić kod, gdy dodatek VSTO jest ładowany i zamykany. Wiele [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] innych funkcji są dostępne w projektach dodatków VSTO, takich jak formularze systemu Windows i wbudowany debuger.

 Aby uzyskać więcej informacji na temat dodatków VSTO, zobacz następujące tematy:

- [Rozpoczęcie programowania dodatków VSTO](../vsto/getting-started-programming-vsto-add-ins.md)

- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatyzowanie aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych
 Można programowo włączyć funkcje aplikacji pakietu Office do rozwiązania, pisząc kod, który uzyskuje dostęp do modelu obiektu aplikacji. Modele obiektów są rozmieszczenie klas, które uwidaczniają funkcjonalność za pośrednictwem różnych właściwości i metod. Model obiektu dla każdej aplikacji pakietu Office jest inny.

 Aby użyć modelu obiektowego aplikacji pakietu Office z rozwiązania utworzonego przy użyciu narzędzi programistycznych pakietu Office w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], należy użyć podstawowego zestawu międzyoperacyjnego (PIA) dla aplikacji. PiA umożliwia kod zarządzany w rozwiązaniu do interakcji z modelu obiektów opartych na modelu obiektowym aplikacji pakietu Office.

 Aby wykonać większość zadań programistycznych, muszą być zainstalowane i zarejestrowane pias pakietu Office w globalnej pamięci podręcznej zestawów na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do tworzenia rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Pias pakietu Office nie są wymagane na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu VSTO Office. Aby uzyskać więcej informacji, zobacz [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

 Aby uzyskać więcej informacji na temat korzystania z pia w rozwiązaniach pakietu Office VSTO, zobacz następujące tematy:

- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)

- [Zespoły międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Uruchamianie rozwiązań pakietu Microsoft VSTO Office na komputerach użytkowników końcowych
 Podczas tworzenia rozwiązania pakietu OFFICE VSTO, należy wziąć pod uwagę, jak wymagania dotyczące wdrażania może mieć wpływ na wybory programistyczne.

### <a name="deployment-options"></a>Opcje wdrożenia
 Użyj funkcji ClickOnce lub Instalator Windows, aby wdrożyć rozwiązania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]utworzone przy użyciu narzędzi programistycznych pakietu Office w programie . ClickOnce wdrożenia umożliwia tworzenie samoaktualizujących rozwiązań, które mogą być instalowane i uruchamiane przy minimalnej interakcji z użytkownikiem. Pliki Instalatora Windows (*msi*) można łatwo dystrybuować na komputerach użytkowników końcowych lub dystrybuować za pomocą programu Systems Management Server (SMS). Aby uzyskać więcej informacji na temat wdrażania rozwiązań pakietu VSTO Office, zobacz [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md).

### <a name="install-prerequisites"></a>Instalacja wymagań wstępnych
 Aby użytkownicy końcowi mogli uruchamiać rozwiązanie utworzone [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]przy użyciu narzędzi programistycznych pakietu Office w , ich komputery muszą mieć zainstalowane pewne wymagania wstępne. Jeśli wdrożysz rozwiązanie przy użyciu ClickOnce lub tworząc plik Instalatora Windows, te wymagania wstępne mogą być instalowane z rozwiązaniem. Aby uzyskać więcej informacji, zobacz [Wymagania wstępne dotyczące rozwiązania pakietu Office dotyczące wdrażania](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e) i [Jak: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych w celu uruchamiania rozwiązań pakietu Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

### <a name="security"></a>Zabezpieczenia
 Zabezpieczenia rozwiązań pakietu VSTO Office są wymuszane przez serię kontroli, które [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] powoduje, że podczas instalowania i ładowania rozwiązania. Kontrole te obejmują sprawdzenie, czy lokalizacja manifestu wdrożenia jest zaufana lub czy certyfikat używany do podpisywania manifestu wdrożenia jest zaufany. Aby uzyskać więcej informacji, zobacz [Rozwiązania bezpiecznego pakietu Office](../vsto/securing-office-solutions.md).

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie &#40;rozwoju pakietu Office w programie Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Architektura dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Rozpoczęcie programowania dodatków VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
