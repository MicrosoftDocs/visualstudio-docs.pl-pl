---
title: Projekt różnych plików | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c46126507ef9bb293bd0fa6771f53343ad6206f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726675"
---
# <a name="miscellaneous-files-project"></a>Projekt Różne pliki
Gdy użytkownik otwiera elementy projektu, IDE przypisuje do projektu różne pliki wszystkie elementy, które nie są członkami żadnych projektów w rozwiązaniu.

 Projekty odgrywają znaczącą rolę w ustaleniu, który Edytor jest używany, gdy użytkownik otwiera element projektu. Projekt można zaprojektować, aby otworzyć niektóre pliki przy użyciu edytora specyficznego dla projektu lub standardowego edytora.

 Edytor specyficzny dla projektu zwykle wymaga, aby użytkownik miał specjalną wiedzę lub użyć specjalnych interfejsów z projektu. Aby uzyskać więcej informacji, zobacz [jak: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md).

 Standardowy Edytor może otworzyć dowolny plik o określonym rozszerzeniu w dowolnym projekcie. Użytkownik może dostosować niektóre standardowe edytory, takie jak edytor tekstu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], dla projektów, ale nadal zachowują swój publiczny znak. Standardowe edytory są tworzone za pomocą metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

 Jeśli żaden projekt w rozwiązaniu nie odpowiada, że może otworzyć element projektu, IDE udostępnia specjalny projekt o nazwie różne pliki projektu, który otwiera dowolny plik.

 Ten specjalny projekt umożliwia otwarcie pliku poza kontekstem projektu. Podczas przetwarzania metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> projekt różne pliki zawsze reaguje na bardzo niski priorytet. W związku z tym projekt różne pliki zawsze uzyskuje wszystkie projekty o wyższym priorytecie, które mogą otwierać pliki.

 Projekt różne pliki nie wymaga, aby użytkownik jawnie go utworzył przy użyciu okna dialogowego **Nowy projekt** . Ponadto projekt różne pliki nie zarządza na stałe listą członków projektu. Używa funkcji opcjonalnej do rejestrowania listy ostatnio używanych plików dla każdego użytkownika.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)
- [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)
- [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)