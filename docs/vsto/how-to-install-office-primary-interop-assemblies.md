---
title: 'Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4b6f701e3962a25e7239c829d409a3ad69a1833a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419596"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office
  Po zainstalowaniu pakietu Office, należy zainstalować podstawowe zestawy międzyoperacyjne Microsoft Office (PIA).

## <a name="to-install-the-pias-when-you-install-office"></a>Aby zainstalować PIA, podczas instalowania pakietu Office

1. Upewnij się, że została zainstalowana wersja programu .NET Framework, która nie jest starsza niż 2.0.

2. Zainstaluj program Microsoft Office i upewnij się, że **dodatkiem .NET Programmability Support** funkcji wybrano dla aplikacji, aby rozszerzyć (Ta funkcja jest dostępna w domyślnej instalacji).

    > [!WARNING]
    > Domyślnie PIA firmy są osadzone w rozwiązaniu podczas kompilacji, dzięki czemu nie trzeba rozpowszechniać zestawów PIA dla użytkowników jako warunek wstępny do korzystania z dodatku narzędzi VSTO lub dostosowywania.

## <a name="see-also"></a>Zobacz także
- [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Instrukcje: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Instrukcje: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Instrukcje: Zainstalować Visual Studio Tools for Office runtime do dystrybucji](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
