---
title: Trwałość i uruchomiona tabela dokumentów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706717"
---
# <a name="persistence-and-the-running-document-table"></a>Trwałość i uruchamianie tabeli dokumentów
W środowisku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE projekty są całkowicie odpowiedzialne za zarządzanie trwałością elementów projektu, które są wykonywane za pomocą usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Dokumenty są podstawową jednostką trwałości w środowisku programu Visual Studio. Projekty koordynują otwieranie, zapisywanie i zmienianie nazw dokumentów z uruchomioną tabelą dokumentu (RDT), czyli zasobem śledzącym stan wszystkich otwartych dokumentów.

## <a name="managing-persistence"></a>Zarządzanie trwałością
 Projekty kontrolują usługę trwałości środowiska przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfejsu. Mimo że środowisko nigdy nie poprosi bezpośrednio o utrwalenie dokumentu, prosi o zaprojektowanie projektu (lub hierarchii) o zapisanie dokumentu. Dzięki temu projekt może zapisywać dane elementów projektu w plikach lokalnych, plikach zdalnych, bazie danych, repozytorium lub innym nośniku.

 Środowisko globalne utrzymuje RDT. Środowisko zachowuje wpisy dla wszystkich otwartych okien i dokumentów w RDT, co umożliwia im otrzymywanie powiadomień specjalnych, takich jak w przypadku zamknięcia rozwiązania. Ponadto RDT sprawia, że środowisko śledzi odpowiednie węzły w **Eksplorator rozwiązań**. RDT obsługuje jeden rekord na otwarty, trwały obiekt, w tym pliki projektu i dokumenty elementów projektu.

## <a name="see-also"></a>Zobacz też
- [Uruchamianie tabeli dokumentu](../../extensibility/internals/running-document-table.md)
- [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
