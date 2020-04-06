---
title: Obsługa kontroli źródła | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704728"
---
# <a name="supporting-source-control"></a>Obsługa kontroli kodu źródłowego
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obsługuje wyewidencjonowania plików, zaewidencjonowania i inne operacje kontroli źródła dla projektu lub edytora. Jako klient kontroli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] źródła, jest przeznaczony do interakcji z [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]pakietem kontroli źródła, takich jak , który zapewnia archiwizacji, przechowywania wersji i urządzeń kontroli dla dynamicznie zdefiniowanego zestawu plików.

## <a name="in-this-section"></a>W tej sekcji
- [Model pakietów kontroli kodu źródłowego](../../extensibility/internals/model-for-source-control-packages.md)

 W tym artykule opisano interfejsy typ projektu musi zaimplementować do obsługi kontroli źródła.

- [Decyzje dotyczące projektu](../../extensibility/internals/source-control-design-decisions.md)

 Zawiera pytania, których odpowiedzi zmieniają sposób implementowania typu projektu.

- [Szczegóły konfiguracji](../../extensibility/internals/source-control-configuration-details.md)

 W tym artykule opisano, jak obsługa kontroli źródła zmienia implementację typu projektu.

- [Dodatkowe wskazówki dotyczące projektów i edytorów](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 W tym artykule omówiono najlepsze rozwiązania dotyczące typów projektów i edytorów.

- [Szczegóły środowiska uruchomieniowego](../../extensibility/internals/source-control-runtime-details.md)

 W tym artykule opisano sposób rejestrowania projektu, gdy użytkownik dodaje go do systemu kontroli źródła.

## <a name="reference"></a>Tematy pomocy
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>Wskazuje pakiet kontroli środowiska lub źródła, że plik ma zostać zmieniony w pamięci lub zapisany.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>Umożliwia projektom i hierarchiom rejestrowanie się za pomocą kontroli źródła i uzyskiwanie informacji o stanie kontroli źródła.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>Zaimplementowano w systemie projektu w celu zapewnienia kontroli źródła dla plików projektu i elementów projektu.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>Używane przez projekty do wykonywania zapytań w środowisku w celu uzyskania uprawnień do dodawania, usuwania lub zmieniania nazwy pliku lub katalogu w rozwiązaniu.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>Powiadamia klientów o zmianach wprowadzonych w plikach lub katalogach projektu.

## <a name="related-sections"></a>Sekcje pokrewne
- [Project Types (Typy projektów)](../../extensibility/internals/project-types.md)

 Zawiera omówienie projektów jako podstawowych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementów składowych zintegrowanego środowiska programistycznego (IDE). Łącza są dostarczane do dodatkowych tematów, które wyjaśniają, jak projekty kontroli tworzenia i kompilacji kodu.
