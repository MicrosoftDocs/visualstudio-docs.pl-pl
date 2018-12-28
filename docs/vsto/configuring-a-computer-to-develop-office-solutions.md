---
title: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: a0e6f44b923bf515977c07bbfec69b9c8e58593c
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2018
ms.locfileid: "53441421"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Konfigurowanie komputera do opracowywania rozwiązań pakietu Office

Do tworzenia dodatków narzędzi VSTO dla programów i dostosowania pakietu Microsoft Office, należy zainstalować obsługiwaną wersję programu Visual Studio, .NET Framework i Microsoft Office.

|Oprogramowanie|Obsługiwane wersje|
|--------------|------------------------|
|Visual Studio 2017| W każdej wersji za pomocą **rozwoju pakietu Office/SharePoint** obciążenia.|
|.NET Framework|-.NET Framework 4 lub nowszej.|
|Microsoft Office|<ul><li>Dowolna wersja pakietu Office, w tym Office Professional Plus dla Office 365.</li><li>Dowolny z następujących aplikacji:<br /><br /> <ul><li>Excel</li><li>InfoPath (pakiet Office 2013 i Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Projekt</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) musi być zainstalowany jako część pakietu Office. **Ważne:** Szybka instalacja wersji aplikacji pakietu Office 2010 nie są obsługiwane.|

Aby uzyskać szczegółowe kroki instalacji, zobacz [jak: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Jeśli szablony projektu nie pojawiają się lub nie działają w programie Visual Studio

Zainstaluj obsługiwaną wersję programu Visual Studio, .NET Framework i Microsoft Office, ale szablony projektów pakietu Office albo nie są wyświetlane w programie Visual Studio **nowy projekt** okno dialogowe lub komunikat o błędzie podczas próby użycia, Sprawdź następujące informacje:

- Upewnij się, że masz zainstalowany na tym komputerze narzędzia Microsoft Office developer tools.

     Narzędzia Office developer tools są opcjonalnym składnikiem programu Visual Studio, ale są instalowane automatycznie wraz z Visual Studio. Jeśli dostosowujesz instalację programu Visual Studio przez określenie, które funkcje do zainstalowania, upewnij się, że wybierasz **Microsoft Office Developer Tools** podczas instalacji, aby zainstalować narzędzia.

     Aby upewnić się, że te narzędzia są zainstalowane, uruchom Instalatora programu Visual Studio i wybierz polecenie **Modyfikuj** przycisku. Wybierz **Microsoft Office Developer Tools** pole wyboru, a następnie wybierz **aktualizacji** przycisku.

- Upewnij się, że nie używasz wersji pakietu Office, który został dostarczony przez kliknięcie do uruchomienia. Zobacz [jak: Sprawdź, czy program Outlook jest aplikacją kliknij polecenie do uruchomienia na komputerze](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Upewnij się, że używasz tylko jedna wersja pakietu Microsoft Office.

Jeśli nadal występują problemy, zobacz [dodatkowa obsługa błędów w rozwiązaniach pakietu Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Zobacz także

[Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Instrukcje: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Instrukcje: Zainstalować Visual Studio Tools for Office runtime do dystrybucji](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Typ funkcji według aplikacji pakietu Office i projekt](../vsto/features-available-by-office-application-and-project-type.md)
