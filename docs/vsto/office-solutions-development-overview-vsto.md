---
title: Omówienie programowania rozwiązań dla pakietu Office (VSTO)
description: Dowiedz się, jak opracowywać dostosowania znanych Microsoft Office interfejsów użytkownika i narzędzi, takich jak funkcje przetwarzania słów w programie Word i funkcje analizy danych w programie Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 03da1c8052140bbe23ce4d99c12d72baef18898f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891959"
---
# <a name="office-solutions-development-overview-vsto"></a>Omówienie programowania rozwiązań dla pakietu Office (VSTO)
  Korzystając z Microsoft Office jako frontonu dla rozwiązań, możesz skorzystać ze znanych Microsoft Office interfejsów użytkownika i narzędzi, takich jak funkcje przetwarzania słów w programie Word, funkcje analizy danych programu Excel i funkcje zarządzania pocztą e-mail w programie Outlook. W programie Visual Studio można opracowywać rozwiązania umożliwiające dostosowywanie aplikacji pakietu Office i dodawanie określonych funkcji potrzebnych dla procesów firmy. Można na przykład obrócić program Word do generatora kontraktu, który składa kontrakty z istniejących części, które mogą być edytowane lub niemożliwe do edycji. W programie Excel można utworzyć zautomatyzowany arkusz budżetu dostosowany do różnych projektów. Użytkownicy mogą również korzystać z rozwiązań pakietu Office w trybie offline, co sprawia, że złożone rozwiązania są bardziej praktyczne niż w przypadku używania architektury opartej na sieci Web.

 Ten temat zawiera omówienie typów rozwiązań pakietu Office, które można utworzyć za pomocą szablonów Visual Studio Tools pakietu Office (VSTO) dostępnych w narzędziach Office Developer Tools w programie Visual Studio. Aby uzyskać ogólne informacje na temat sposobu programowania w pakiecie Office, zobacz [Centrum deweloperów pakietu Office](https://developer.microsoft.com/office).

## <a name="choose-an-office-project-type"></a>Wybierz typ projektu pakietu Office
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] udostępnia następujące typy szablonów projektów dla programowania Office opartego na narzędziu VSTO:

- **Dostosowania na poziomie dokumentu** są skojarzone z określonym dokumentem.

- **Dodatki narzędzi VSTO** są skojarzone z samą aplikacją.

  Aby określić, które typy projektów są najlepsze dla danego rozwiązania, należy zastanowić się, czy kod ma być uruchamiany tylko wtedy, gdy określony dokument jest otwarty, lub czy kod ma być dostępny za każdym razem, gdy aplikacja jest uruchomiona. Aby uzyskać więcej informacji o szablonach projektów, zobacz [Office Project Templates Overview](../vsto/office-project-templates-overview.md).

  Typy projektów, które można utworzyć, zależą od aplikacji pakietu Office zainstalowanych na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [dostępność funkcji według aplikacji pakietu Office i typów projektów](../vsto/features-available-by-office-application-and-project-type.md).

### <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentów
 Dostosowania na poziomie dokumentu składają się z zestawu, który jest skojarzony z pojedynczym dokumentem, skoroszytem lub szablonem w programie Microsoft Office Word lub Microsoft Office Excel. Zestaw jest ładowany po otwarciu skojarzonego dokumentu. Funkcje w obszarze dostosowania, które tworzysz, są dostępne tylko wtedy, gdy skojarzony dokument jest otwarty. Dostosowania nie mogą wprowadzać zmian w całej aplikacji, takich jak wyświetlanie nowego elementu menu lub karty wstążki, gdy dowolny dokument jest otwarty.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawiera narzędzia ułatwiające tworzenie dostosowań na poziomie dokumentu. Dostosowany dokument jest hostowany jako powierzchnia projektowa w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , która umożliwia zaprojektowanie dokumentu przez przeciąganie i upuszczanie na niego kontrolek. Wiele innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] funkcji jest dostępnych w projektach na poziomie dokumentu, takich jak kontrolki Windows Forms, powiązanie danych metodą "przeciągnij i upuść" oraz zintegrowany debuger.

 Aby uzyskać więcej informacji na temat dostosowań, zobacz następujące tematy:

- [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Architektura dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>Dodatki narzędzi VSTO
 Dodatki narzędzi VSTO składają się z zestawu, który jest skojarzony z aplikacją Microsoft Office. Zazwyczaj dodatek VSTO jest uruchamiany po uruchomieniu skojarzonej aplikacji, chociaż użytkownicy mogą również ładować dodatki narzędzi VSTO po uruchomieniu aplikacji. Funkcje w dodatkach VSTO, które tworzysz, są dostępne dla aplikacji, niezależnie od tego, które dokumenty są otwarte.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawiera narzędzia, które ułatwiają tworzenie dodatków narzędzi VSTO. Projekty dodatków obejmują automatycznie wygenerowaną klasę, która reprezentuje dodatek narzędzi VSTO. Ta klasa zawiera właściwości i zdarzenia, których można użyć w celu uzyskania dostępu do modelu obiektów aplikacji hosta i uruchomienia kodu po załadowaniu i zamknięciu dodatku VSTO. Wiele innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] funkcji jest dostępnych w projektach dodatku VSTO, takich jak Windows Forms i zintegrowany debuger.

 Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO, zobacz następujące tematy:

- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)

- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatyzowanie aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych
 Można programowo dołączyć funkcje aplikacji pakietu Office do rozwiązania, pisząc kod, który uzyskuje dostęp do modelu obiektów aplikacji. Modele obiektów to rozmieszczenie klas, które udostępniają funkcje poprzez różne właściwości i metody. Model obiektów dla każdej aplikacji pakietu Office jest inny.

 Aby użyć modelu obiektów aplikacji pakietu Office z rozwiązania utworzonego przy użyciu narzędzi programistycznych pakietu Office w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , należy użyć podstawowego zestawu międzyoperacyjnego (PIA) dla aplikacji. PIA umożliwia współdziałanie kodu zarządzanego w rozwiązaniu z modelem obiektów opartym na modelu COM aplikacji pakietu Office.

 Aby wykonywać większość zadań programistycznych, należy zainstalować i zarejestrować pakiet Office zestawów PIA w globalnej pamięci podręcznej zestawów na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Na komputerach użytkowników końcowych nie są wymagane do uruchamiania rozwiązań Office VSTO. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

 Aby uzyskać więcej informacji o korzystaniu z zestawów PIA w rozwiązaniach pakietu Office VSTO, zobacz następujące tematy:

- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)

- [Podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Uruchamianie rozwiązań pakietu Office VSTO firmy Microsoft na komputerach użytkowników końcowych
 Podczas tworzenia rozwiązania pakietu Office VSTO należy wziąć pod uwagę, jak wymagania dotyczące wdrożenia mogą mieć wpływ na opcje deweloperskie.

### <a name="deployment-options"></a>Opcje wdrożenia
 Użyj technologii ClickOnce lub Instalator Windows do wdrożenia rozwiązań utworzonych przy użyciu narzędzi programistycznych pakietu Office w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Wdrożenie ClickOnce umożliwia tworzenie rozwiązań samoaktualizacji, które mogą być instalowane i uruchamiane z minimalnym interakcją użytkownika. Pliki Instalator Windows (*. msi*) mogą być łatwo dystrybuowane do komputerów użytkowników końcowych lub dystrybuowane za pomocą programu Systems Management Server (SMS). Aby uzyskać więcej informacji na temat wdrażania rozwiązań pakietu Office VSTO, zobacz [wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md).

### <a name="install-prerequisites"></a>Instalacja wymagań wstępnych
 Zanim użytkownicy końcowi będą mogli uruchomić rozwiązanie utworzone przy użyciu narzędzi programistycznych pakietu Office w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , na swoich komputerach muszą zostać zainstalowane pewne wymagania wstępne. W przypadku wdrożenia rozwiązania przy użyciu technologii ClickOnce lub tworzenia pliku Instalator Windows te wymagania wstępne można zainstalować razem z rozwiązaniem. Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące wdrażania pakietu Office](/previous-versions/bb608617(v=vs.110)) i [instrukcje: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych w celu uruchamiania rozwiązań pakietu Office](/previous-versions/bb608608(v=vs.110)).

### <a name="security"></a>Zabezpieczenia
 Zabezpieczenia rozwiązań pakietu Office dla programu VSTO są wymuszane przez serię kontroli, która powoduje, że [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] podczas instalowania i ładowania rozwiązania. Te testy obejmują sprawdzenie, czy lokalizacja manifestu wdrożenia jest zaufana, czy certyfikat używany do podpisywania manifestu wdrożenia jest zaufany. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie &#40;Programowanie Office w programie Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Architektura dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
