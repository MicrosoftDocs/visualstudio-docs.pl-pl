---
title: Projekt różnych plików | Microsoft Docs
description: Dowiedz się więcej o dwóch typach edytorów, których można użyć do otwierania plików w projekcie programu Visual Studio i roli projektu w celu określenia edytora, który ma być używany.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b79eaaeaf94954e2d3dc1bd855b56bee5b8bdae4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063282"
---
# <a name="miscellaneous-files-project"></a>Projekt Różne pliki
Gdy użytkownik otwiera elementy projektu, IDE przypisuje do projektu różne pliki wszystkie elementy, które nie są członkami żadnych projektów w rozwiązaniu.

 Projekty odgrywają znaczącą rolę w ustaleniu, który Edytor jest używany, gdy użytkownik otwiera element projektu. Projekt można zaprojektować, aby otworzyć niektóre pliki przy użyciu edytora specyficznego dla projektu lub standardowego edytora.

 Edytor specyficzny dla projektu zwykle wymaga, aby użytkownik miał specjalną wiedzę lub użyć specjalnych interfejsów z projektu. Aby uzyskać więcej informacji, zobacz [jak: otwieranie edytorów Project-Specific](../../extensibility/how-to-open-project-specific-editors.md).

 Standardowy Edytor może otworzyć dowolny plik o określonym rozszerzeniu w dowolnym projekcie. Użytkownik może dostosować niektóre standardowe edytory, takie jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Edytor tekstu, dla projektów, ale zachowują swój publiczny znak. Standardowe edytory są tworzone przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody.

 Jeśli żaden projekt w rozwiązaniu nie odpowiada, że może otworzyć element projektu, IDE udostępnia specjalny projekt o nazwie różne pliki projektu, który otwiera dowolny plik.

 Ten specjalny projekt umożliwia otwarcie pliku poza kontekstem projektu. Podczas przetwarzania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metody projekt różne pliki zawsze reaguje na bardzo niski priorytet. W związku z tym projekt różne pliki zawsze uzyskuje wszystkie projekty o wyższym priorytecie, które mogą otwierać pliki.

 Projekt różne pliki nie wymaga, aby użytkownik jawnie go utworzył przy użyciu okna dialogowego **Nowy projekt** . Ponadto projekt różne pliki nie zarządza na stałe listą członków projektu. Używa funkcji opcjonalnej do rejestrowania listy ostatnio używanych plików dla każdego użytkownika.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)
- [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
