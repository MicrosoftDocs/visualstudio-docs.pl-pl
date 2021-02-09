---
title: Architektura dodatków narzędzi VSTO
description: Dodatki VSTO utworzone w programie Visual Studio mają funkcje architektury, które podkreślają stabilność i bezpieczeństwo oraz umożliwiają ścisłą pracę z Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 136903bd6d844d57ef06fce5a62506e026355509
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882612"
---
# <a name="architecture-of-vsto-add-ins"></a>Architektura dodatków narzędzi VSTO
  Dodatki VSTO utworzone przy użyciu narzędzi deweloperskich pakietu Office w programie Visual Studio mają funkcje architektury, które podkreślają stabilność i bezpieczeństwo oraz umożliwiają ścisłą pracę z Microsoft Office. W tym temacie opisano następujące aspekty dodatków narzędzi VSTO:

- [Opis dodatków narzędzi VSTO](#UnderstandingAddIns)

- [Składniki dodatków narzędzi VSTO](#AddinComponents)

- [Jak dodatki narzędzi VSTO współpracują z aplikacjami Microsoft Office](#HowAddinsWork)

  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

  Aby uzyskać ogólne informacje na temat tworzenia dodatków narzędzi VSTO, zobacz temat programowanie [rozwiązań pakietu Office omówienie &#40;narzędzia vsto&#41;](../vsto/office-solutions-development-overview-vsto.md) i [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md).

## <a name="understand-vsto-add-ins"></a><a name="UnderstandingAddIns"></a> Opis dodatków narzędzi VSTO
 Korzystając z narzędzi deweloperskich pakietu Office w programie Visual Studio do tworzenia dodatku narzędzi VSTO, należy utworzyć zestaw kodu zarządzanego, który jest ładowany przez aplikację Microsoft Office. Po załadowaniu zestawu zestaw narzędzi VSTO może reagować na zdarzenia, które są zgłaszane w aplikacji (na przykład gdy użytkownik kliknie element menu). Dodatek VSTO może również wywołać model obiektów w celu zautomatyzowania i rozbudowania aplikacji i może użyć dowolnej klasy w obiekcie [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

 Zestaw komunikuje się ze składnikami COM aplikacji za pomocą podstawowego zestawu międzyoperacyjnego aplikacji. Aby uzyskać więcej informacji, zobacz [zestawy podstawowych międzyoperacyjnych pakietu Office](../vsto/office-primary-interop-assemblies.md) i [programowanie rozwiązań pakietu office — Omówienie &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 Jeśli dla aplikacji jest zainstalowanych wiele dodatków VSTO, każdy dodatek Narzędzia VSTO jest ładowany w innej domenie aplikacji. Oznacza to, że jeden dodatek narzędzi VSTO, który zachowuje się nieprawidłowo nie może spowodować niepowodzenia innych dodatków narzędzi VSTO. Pomaga również upewnić się, że po zamknięciu aplikacji wszystkie zestawy dodatków VSTO są zwalniane z pamięci. Aby uzyskać więcej informacji na temat domen aplikacji, zobacz [domeny aplikacji](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> Dodatki VSTO tworzone przy użyciu narzędzi deweloperskich pakietu Office w programie Visual Studio są przeznaczone do użycia tylko wtedy, gdy aplikacja hosta Microsoft Office uruchamiana przez użytkownika końcowego. Jeśli aplikacja jest uruchamiana programowo (na przykład przy użyciu automatyzacji), dodatek narzędzi VSTO może nie zadziałać zgodnie z oczekiwaniami.

## <a name="components-of-vsto-add-ins"></a><a name="AddinComponents"></a> Składniki dodatków narzędzi VSTO
 Chociaż zestaw dodatków narzędzi VSTO jest głównym składnikiem, istnieje kilka innych składników, które odgrywają ważną rolę w sposobie, w jaki Microsoft Office aplikacje odnajdują i ładują dodatki narzędzi VSTO.

### <a name="registry-entries"></a>Wpisy rejestru
 Aplikacje Microsoft Office odnajdują dodatki narzędzi VSTO, szukając zestawu wpisów rejestru. Aby uzyskać pełną listę wpisów rejestru używanych przez dodatki narzędzi VSTO, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

 Podczas kompilowania rozwiązania program Visual Studio tworzy wszystkie wymagane wpisy rejestru na komputerze deweloperskim, aby można było debugować i uruchamiać dodatek narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

 Jeśli używasz technologii ClickOnce do wdrożenia rozwiązania, program instalacyjny wygenerowany przez proces publikowania automatycznie tworzy klucze rejestru na komputerze użytkownika końcowego. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

### <a name="deployment-manifest-and-application-manifest"></a>Manifest wdrożenia i manifest aplikacji
 Dodatki narzędzi VSTO używają manifestów wdrożenia i manifestów aplikacji do identyfikowania i ładowania najnowszej wersji zestawu dodatku VSTO. Manifest wdrożenia wskazuje bieżący manifest aplikacji. Manifest aplikacji wskazuje zestaw dodatku VSTO i określa klasę punktu wejścia do wykonania w zestawie. Aby uzyskać więcej informacji, zobacz [manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools dla środowiska uruchomieniowego pakietu Office
 Aby uruchomić Dodatki VSTO utworzone przy użyciu narzędzi deweloperskich pakietu Office w programie Visual Studio, na komputerach użytkowników końcowych musi być zainstalowany program [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Środowisko uruchomieniowe obejmuje składniki niezarządzane i zestaw zestawów zarządzanych. Składniki niezarządzane załadowały zestaw dodatku VSTO. Zarządzane zestawy udostępniają model obiektów używany przez kod dodatku VSTO do automatyzowania i zwiększania poziomu aplikacji hosta.

 Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="how-vsto-add-ins-work-with-microsoft-office-applications"></a><a name="HowAddinsWork"></a> Jak dodatki narzędzi VSTO współpracują z aplikacjami Microsoft Office
 Gdy użytkownik uruchamia aplikację Microsoft Office, aplikacja używa manifestu wdrażania i manifestu aplikacji do lokalizowania i ładowania najnowszej wersji zestawu dodatku VSTO. Na poniższej ilustracji przedstawiono podstawową architekturę tych dodatków narzędzi VSTO.

 ![Architektura dodatku dla pakietu Office 2007](../vsto/media/office07addin.png "Architektura dodatku dla pakietu Office 2007")

> [!NOTE]
> W rozwiązaniach pakietu Office, które są przeznaczone dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , są wywoływane w modelu obiektów aplikacji hosta za pomocą informacji o typie Pia, które są osadzone w zestawie rozwiązania, zamiast bezpośredniego wywoływania Pia. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Proces ładowania
 Następujące kroki są wykonywane, gdy użytkownik uruchamia aplikację:

1. Aplikacja sprawdza rejestr pod kątem wpisów identyfikujących dodatki narzędzi VSTO, które zostały utworzone przy użyciu narzędzi deweloperskich pakietu Office w programie Visual Studio.

2. Jeśli aplikacja znajdzie te wpisy rejestru, aplikacja ładuje VSTOEE.dll, która ładuje VSTOLoader.dll. Są to niezarządzane biblioteki DLL, które są składnikami modułu ładującego dla programu Visual Studio 2010 Tools for Office Runtime. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

3. *VSTOLoader.dll* ładuje [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] i uruchamia zarządzaną część [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

4. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Sprawdza aktualizacje manifestu i pobiera najnowsze manifesty aplikacji i wdrożenia.

5. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Wykonuje serię kontroli zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).

6. Jeśli dodatek VSTO jest zaufany do uruchomienia, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używa manifestu wdrożenia i manifestu aplikacji, aby sprawdzić dostępność aktualizacji zestawu. Jeśli zostanie udostępniona nowa wersja zestawu, środowisko uruchomieniowe pobierze nową wersję zestawu do [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pamięci podręcznej na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego](../vsto/deploying-an-office-solution.md).

7. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Tworzy nową domenę aplikacji, w której ma zostać załadowany zestaw dodatku VSTO.

8. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Ładuje zestaw dodatku VSTO do domeny aplikacji.

9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Wywołuje <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodę w dodatku VSTO, jeśli został on zastąpiony.

     Opcjonalnie możesz przesłonić tę metodę, aby uwidocznić obiekt w dodatku VSTO do innych rozwiązań Microsoft Office. Aby uzyskać więcej informacji, zobacz [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

10. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Wywołuje <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodę w dodatku VSTO, jeśli został on zastąpiony.

     Opcjonalnie można przesłonić tę metodę, aby rozszerzać Microsoft Office funkcję przez zwrócenie obiektu implementującego interfejs rozszerzalności. Aby uzyskać więcej informacji, zobacz [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

    > [!NOTE]
    > [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Wykonuje odrębne wywołania <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metody dla każdego interfejsu rozszerzalności obsługiwanego przez aplikację hosta. Mimo że pierwsze wywołanie metody jest <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> zwykle wykonywane przed wywołaniem `ThisAddIn_Startup` metody, dodatek VSTO nie powinien wprowadzać żadnych założeń dotyczących tego, kiedy <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> Metoda zostanie wywołana lub ile razy zostanie wywołana.

11. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Wywołuje `ThisAddIn_Startup` metodę w dodatku VSTO. Ta metoda jest domyślnym programem obsługi zdarzeń dla <xref:Microsoft.Office.Tools.AddInBase.Startup> zdarzenia. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Zobacz też
- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office — omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
