---
title: Trwałość i uruchamianie dokumentu tabeli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b734d21950fd3765a7c331bbcdc47177f48e2b0a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726096"
---
# <a name="persistence-and-the-running-document-table"></a>Trwałość i uruchamianie tabeli dokumentów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE, projekty są całkowicie odpowiedzialni za zarządzanie trwałości ich elementów projektu, które realizowane przy użyciu usługi, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Dokumenty są podstawową jednostką trwałości w środowisku Visual Studio. Projekty koordynować otwieranie, zapisywanie i zmiana nazwy dokumentów za pomocą uruchomionej tabeli dokumentu (Normalizacją) z zasobem, który śledzi stan wszystkich otwartych dokumentach.  
  
## <a name="managing-persistence"></a>Zarządzanie trwałości  
 Projekty sterowania usługą trwałości środowiska poprzez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfejsu. Podczas środowiska prosi nigdy bezpośrednio dokumentu się, prosi będąca właścicielem projektu (lub hierarchia) można zapisać dokumentu. Dzięki temu możliwe dla projektu, aby zapisać swoje dane elementu projektu w lokalnych plików, pliki zdalne, bazę danych, repozytorium lub innego nośnika.  
  
 W środowisku globalnym zachowuje Normalizacją. Środowisko obsługuje wpisy dla wszystkich okien i dokumentów w Normalizacją, co umożliwia im odbieranie powiadomień specjalne, np. po zamknięciu rozwiązania. Ponadto Normalizacją umożliwia środowiska śledzić ich odpowiednich węzłów w **Eksploratora rozwiązań**. Normalizacją utrzymuje jeden rekord dla każdego obiektu otwarte, stałe, w tym pliki projektu i elementu projektu dokumentów.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie tabeli dokumentu](../../extensibility/internals/running-document-table.md)   
 [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

