---
title: Projektowanie i tworzenie rozwiązań pakietu Office
description: Dowiedz się, w jaki sposób program Visual Studio udostępnia szablony projektów, których można użyć do tworzenia kilku różnych typów rozwiązań pakietu Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df634a7c242819e4f41a6fddeae4099a3d25fae2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897641"
---
# <a name="design-and-create-office-solutions"></a>Projektowanie i tworzenie rozwiązań pakietu Office

Program Visual Studio zawiera szablony projektów, których można użyć do tworzenia kilku różnych typów rozwiązań pakietu Office. W tej części dokumentacji opisano szablony projektów i przedstawiono wskazówki dotyczące tworzenia projektów pakietu Office. Aby dowiedzieć się, jak zaimplementować dostosowania kodu i interfejsu użytkownika po utworzeniu projektu, zobacz [opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-office-projects"></a>Tworzenie projektów pakietu Office
 Przed rozpoczęciem należy określić wymagania i poznać typ rozwiązania, które oferuje najlepsze dopasowanie. Na przykład jeśli Twoje rozwiązanie pakietu Office musi być uruchamiane za każdym razem, gdy aplikacja jest używana, dodatek VSTO najlepiej odpowiada Twoim wymaganiom. Jeśli kod jest ściśle zintegrowany z pojedynczym dokumentem, Utwórz dostosowanie na poziomie dokumentu. Te typy projektów są dostępne jako szablony projektów programu Visual Studio. Aby uzyskać więcej informacji na temat szablonów projektu pakietu Office, które są dołączone do programu Visual Studio, zobacz [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md). Aby uzyskać więcej informacji o sposobach tworzenia projektów pakietu Office, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Projekty pakietu Office mają funkcje i elementy projektu, które różnią się od innych typów projektów w programie Visual Studio. Na przykład podczas tworzenia projektu na poziomie dokumentu dokument lub skoroszyt w projekcie można otworzyć i edytować w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w środowisku programu Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="choose-a-net-framework-version"></a>Wybierz wersję .NET Framework
 Po wybraniu typu projektu, który najlepiej spełnia Twoje wymagania, możesz wybrać wersję .NET Framework, która ma być używana w procesie tworzenia oprogramowania. W projektach pakietu Office można wskazać następujące wersje .NET Framework:

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  Wersja .NET Framework wybrana dla projektu jest wymagana na komputerach użytkowników końcowych, aby można było uruchomić rozwiązanie. Na przykład, jeśli projekt jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest to wymagane na komputerach użytkowników końcowych. W tym przykładzie rozwiązanie nie zostanie uruchomione, jeśli na komputerach użytkowników końcowych zostanie zainstalowany tylko .NET Framework 3,5.

  W przypadku migrowania projektu dodatku VSTO przeznaczonego dla .NET Framework 3,5, program Visual Studio zmienia platformę docelową projektu na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później w zależności od zainstalowanej wersji pakietu Office.

  Jednak po zmianie platformy docelowej przez program Visual Studio może być konieczne zmodyfikowanie niektórych kodów w projekcie, jeśli są one używane w niektórych funkcjach. Aby uzyskać więcej informacji na temat zmiany platformy docelowej, zobacz [How to: Targeting a Version of a .NET Framework](../ide/visual-studio-multi-targeting-overview.md). Aby uzyskać więcej informacji o zmianach, które mogą być konieczne w projekcie, zobacz [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

  Jeśli program Visual Studio zmieni .NET Framework docelowy dla projektu i używasz technologii ClickOnce do wdrożenia rozwiązania, upewnij się, że wybrano odpowiednią wersję .NET Framework w oknie dialogowym **wymagania wstępne** . Ten wybór nie zmienia się automatycznie po zmianie platformy docelowej dla projektu. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych w celu uruchamiania rozwiązań pakietu Office](/previous-versions/bb608608(v=vs.110)).

> [!NOTE]
> Nie można określić .NET Framework 3,5 lub wcześniej w projektach pakietu Office utworzonych przy użyciu programu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] . Projekty pakietu Office tworzone przy użyciu programu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] wymagają funkcji, które zostały po raz pierwszy wprowadzone w [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Informacje o tym, kiedy zestawów PIA pakietu Office są wymagane na komputerach użytkowników końcowych
 Domyślnie zestawy podstawowych międzyoperacyjnych pakietu Office (zestawów PIA) nie muszą być zainstalowane na komputerach użytkowników końcowych, jeśli właściwość **Osadź typy** współdziałania w projekcie ma ustawioną wartość **true**, która jest wartością domyślną. W tym scenariuszu informacje o typie dla typów PIA, które są używane przez rozwiązanie, są osadzone w zestawie rozwiązania podczas kompilowania projektu. W czasie wykonywania, informacje o typie osadzonym są używane zamiast zestawów Pia do wywołania modelu obiektów opartych na modelu COM aplikacji pakietu Office. Aby uzyskać więcej informacji na temat sposobu osadzenia typów z zestawów PIA w rozwiązaniu, zobacz temat [równoważność typów i osadzone typy międzyoperacyjnych](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).

 Jeśli właściwość **Osadź typy** współdziałania w projekcie ma ustawioną **wartość false**, pakiet Office zestawów Pia musi być zainstalowany i zarejestrowany w globalnej pamięci podręcznej zestawów na każdym komputerze użytkownika końcowego, na którym działa rozwiązanie. W większości przypadków zestawów PIA są instalowane domyślnie z pakietem Office, ale można również włączyć redystrybucyjny PIA jako warunek wstępny dla Twojego rozwiązania. Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące wdrażania pakietu Office](/previous-versions/bb608617(v=vs.110)).

### <a name="understand-the-client-profile"></a>Informacje o profilu klienta
 Profil klienta .NET Framework to podzbiór pełnych .NET Framework. Można wybrać profil klienta .NET Framework, jeśli trzeba używać tylko funkcji klienta w .NET Framework i chcesz zapewnić najszybszy możliwy proces wdrażania dla rozwiązania pakietu Office. Aby uzyskać więcej informacji, zobacz [.NET Framework profilu klienta](/dotnet/framework/deployment/client-profile).

 Podczas tworzenia projektu pakietu Office [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , który jest przeznaczony dla programu, [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] Domyślnie jest to element docelowy. Jeśli chcesz opracować dla pełnej [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , należy ustawić tę opcję po utworzeniu projektu. Aby uzyskać więcej informacji, zobacz [How to: Target of a wersja .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Tworzenie rozwiązań dla 64-bitowej wersji Microsoft Office
 Microsoft Office jest dostępna w 64-bitowych i 32-bitowych wersjach. Aby utworzyć rozwiązania pakietu Office, które mogą być uruchamiane w dowolnej wersji, dla ustawienia cel platformy dla projektu należy ustawić **dowolny procesor**. Jest to wartość domyślna dla projektów pakietu Office. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

 Istnieją oddzielne wersje 64-bitowe i 32-bitowe [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , które są używane przez 64-bitowe i 32-bitowe wersje Microsoft Office. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-office-solutions"></a>Zestawy w rozwiązaniach pakietu Office
 Podczas tworzenia projektu pakietu Office przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, napisany kod jest ostatecznie kompilowany do zestawu. Zestaw jest wdrażany na serwerze udostępnionym lub w katalogu na komputerze klienckim.

 Zestawy w rozwiązaniach pakietu Office są ładowane przez aplikację pakietu Office. Po załadowaniu zestawu kod w zestawie może reagować na zdarzenia, które są zgłaszane w aplikacji, na przykład gdy użytkownik kliknie element menu. Kod w zestawie może również wywołać model obiektów w celu zautomatyzowania i rozbudowania aplikacji i może użyć dowolnej klasy w obiekcie [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] . Aby uzyskać więcej informacji, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md) i [architektury dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md).

 Rozwiązania pakietu Office używają manifestów wdrożenia i manifestów aplikacji do identyfikowania zestawu. Manifesty zawierają informacje o nazwie, wersji i lokalizacji zestawu, aby aplikacja mogła znaleźć, połączyć i uruchomić poprawny zestaw. Aby uzyskać więcej informacji, zobacz [manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Projekty na poziomie dokumentu zawierają również dokumenty oprócz zestawu. Dokument pełni rolę frontonu aplikacji i jest miejscem, w którym odbywa się cała interakcja z użytkownikiem. Każdy dokument może zawierać tylko jeden główny zestaw projektu; Jednak wiele dokumentów może wskazywać na ten sam zestaw.

 Zestawy w projektach na poziomie dokumentu nie są osadzone w dokumencie; Zamiast tego są one przechowywane w innym miejscu i są identyfikowane przez manifest aplikacji dokumentu.

## <a name="security-considerations-for-assemblies"></a>Zagadnienia dotyczące zabezpieczeń zestawów
 Aby można było uruchomić rozwiązanie pakietu Office na komputerze, zestawy używane przez rozwiązanie muszą być zaufane do uruchomienia. Aby uzyskać więcej informacji o zabezpieczeniach, zobacz [Secure Solutions Office](../vsto/securing-office-solutions.md).

 Domyślnie zestaw rozwiązań i wszystkie zestawy, do których istnieją odwołania, które znajdują się w folderze wyjściowym projektu, są zaufane do uruchamiania na komputerze deweloperskim podczas kompilowania projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

 Ze względów bezpieczeństwa najlepiej tworzyć projekty na komputerze lokalnym, a nie rozwijać je w lokalizacji udostępnionej. Aby uzyskać więcej informacji, zobacz [programowanie zespołowe rozwiązań pakietu Office](../vsto/collaborative-development-of-office-solutions.md).

## <a name="referenced-assemblies"></a>Przywoływane zestawy
 Zestaw może odwoływać się do innych zestawów, które są wymienione w odwołaniach projektu. Jednak jeden zestaw projektów na poziomie dokumentu nie może odwoływać się do innego zestawu projektu na poziomie dokumentu.

## <a name="see-also"></a>Zobacz też
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Projekty pakietu Office w środowisku programu Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md)
- [Uruchamianie rozwiązań w różnych wersjach Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [Jak: docelowa aplikacja pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Instrukcje: Konfigurowanie informacji o konfiguracji dla rozwiązania pakietu Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [Korzystanie z funkcji pakietu Office w programie Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Typowe zadania w programowaniu pakietu Office](../vsto/common-tasks-in-office-programming.md)
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)