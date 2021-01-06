---
title: Trwałość i uruchomiona tabela dokumentów | Microsoft Docs
description: Dowiedz się, w jaki sposób projekt koordynuje otwieranie, zapisywanie i zmienianie nazw dokumentów w uruchomionej tabeli dokumentów, która śledzi stan dokumentu w środowisku IDE programu Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bfc480c8b4a41fe29900681289ad08c54d3c1f31
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875963"
---
# <a name="persistence-and-the-running-document-table"></a>Trwałość i uruchamianie tabeli dokumentów
W środowisku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE projekty są całkowicie odpowiedzialne za zarządzanie trwałością elementów projektu, które są wykonywane za pomocą usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Dokumenty są podstawową jednostką trwałości w środowisku programu Visual Studio. Projekty koordynują otwieranie, zapisywanie i zmienianie nazw dokumentów z uruchomioną tabelą dokumentu (RDT), czyli zasobem śledzącym stan wszystkich otwartych dokumentów.

## <a name="managing-persistence"></a>Zarządzanie trwałością
 Projekty kontrolują usługę trwałości środowiska przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfejsu. Mimo że środowisko nigdy nie poprosi bezpośrednio o utrwalenie dokumentu, prosi o zaprojektowanie projektu (lub hierarchii) o zapisanie dokumentu. Dzięki temu projekt może zapisywać dane elementów projektu w plikach lokalnych, plikach zdalnych, bazie danych, repozytorium lub innym nośniku.

 Środowisko globalne utrzymuje RDT. Środowisko zachowuje wpisy dla wszystkich otwartych okien i dokumentów w RDT, co umożliwia im otrzymywanie powiadomień specjalnych, takich jak w przypadku zamknięcia rozwiązania. Ponadto RDT sprawia, że środowisko śledzi odpowiednie węzły w **Eksplorator rozwiązań**. RDT obsługuje jeden rekord na otwarty, trwały obiekt, w tym pliki projektu i dokumenty elementów projektu.

## <a name="see-also"></a>Zobacz też
- [Uruchamianie tabeli dokumentu](../../extensibility/internals/running-document-table.md)
- [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
