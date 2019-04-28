---
title: 'Instrukcje: Zainstalować Visual Studio Tools for Office runtime do dystrybucji'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 41b6ec5c91fe9dc16a07703358ee0bb951efb490
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412587"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Instrukcje: Zainstalować Visual Studio Tools for Office runtime do dystrybucji
  Visual Studio 2010 Tools dla pakietu Office runtime musi być zainstalowane na każdym komputerze, uruchomionym rozwiązania, które są tworzone za pomocą Microsoft Office developer tools w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Środowisko uruchomieniowe jest instalowana automatycznie podczas instalowania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]i Microsoft Office. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

 Konieczne może być następnie wykonaj poniższe instrukcje instalacji ręcznej w następujących sytuacjach:

- Musisz zainstalować [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] na serwerze. Na przykład chcesz użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy na poziomie dokumentu rozwiązania na serwerze zarządzania.

- Musisz zainstalować środowisko uruchomieniowe na komputerze, który ma już wszystkie inne wymagania wstępne dla rozwiązań pakietu Office, zainstalowane.

    > [!NOTE]
    > Musi być administratorem na komputerze deweloperskim, aby zainstalować program .NET Framework i [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Aby zainstalować Visual Studio Tools for Office runtime

1. Zainstaluj [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej.

    - Aby pobrać [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], zobacz [Microsoft .NET Framework 4 (Instalator internetowy)](http://go.microsoft.com/fwlink/?LinkId=178957).

    - Aby pobrać [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], zobacz [profil klienta programu Microsoft .NET Framework 4 (Instalator internetowy)](http://go.microsoft.com/fwlink/?LinkId=178958).

    - Aby pobrać [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], zobacz [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).

2. Uruchom *vstor_redist.exe* zainstalował [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

     Możesz pobrać te pliki Instalatora z [Visual Studio 2010 Tools dla pakietu Office runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Wymagania wstępne dotyczące [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dopasowania wymagania wstępne dotyczące programu .NET Framework.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zawiera pakietów językowych. W przypadku instalacji systemu Windows jest ustawiony na język inny niż angielski, można wyświetlić komunikaty czasu wykonywania, w tym samym języku, którego używasz dla Windows. Podobnie jeśli użytkownicy końcowi instalują [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , a następnie uruchom swoje rozwiązania w przypadku instalacji systemu Windows, które są ustawione na język inny niż angielski, środowisko uruchomieniowe komunikaty pojawią się w języku Windows. W niektórych przypadkach może być konieczne dodatkowe pakiety językowe. Na przykład może być konieczne dodatkowe pakiety językowe, jeśli Twoja kopia Windows używa więcej niż jedno ustawienie języka lub przełączanie na inny język, po zainstalowaniu już [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Można znaleźć pakietów językowych w [programu Microsoft Visual Studio 2010 Tools dla pakietu językowego programu Microsoft Office system (środowisko uruchomieniowe w wersji 4.0)](http://go.microsoft.com/fwlink/?LinkId=140386).

## <a name="see-also"></a>Zobacz także
- [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Instrukcje: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
