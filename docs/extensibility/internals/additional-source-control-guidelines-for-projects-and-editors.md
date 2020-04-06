---
title: Dodatkowe wytyczne dotyczące kontroli źródeł dla projektów i redaktorów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181f6c10ff7ce95cd3a37151f117353d1bb47d41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710109"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Dodatkowe wytyczne dotyczące kontroli źródeł dla projektów i edytorów
Istnieje wiele wytycznych, które projekty i edytory powinny stosować się do w celu obsługi kontroli źródła.

## <a name="guidelines"></a>Wytyczne
 Projekt lub edytor należy również wykonać następujące czynności w celu obsługi kontroli źródła:

|Obszar|Projekt|Edytor|Szczegóły|
|----------|-------------|------------|-------------|
|Prywatne kopie plików|X||Środowisko obsługuje prywatne kopie plików. Oznacza to, że każda osoba zarejestrowana w projekcie ma własną kopię prywatną plików w tym projekcie.|
|Trwałość ANSI/Unicode|X|X|Jeśli piszesz kod trwałości, utrwalić pliki w formularzu ANSI, ponieważ większość programów kontroli źródła nie obsługuje obecnie Unicode.|
|Wyliczaj pliki|X||Projekt musi zawierać określoną listę wszystkich plików w nim i musi być w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> stanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> wyliczyć listę plików przy użyciu lub (VSH_PROPID_First_Child/Next_Sibling). Projekt należy również uwidaczniać nazwy elementów za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementacji i wyszukiwania nazw pomocy technicznej (w tym plików specjalnych) za pośrednictwem jego implementacji.|
|Format tekstu|X|X|Jeśli to możliwe, pliki powinny być w formacie tekstowym do obsługi scalania różnych wersji. Pliki, które nie są w formacie tekstowym, nie mogą być później scalane z innymi wersjami pliku. Preferowanym formatem tekstu jest XML.|
|Oparte na referencjach|X||Projekty oparte na odniesieniach są łatwo obsługiwane w kontroli źródła. Jednak projekty oparte na katalogu są również obsługiwane przez kontrolę źródła, o ile projekt może utworzyć listę swoich plików na żądanie, niezależnie od tego, czy te pliki istnieją na dysku. Podczas otwierania projektu z kontroli źródła, plik projektu jest przenoszony najpierw przed dowolnym z jego plików.|
|Utrwalanie obiektów i właściwości w przewidywalnej kolejności|X|X|Utrwalić pliki w przewidywalnej kolejności, takich jak kolejność alfabetyczna, aby ułatwić scalanie.|
|Załaduj ponownie|X|X|Gdy plik zmieni się na dysku, edytor musi mieć możliwość ponownego załadowania go. Gdy uczestniczysz w kontroli źródła, środowisko będzie ponownie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> załadowywania danych dla Ciebie, wywołując implementacji. Najtrudniejszy przypadek przeładowania jest, gdy wyewidencjonowanie występuje, gdy zostały<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wywołane IVsQueryEditQuerySave:: i przetwarzania informacji. Jednak kod ponownego ładowania musi być w stanie uruchomić w tej sytuacji.<br /><br /> Środowisko automatycznie ponownie ładuje pliki projektu. Jednak projekt musi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> zostać zaimplementowany, jeśli ma zagnieżdżone hierarchie w celu obsługi ponownego ładowania zagnieżdżonych plików projektu.|

## <a name="see-also"></a>Zobacz też
- [Kontrola źródła pomocy technicznej](../../extensibility/internals/supporting-source-control.md)
