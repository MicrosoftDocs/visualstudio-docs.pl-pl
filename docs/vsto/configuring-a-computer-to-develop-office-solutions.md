---
title: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office
description: Dowiedz się, jak zainstalować obsługiwaną wersję programu Visual Studio, .NET Framework i Microsoft Office, aby można było utworzyć Dodatki i dostosowania narzędzia VSTO dla Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee8f840aa81d3decfdb96dd2658b758704443347
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910573"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Konfigurowanie komputera do opracowywania rozwiązań pakietu Office

Aby utworzyć Dodatki i dostosowania narzędzia VSTO dla Microsoft Office, zainstaluj obsługiwaną wersję programu Visual Studio, .NET Framework i Microsoft Office.

|Oprogramowanie|Obsługiwane wersje|
|--------------|------------------------|
|Visual Studio 2017| Dowolna wersja z obciążeniem **programistycznym dla pakietu Office/programu SharePoint** .|
|.NET Framework|— .NET Framework 4 lub nowszy.|
|Microsoft Office|<ul><li>Wszystkie wersje pakietu Office, w tym Microsoft 365 aplikacje dla przedsiębiorstw.</li><li>Dowolne z następujących aplikacji autonomicznych:<br /><br /> <ul><li>Excel</li><li>InfoPath (tylko pakiet Office 2013 i pakiet Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) musi być zainstalowany w ramach pakietu Office. **Ważne:** Wersje programów pakietu Office 2010 nie są obsługiwane przez klikanie do uruchomienia.|

Aby zapoznać się ze szczegółowymi krokami instalacji, zobacz [jak: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Jeśli szablony projektu nie są wyświetlane lub nie działają w programie Visual Studio

W przypadku zainstalowania obsługiwanej wersji programu Visual Studio, .NET Framework i Microsoft Office, ale szablony programu Office Project nie są wyświetlane w oknie dialogowym **Nowy projekt** programu Visual Studio lub wystąpi błąd podczas próby użycia jednego z nich, należy sprawdzić następujące kwestie:

- Upewnij się, że na komputerze zainstalowano narzędzia deweloperskie Microsoft Office.

     Narzędzia Office Developer Tools są opcjonalnym składnikiem programu Visual Studio, ale są instalowane automatycznie wraz z programem Visual Studio. W przypadku dostosowania instalacji programu Visual Studio przez określenie, które funkcje zainstalować, należy wybrać **Microsoft Office narzędzia deweloperskie** podczas instalacji, aby zainstalować narzędzia.

     Aby upewnić się, że te narzędzia są zainstalowane, uruchom program instalacyjny programu Visual Studio, a następnie wybierz przycisk **Modyfikuj** . Zaznacz pole wyboru **Microsoft Office narzędzia deweloperskie** , a następnie kliknij przycisk **Aktualizuj** .

- Upewnij się, że nie korzystasz z wersji pakietu Office, która została dostarczona przez kliknięcie przycisku do uruchomienia. Zobacz [jak to zrobić: Sprawdź, czy program Outlook jest aplikacją typu "kliknij i uruchom" na komputerze](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Upewnij się, że masz uruchomioną tylko jedną wersję Microsoft Office.

Jeśli nadal występują problemy, zobacz [dodatkowe wsparcie dla błędów w rozwiązaniach pakietu Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie &#40;Programowanie Office w programie Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Instrukcje: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Instrukcje: Instalowanie pakietu redystrybucyjnego środowiska uruchomieniowego Office Visual Studio Tools](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Funkcje dostępne według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md)