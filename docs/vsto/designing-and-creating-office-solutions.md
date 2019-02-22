---
title: Projektowanie i tworzenie rozwiązań pakietu Office
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b939640b0676ae34eedeed96c8a4b6b21a5a37e4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599522"
---
# <a name="design-and-create-office-solutions"></a>Projektowanie i tworzenie rozwiązań pakietu Office

Visual Studio udostępnia szablony projektów, których można utworzyć kilka różnych typów rozwiązań dla pakietu Office. Ten rozdział dokumentacji zawiera opis szablonów projektów i zawiera wskazówki dotyczące tworzenia projektów pakietu Office. Aby uzyskać informacje o sposobie implementacji dostosowania interfejsu użytkownika oraz kodu po utworzeniu projektu, zobacz [rozwiązań Office tworzenie](../vsto/developing-office-solutions.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

> [!NOTE]
> Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.

## <a name="create-office-projects"></a>Tworzenie projektów Office
 Przed rozpoczęciem należy określania wymagań dotyczących i Odkryj typ rozwiązania, które oferuje najlepszym rozwiązaniem. Jeśli na przykład rozwiązania pakietu Office należy uruchomić każdym aplikacji jest używany, dodatku narzędzi VSTO najlepsze uniwersalna, odpowiednia wymagań. Jeśli kod jest ściśle zintegrowany z pojedynczego dokumentu, należy utworzyć dostosowywania poziomie dokumentu. Te typy projektów są dostępne jako szablony projektu Visual Studio. Aby uzyskać więcej informacji na temat szablonów projektu pakietu Office, które są dołączone do programu Visual Studio, zobacz [Przegląd szablony projektu pakietu Office](../vsto/office-project-templates-overview.md). Aby uzyskać więcej informacji na temat tworzenia projektów pakietu Office, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Projekty pakietu Office ma funkcje i elementy projektu, które różnią się od innych typów projektów w programie Visual Studio. Na przykład podczas tworzenia projektu na poziomie dokumentu, dokument lub skoroszyt w projekcie można go otworzyć i edytować w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="choose-a-net-framework-version"></a>Wybierz wersję .NET Framework
 Po wybraniu typu projektu, który najlepiej spełnia Twoje wymagania, możesz wybrać wersję programu .NET Framework do użycia w procesie tworzenia aplikacji. Można wskazać następujące wersje .NET Framework w projektach pakietu Office:

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  .NET Framework w wersji wybranego projektu jest wymagany na komputerach użytkowników końcowych dla rozwiązania w celu uruchomienia. Na przykład jeśli projekt jest ukierunkowany [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest wymagane na komputerach użytkowników końcowych. W tym przykładzie rozwiązania nie będzie działać, jeśli tylko program .NET Framework 3.5 jest zainstalowany na komputerach użytkowników końcowych.

  W przypadku migrowania projektów dodatku narzędzi VSTO, który jest przeznaczony dla .NET Framework 3.5 programu Visual Studio zmiany platformy docelowej projektu do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego, w zależności od wersji pakietu Office, który został zainstalowany.

  Jednak po programu Visual Studio zmian platformy docelowej, konieczne może modyfikować część kodu w projekcie, jeżeli będzie używał pewnych funkcji. Aby uzyskać więcej informacji o tym, jak zmienić platformę docelową, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Aby uzyskać więcej informacji o zmianach, konieczne może być w projekcie, zobacz [Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

  Jeśli program Visual Studio zmieni docelową aplikację .NET Framework dla projektu, a używasz ClickOnce do wdrażania rozwiązania, upewnij się, możesz również wybrać odpowiednią wersję programu .NET Framework w **wymagania wstępne** okno dialogowe. Zaznacz to pole wyboru nie zmienia się automatycznie, gdy zmienić platformę docelową dla projektu. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

> [!NOTE]
>  Nie można skierowane do .NET Framework 3.5 lub wyżej w projektach pakietu Office, które tworzysz przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]. Projekty pakietu Office, które tworzysz przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] wymagają funkcji, które zostały najpierw wprowadzone w [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Zrozumieć, kiedy zestawy PIA pakietu Office są wymagane na komputerach użytkowników końcowych
 Domyślnie, podstawowe zestawy międzyoperacyjne (PIA) pakietu Office nie są zainstalowane na komputerach użytkowników końcowych, jeśli **Osadź typy współdziałania** każdego odwołania PIA pakietu Office w projekcie jest właściwością **True**, który jest wartością domyślną. W tym scenariuszu informacji o typie dla typów PIA, które są używane przez rozwiązania jest osadzony w zestawie rozwiązania podczas kompilowania projektu. W czasie wykonywania informacje o typie osadzony służy zamiast zestawów PIA do wywołania w modelu obiektów opartych na modelu COM aplikacji pakietu Office. Aby uzyskać więcej informacji na temat sposobu typów z zestawy PIA są osadzone w rozwiązaniu, zobacz [równoważność typów i osadzone typy międzyoperacyjne](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).

 Jeśli **Osadź typy współdziałania** każdego odwołania PIA pakietu Office w projekcie jest właściwością **False**, zestawy PIA pakietu Office musi być zainstalowane i zarejestrowane w globalnej pamięci podręcznej na każdym komputerze użytkownika końcowego, Uruchamia rozwiązanie. W większości przypadków zestawy PIA są instalowane domyślnie z pakietem Office, ale możesz również uwzględnić PIA do dystrybucji jako warunek wstępny dla Twojego rozwiązania. Aby uzyskać więcej informacji, zobacz [wymagania wstępne rozwiązania pakietu Office wdrożenia](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e).

### <a name="understand-the-client-profile"></a>Zrozumienie client profile
 .NET Framework Client Profile jest podzbiorem pełny program .NET Framework. Można kierować platformy .NET Framework Client Profile, należy użyć tylko funkcje klienta w programie .NET Framework, jeśli chcesz udostępnić najszybszy środowisko wdrażania dla rozwiązania pakietu Office. Aby uzyskać więcej informacji, zobacz [profil klienta .NET Framework](/dotnet/framework/deployment/client-profile).

 Podczas tworzenia projektu Office współpracującego [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] domyślny. Jeśli chcesz programować dla pełnego [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], należy ustawić tę opcję, po utworzeniu projektu. Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Tworzenie rozwiązań dla 64-bitowej wersji pakietu Microsoft Office
 Microsoft Office jest dostępny w wersji 64-bitowe i 32-bitowych. Aby utworzyć rozwiązania pakietu Office, które mogą być uruchamiane w każdej wersji, ustawienie obiektu docelowego platformy dla projektu musi być równa **dowolny Procesor**. Jest to wartość domyślna dla projektów pakietu Office. Aby uzyskać więcej informacji, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).

 Istnieją osobne 64-bitowe i 32-bitowe wersje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używanych przez 64-bitowe i 32-bitowe wersje pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-office-solutions"></a>Zestawy w rozwiązaniach pakietu Office
 Podczas tworzenia projektu pakietu Office przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, kod, który można napisać po pewnym czasie jest skompilowany w zestawie. Zestaw jest wdrożony na serwerze współużytkowanym lub do katalogu na komputerze klienckim.

 Zestawy w rozwiązaniach pakietu Office są ładowane przez aplikację pakietu Office. Po załadowaniu zestawu kodu w zestawie mogą odpowiadać na zdarzenia, które są wywoływane na przykład w aplikacji, gdy użytkownik kliknie element menu. Kod w zestawie, można również wywołać modelu obiektów automatyzacji i rozszerzania aplikacji i może używać dowolnej klasy w [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Aby uzyskać więcej informacji, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md) i [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

 Rozwiązania dla pakietu Office Użyj manifesty aplikacji i manifestów wdrożenia, aby zidentyfikować zestawu. Manifesty zawierać informacje o nazwę zestawu, wersji i lokalizacji, aplikacji można znaleźć, połączyć i uruchomić poprawny zestaw. Aby uzyskać więcej informacji, zobacz [stosowania i wdrażania manifestów w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Projektów na poziomie dokumentów zawierają dokumentu poza zestaw. Dokument działa jako fronton aplikacji i to, gdzie odbywa się wszystkich interakcji z użytkownikiem. Każdy dokument może mieć tylko jeden zestaw głównego projektu skojarzonego z nim; Jednak wiele dokumentów może wskazywać tego samego zestawu.

 Zestawy w projektach na poziomie dokumentu nie są osadzone w dokumencie. Zamiast tego są przechowywane w innym miejscu i są identyfikowane za pomocą dokumentu, manifest aplikacji.

## <a name="security-considerations-for-assemblies"></a>Zagadnienia dotyczące zabezpieczeń zestawów
 Dla rozwiązań pakietu Office do uruchomienia na komputerze zestawy używane przez to rozwiązanie musi być zaufane do uruchomienia. Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [rozwiązań Secure Office](../vsto/securing-office-solutions.md).

 Domyślnie zestawu rozwiązania i przywoływanych zestawach, które znajdują się w folderze danych wyjściowych projektu są zaufane do uruchomienia na komputerze deweloperskim, podczas kompilowania projektu. Aby uzyskać więcej informacji, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).

 Ze względów bezpieczeństwa jest najlepiej tworzyć projekty na komputerze lokalnym, zamiast tworzenia w lokalizacji udostępnionej. Aby uzyskać więcej informacji, zobacz [programowanie zespołowe rozwiązań pakietu Office](../vsto/collaborative-development-of-office-solutions.md).

## <a name="referenced-assemblies"></a>przywoływanych zestawach
 Zestaw może odwoływać się do innych zestawów, które są wymienione w odwołaniach projektu. Jednak jeden zestaw projektów dokumentów nie może odwoływać się innego zestawu w projekcie na poziomie dokumentu.

## <a name="see-also"></a>Zobacz także
- [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Projekty pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md)
- [Uruchamianie rozwiązań w różnych wersjach pakietu Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [Instrukcje: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Instrukcje: Ustawianie informacji o konfiguracji dla rozwiązań pakietu Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [Użyj funkcji pakietu Office w Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
- [Typowe zadania w programowaniu pakietu Office](../vsto/common-tasks-in-office-programming.md)
- [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
