---
title: 'Instrukcje: Instalowanie pakietu redystrybucyjnego środowiska uruchomieniowego Office Visual Studio Tools'
description: Dowiedz się, jak zainstalować pakiet redystrybucyjny programu Microsoft Visual Studio 2010 Tools for Office Runtime.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8fce7cc0fdbba49e0e247a6a65336105e149b6d
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846535"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Instrukcje: Instalowanie pakietu redystrybucyjnego środowiska uruchomieniowego Office Visual Studio Tools
  Program Visual Studio 2010 Tools for Office Runtime musi być zainstalowany na każdym komputerze, na którym są uruchomione rozwiązania utworzone przy użyciu narzędzi deweloperskich Microsoft Office w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Środowisko uruchomieniowe jest instalowane automatycznie podczas instalacji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programu, a Microsoft Office. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools scenariuszy instalacji pakietu Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Może być konieczne wykonanie ręcznej instrukcji instalacji poniżej w następujących sytuacjach:

- Należy zainstalować [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] na serwerze programu. Na przykład, chcesz użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy do zarządzania rozwiązaniami na poziomie dokumentu na serwerze.

- Musisz zainstalować środowisko uruchomieniowe na komputerze, na którym już zainstalowano wszystkie inne wymagania wstępne dotyczące rozwiązań pakietu Office.

    > [!NOTE]
    > Musisz być administratorem na komputerze deweloperskim, aby zainstalować .NET Framework i [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Aby zainstalować Visual Studio Tools dla środowiska uruchomieniowego pakietu Office

1. Zainstaluj program [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy.

    - Aby pobrać [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] program, zobacz [Microsoft .NET Framework 4 (Instalator sieci Web)](https://www.microsoft.com/download/details.aspx?id=17851).

    - Aby pobrać [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] program, zobacz [Microsoft .NET Framework 4 Client Profile (Instalator sieci Web)](https://www.microsoft.com/download/details.aspx?id=17113).

    - Aby pobrać [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] program, zobacz [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Uruchom *vstor_redist.exe* , aby zainstalować program [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

     Pliki instalacyjne można pobrać z programu [Visual Studio 2010 Tools for Office Runtime](https://www.microsoft.com/download/details.aspx?id=56961). Wymagania wstępne dotyczące programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] są zgodne z wymaganiami wstępnymi .NET Framework.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Obejmuje pakiety językowe. Jeśli instalacja systemu Windows jest ustawiona na język inny niż angielski, można wyświetlić komunikaty środowiska uruchomieniowego w tym samym języku, który jest używany dla systemu Windows. Podobnie, jeśli użytkownicy końcowi zainstalują [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i uruchamiają rozwiązania w instalacjach systemu Windows, które są ustawione na język inny niż angielski, komunikaty środowiska uruchomieniowego będą wyświetlane w tym samym języku co system Windows. W niektórych przypadkach mogą być potrzebne dodatkowe pakiety językowe. Na przykład mogą być potrzebne dodatkowe pakiety językowe, jeśli kopia systemu Windows korzysta z więcej niż jednego ustawienia języka lub przełączasz się do innego języka po zainstalowaniu programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Pakiety językowe można znaleźć w witrynie [Microsoft Visual Studio 2010 Tools dla pakietu językowego systemu Microsoft Office System (wersja 4,0 Runtime)](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie &#40;Programowanie Office w programie Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Instrukcje: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
