---
title: Obsługa kontroli źródła | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704728"
---
# <a name="supporting-source-control"></a>Obsługa kontroli kodu źródłowego
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje wyewidencjonowywanie plików, ewidencjonowanie i inne operacje kontroli źródła dla projektu lub edytora. Jako klient kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] został zaprojektowany w celu współdziałania z pakietem kontroli źródła, np [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ., który oferuje funkcje archiwizowania, obsługi wersji i kontroli dla dynamicznie zdefiniowanego zestawu plików.

## <a name="in-this-section"></a>W tej sekcji
- [Model pakietów kontroli kodu źródłowego](../../extensibility/internals/model-for-source-control-packages.md)

 Opisuje interfejsy, które typ projektu musi zaimplementować, aby umożliwić obsługę kontroli źródła.

- [Decyzje dotyczące projektu](../../extensibility/internals/source-control-design-decisions.md)

 Zawiera pytania, których odpowiedzi zmieniają sposób implementacji typu projektu.

- [Szczegóły konfiguracji](../../extensibility/internals/source-control-configuration-details.md)

 Opisuje, jak pomocnicza kontrola źródła zmienia implementację typu projektu.

- [Dodatkowe wskazówki dotyczące projektów i edytorów](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Omawia najlepsze rozwiązania dotyczące typów projektów i edytorów.

- [Szczegóły środowiska uruchomieniowego](../../extensibility/internals/source-control-runtime-details.md)

 Opisuje sposób rejestrowania projektu, gdy użytkownik dodaje go do systemu kontroli źródła.

## <a name="reference"></a>Dokumentacja
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Wskazuje środowisko lub pakiet kontroli źródła, w którym plik zostanie zmieniony w pamięci lub zapisany.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> Zezwala na projekty i hierarchie do zarejestrowania się w kontroli źródła i uzyskiwania informacji o stanie kontroli źródła.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Zaimplementowane w systemie projektu w celu zapewnienia kontroli źródła dla plików projektu i elementów projektu.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Używane przez projekty do wykonywania zapytań dotyczących środowiska w celu dodania, usunięcia lub zmiany nazwy pliku lub katalogu w rozwiązaniu.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> Powiadamia klientów o zmianach wprowadzonych w plikach projektu lub katalogach.

## <a name="related-sections"></a>Sekcje pokrewne
- [Typy projektów](../../extensibility/internals/project-types.md)

 Zawiera omówienie projektów jako podstawowych bloków konstrukcyjnych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). Linki są dostarczane do dodatkowych tematów, które wyjaśniają, jak projekty kontrolują Kompilowanie i kompilowanie kodu.
