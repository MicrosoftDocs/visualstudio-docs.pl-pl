---
title: Wskazówki dotyczące kontroli źródła dla projektów i edytorów
description: Zapoznaj się z wytycznymi, które są zgodne z projektami i edytorami, aby umożliwić obsługę kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2509f2f6f9da91c3df60d6b041d5ebb6bdd367b6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079010"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Dodatkowe wskazówki dotyczące kontroli źródła dla projektów i edytorów
Istnieje kilka wytycznych, które są zgodne z projektami i edytorami w celu zapewnienia obsługi kontroli źródła.

## <a name="guidelines"></a>Wytyczne
 Aby umożliwić obsługę kontroli źródła, projekt lub Edytor powinien również wykonać następujące czynności:

|Warstwowy|Project|Edytor|Szczegóły|
|----------|-------------|------------|-------------|
|Prywatne kopie plików|X||Środowisko obsługuje prywatne kopie plików. Oznacza to, że każda osoba zarejestrowana w projekcie ma swoją prywatną kopię plików w tym projekcie.|
|Trwałość ANSI/Unicode|X|X|Jeśli zapiszesz kod trwałości, Utrwalaj pliki w postaci ANSI, ponieważ większość programów kontroli źródła nie obsługuje obecnie standardu Unicode.|
|Wyliczanie plików|X||Projekt musi zawierać określoną listę wszystkich plików w nim i musi być w stanie wyliczyć listę plików przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Projekt powinien również ujawniać nazwy elementów za pomocą jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implementacji i obsługiwać wyszukiwanie nazw (w tym pliki specjalne) przez jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementację.|
|Format tekstu|X|X|Jeśli to możliwe, pliki powinny być w formacie tekstowym, aby obsługiwać scalanie różnych wersji. Pliki, które nie są w formacie tekstowym, nie mogą być scalane z innymi wersjami plików później. Preferowanym formatem tekstu jest XML.|
|Oparta na odwołaniach|X||Projekty oparte na odwołaniach są łatwo obsługiwane w kontroli źródła. Jednak projekty oparte na katalogach są również obsługiwane przez kontrolę źródła, tak długo, jak projekt może generować listę swoich plików na żądanie, niezależnie od tego, czy te pliki istnieją na dysku. Podczas otwierania projektu z kontroli źródła plik projektu jest najpierw umieszczany przed dowolnym z jego plików.|
|Utrwalanie obiektów i właściwości w kolejności przewidywalnej|X|X|Utrwalaj pliki w przewidywalnej kolejności, takiej jak kolejność alfabetyczna, aby ułatwić scalanie.|
|Załaduj ponownie|X|X|Gdy plik jest zmieniany na dysku, Edytor musi mieć możliwość jego ponownego załadowania. Gdy użytkownik uczestniczy w kontroli źródła, środowisko będzie ponownie ładować dane przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementacji. Najbardziej trudnym przypadkiem ponownego załadowania jest to, że wyewidencjonowanie odbywa się po wywołaniu IVsQueryEditQuerySave:: <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przetwarza informacje. Jednak kod ponownego załadowania musi być w stanie działać w tej sytuacji.<br /><br /> Środowisko automatycznie ponownie ładuje pliki projektu. Jednak projekt musi implementować, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> Jeśli ma zagnieżdżone hierarchie w celu obsługi ponownego ładowania zagnieżdżonych plików projektu.|

## <a name="see-also"></a>Zobacz też
- [Obsługa kontroli źródła](../../extensibility/internals/supporting-source-control.md)
