---
title: Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 729fafd1f6dfdf889293c9686f455be8de5a81fc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970379"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej
  Jeśli platforma docelowa projektu pakietu Office jest zmieniana na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego z wcześniejszej wersji programu .NET Framework, kilka dodatkowych kroków, może być wymagane do uruchamiania rozwiązania na komputerach rozwoju i użytkowników końcowych w dalszym ciągu. Aby uzyskać więcej informacji, zobacz [wymagane zmiany w celu uruchamiania projektów pakietu Office, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Ponadto projekt nie jest już może skompilować. Niektóre funkcje w projektach pakietu Office mają różne modele programowania dla różnych wersji programu .NET Framework. Po zmianie platformy docelowej projektu pakietu Office do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej z wcześniejszej wersji programu .NET Framework, należy następujące zmiany kodu do projektu:

- [Zaktualizuj projekty programu Excel i Word, są migrowane do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aktualizowanie dostosowań Wstążki w projektach pakietu Office, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5)

- [Aktualizowanie regionów formularzy w projektach programu Outlook, są migrowane do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Docelowa platforma projektu pakietu Office zmienia się po uaktualnieniu tego projektu z wcześniejszej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [uaktualnianie i migracja rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Aby uzyskać więcej informacji na temat przyczyn niektóre funkcje w projektach pakietu Office ma inny model programowania, gdy miejscem docelowym [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, adresem [zmiany w projektach przeznaczonych dla platformy .NET Framework 4 lub .NET Framework 4.5projektachdlapakietuOffice](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) i [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Zobacz także
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Instrukcje: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)
- [Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Dodatkowa obsługa błędów w rozwiązaniach pakietu Office](../vsto/additional-support-for-errors-in-office-solutions.md)
