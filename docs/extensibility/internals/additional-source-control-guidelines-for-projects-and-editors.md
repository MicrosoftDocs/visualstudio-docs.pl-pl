---
title: Wskazówki dotyczące projektach i edytorach kontroli źródła dodatkowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4051052a9eeddf45f66bf9b01dcbf608f396b7d8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857792"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Wskazówki dotyczące projektach i edytorach kontroli dodatkowe źródła
Istnieje kilka wskazówek, które projektach i edytorach powinien spełniać w celu obsługi kontroli źródła.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
 Swój projekt lub Edytor również należy wykonać następujące polecenie, aby obsługiwać kontroli źródła:  
  
|Obszar|Projekt|Edytor|Szczegóły|  
|----------|-------------|------------|-------------|  
|Prywatne kopie plików|X||Środowisko obsługuje prywatnej kopii plików. Oznacza to, że każda osoba zarejestrowana w projekcie ma swoje własne prywatną kopię plików, w tym projekcie.|  
|ANSI/Unicode trwałości|X|X|Jeśli piszesz kod stanu trwałego, utrwalanie plików, w postaci ANSI, ponieważ w większości programów kontroli źródła aktualnie nie obsługuje standardu Unicode.|  
|Wyliczanie plików|X||Projekt musi zawierać listę wszystkich plików w nim i musi być w stanie wyliczyć listy plików przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Projekt również powinny ujawniać nazw elementów za pomocą jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implementacja i obsługa techniczna wyszukiwanie nazw (w tym specjalnych plików) za pośrednictwem jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementacji.|  
|Format tekstu|X|X|Jeśli to możliwe, że pliki powinny być w formacie tekstowym, które umożliwiają łączenie różnych wersji. Pliki, które nie są w formacie tekstowym nie można scalić z innymi wersjami go później. Format tekstu preferowane jest XML.|  
|Na podstawie odwołań|X||Projekty oparte na odwołanie łatwo są obsługiwane w kontroli źródła. Jednak projekty oparte na katalog są również obsługiwane przez kontroli źródła, tak długo, jak projekt może wygenerować listy plików na żądanie, niezależnie od tego, czy te pliki znajdują się na dysku. Podczas otwierania projektu z kontroli źródła, plik projektu jest obniżona przed jej plików.|  
|Utrwalanie obiektami i właściwościami w przewidywalnej kolejności|X|X|Utrwalanie plików w przewidywalnej kolejności, takie jak kolejności alfabetycznej, aby ułatwić scalania.|  
|Załaduj ponownie|X|X|Gdy plik ulegnie zmianie na dysku, Edytor musi umożliwiać załadować go ponownie. Kiedy użytkownik uczestniczy w kontroli źródła, środowiska spowoduje ponowne załadowanie danych dla Ciebie, wywołując usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementacji. Podczas wyewidencjonowania wywołanego IVsQueryEditQuerySave jest najtrudniejsze przypadków ponowne załadowanie::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przetwarzania informacji. Jednak kod Załaduj ponownie musi mieć możliwość uruchamiania w takiej sytuacji.<br /><br /> Środowisko automatycznie ponownie ładuje pliki projektu. Jednakże, projekt musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> jeśli zawiera on zagnieżdżone hierarchie w celu zapewnienia obsługi ponownego ładowania zagnieżdżonych plików projektu.|  
  
## <a name="see-also"></a>Zobacz także  
 [Obsługa kontroli źródła](../../extensibility/internals/supporting-source-control.md)