---
title: Projekt różnych plików | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707098"
---
# <a name="miscellaneous-files-project"></a>Projekt Różne pliki
Gdy użytkownik otwiera elementy projektu, IDE przypisuje do różnych plików projektu żadnych elementów, które nie są członkami żadnych projektów w rozwiązaniu.

 Projekty odgrywają znaczącą rolę w określaniu, który edytor jest używany, gdy użytkownik otwiera element projektu. Projekt może być zaprojektowany do otwierania niektórych plików przy użyciu edytora specyficznego dla projektu lub standardowego edytora.

 Edytor specyficzny dla projektu zazwyczaj wymaga, aby użytkownik miał specjalną wiedzę lub używał specjalnych interfejsów z projektu. Aby uzyskać więcej informacji, zobacz [Jak: Otwórz edytory specyficzne dla projektu](../../extensibility/how-to-open-project-specific-editors.md).

 Standardowy edytor może otworzyć dowolny plik określonego rozszerzenia w dowolnym projekcie. Użytkownik może dostosować niektóre standardowe edytory, takie jak edytor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tekstu, dla projektów, ale nadal zachowują swój publiczny charakter. Standardowe edytory są <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> tworzone przy użyciu metody.

 Jeśli żaden projekt w rozwiązaniu nie odpowiada, że można otworzyć element projektu, IDE udostępnia specjalny projekt o nazwie różne pliki projektu, który otwiera dowolny plik.

 Ten specjalny projekt przewiduje otwarcie pliku poza kontekstem projektu. Podczas przetwarzania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metody, różne pliki projektu zawsze odpowiada z bardzo niskim priorytetem. W związku z tym różne pliki projektu zawsze daje do każdego projektu o wyższym priorytecie, który można otworzyć pliki.

 Projekt Różne pliki nie wymaga od użytkownika jawnego tworzenia go za pomocą okna dialogowego **Nowy projekt.** Ponadto projekt Różne pliki nie zarządza trwale listą członków projektu. Używa opcjonalnej funkcji do rejestrowania listy ostatnio używanych plików dla każdego użytkownika.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)
- [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
