---
title: Trwałość i tabela bieżącego dokumentu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706717"
---
# <a name="persistence-and-the-running-document-table"></a>Trwałość i uruchamianie tabeli dokumentów
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE projekty są całkowicie odpowiedzialne za zarządzanie trwałością swoich elementów projektu, które osiągają za pomocą usługi. <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Dokumenty są podstawową jednostką trwałości w środowisku programu Visual Studio. Projekty koordynują otwieranie, zapisywanie i zmienianie nazw dokumentów za pomocą uruchomionej tabeli dokumentów (RDT), zasobu śledzącego stan wszystkich otwartych dokumentów.

## <a name="managing-persistence"></a>Zarządzanie trwałością
 Projekty kontrolują trwałość środowiska, implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfejs. Środowisko nigdy bezpośrednio nie prosi o upośmowanie się w dokumencie, ale prosi projekt będący właścicielem (lub hierarchię) o zapisanie dokumentu. Umożliwia to projektowi zapisanie danych elementu projektu w plikach lokalnych, plikach zdalnych, bazie danych, repozytorium lub innym nośniku.

 Środowisko globalne utrzymuje RDT. Środowisko przechowuje wpisy dla wszystkich otwartych okien i dokumentów w RDT, co umożliwia im odbieranie specjalnych powiadomień, takich jak po zamknięciu rozwiązania. Ponadto RDT umożliwia środowisku śledzenie odpowiadających im węzłów w **Eksploratorze rozwiązań.** RDT przechowuje jeden rekord na otwarty, trwały obiekt, w tym pliki projektu i dokumenty elementu projektu.

## <a name="see-also"></a>Zobacz też
- [Uruchamianie tabeli dokumentu](../../extensibility/internals/running-document-table.md)
- [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
