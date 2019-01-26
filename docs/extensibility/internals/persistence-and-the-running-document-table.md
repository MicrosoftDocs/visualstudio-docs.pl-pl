---
title: Trwałość i uruchamianie dokumentu tabeli | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb66051d3a1ab0119f4b80a68f0f2990e569fe8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929773"
---
# <a name="persistence-and-the-running-document-table"></a>Trwałość i uruchamianie tabeli dokumentów
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, projekty są całkowicie odpowiedzialni za zarządzanie trwałości ich elementów projektu, które realizowane przy użyciu usługi, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Dokumenty są podstawową jednostką trwałości w środowisku Visual Studio. Projekty koordynować otwieranie, zapisywanie i zmiana nazwy dokumentów za pomocą uruchomionej tabeli dokumentu (Normalizacją) z zasobem, który śledzi stan wszystkich otwartych dokumentach.  
  
## <a name="managing-persistence"></a>Zarządzanie trwałości  
 Projekty sterowania usługą trwałości środowiska poprzez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfejsu. Podczas środowiska prosi nigdy bezpośrednio dokumentu się, prosi będąca właścicielem projektu (lub hierarchia) można zapisać dokumentu. Dzięki temu możliwe dla projektu, aby zapisać swoje dane elementu projektu w lokalnych plików, pliki zdalne, bazę danych, repozytorium lub innego nośnika.  
  
 W środowisku globalnym zachowuje Normalizacją. Środowisko obsługuje wpisy dla wszystkich okien i dokumentów w Normalizacją, co umożliwia im odbieranie powiadomień specjalne, np. po zamknięciu rozwiązania. Ponadto Normalizacją umożliwia środowiska śledzić ich odpowiednich węzłów w **Eksploratora rozwiązań**. Normalizacją utrzymuje jeden rekord dla każdego obiektu otwarte, stałe, w tym pliki projektu i elementu projektu dokumentów.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie tabeli dokumentu](../../extensibility/internals/running-document-table.md)   
 [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)