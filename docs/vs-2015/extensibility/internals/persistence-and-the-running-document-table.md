---
title: Trwałość i uruchomiona tabela dokumentów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c422ad1735312c82c8dc027c4adf73c1b033685
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196096"
---
# <a name="persistence-and-the-running-document-table"></a>Trwałość i uruchamianie tabeli dokumentów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W środowisku [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE projekty są całkowicie odpowiedzialne za zarządzanie trwałością elementów projektu, które są wykonywane za pomocą usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Dokumenty są podstawową jednostką trwałości w środowisku programu Visual Studio. Projekty koordynują otwieranie, zapisywanie i zmienianie nazw dokumentów z uruchomioną tabelą dokumentu (RDT), czyli zasobem śledzącym stan wszystkich otwartych dokumentów.  
  
## <a name="managing-persistence"></a>Zarządzanie trwałością  
 Projekty kontrolują usługę trwałości środowiska przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfejsu. Mimo że środowisko nigdy nie poprosi bezpośrednio o utrwalenie dokumentu, prosi o zaprojektowanie projektu (lub hierarchii) o zapisanie dokumentu. Dzięki temu projekt może zapisywać dane elementów projektu w plikach lokalnych, plikach zdalnych, bazie danych, repozytorium lub innym nośniku.  
  
 Środowisko globalne utrzymuje RDT. Środowisko zachowuje wpisy dla wszystkich otwartych okien i dokumentów w RDT, co umożliwia im otrzymywanie powiadomień specjalnych, takich jak w przypadku zamknięcia rozwiązania. Ponadto RDT sprawia, że środowisko śledzi odpowiednie węzły w **Eksplorator rozwiązań**. RDT obsługuje jeden rekord na otwarty, trwały obiekt, w tym pliki projektu i dokumenty elementów projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie tabeli dokumentu](../../extensibility/internals/running-document-table.md)   
 [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
