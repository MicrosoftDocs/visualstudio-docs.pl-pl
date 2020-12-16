---
title: Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego
description: Dowiedz się, jak przeprowadzić migrację rozwiązań pakietu Office do .NET Framework 4 lub nowszego, aby projekt nadal działał.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: 5b7780b6fccef86dfe4a671c0c468e5899adc36c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528458"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego
  Jeśli docelowa platforma projektu pakietu Office zostanie zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub w późniejszym czasie ze starszej wersji .NET Framework, może być konieczne wykonanie pewnych dodatkowych czynności, aby kontynuować uruchamianie rozwiązania na komputerach deweloperskich i użytkowników końcowych. Aby uzyskać więcej informacji, zobacz [wymagane zmiany w celu uruchomienia projektów pakietu Office migrowanych do .NET Framework 4 lub .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Ponadto projekt nie może być już kompilowany. Niektóre funkcje projektów pakietu Office mają różne modele programowania dla różnych wersji .NET Framework. Gdy docelowa platforma projektu pakietu Office zostanie zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub w późniejszym czasie ze starszej wersji .NET Framework, należy wprowadzić następujące zmiany kodu w projekcie:

- [Aktualizowanie projektów programów Excel i Word, które są migrowane do .NET Framework 4 lub .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aktualizowanie dostosowań wstążki w projektach pakietu Office migrowanych do .NET Framework 4 lub .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Aktualizowanie regionów formularzy w projektach programu Outlook migrowanych do .NET Framework 4 lub .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Docelowa struktura projektu pakietu Office zmienia się po uaktualnieniu tego projektu ze starszej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [uaktualnianie i migrowanie rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Aby uzyskać więcej informacji na temat tego, dlaczego niektóre funkcje w projektach pakietu Office mają inny model programowania, gdy jest on przeznaczony dla programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego, zobacz [zmiany w projekcie projektów pakietu Office przeznaczonych dla .NET Framework 4 lub .NET Framework 4,5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) i [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Zobacz też
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Instrukcje: docelowa wersja .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Dodatkowa obsługa błędów w rozwiązaniach pakietu Office](../vsto/additional-support-for-errors-in-office-solutions.md)
