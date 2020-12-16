---
title: Korzystanie z plików lokalnej bazy danych w rozwiązaniach pakietu Office — omówienie
description: Dowiedz się, w jaki sposób można dołączyć plik bazy danych, taki jak plik SQL Server Express (. mdf) lub plik Microsoft Office Access (. mdb), w rozwiązaniu pakietu Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1a3166a88080eaee1042187c171c4938d236058a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526552"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Korzystanie z plików lokalnej bazy danych w rozwiązaniach pakietu Office — omówienie
  Możesz dołączyć plik bazy danych, taki jak plik SQL Server Express (*. mdf*) lub plik Microsoft Office Access (*. mdb*), w rozwiązaniu pakietu Office. Dzięki temu użytkownicy końcowi mogą utrzymywać lokalną bazę danych w sytuacjach, gdy utrzymanie scentralizowanej bazy danych nie jest wymagane, na przykład w rozwiązaniu do spisu lokalnego, które jest używane tylko na jednym komputerze.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Zaimportuj plik bazy danych do projektu
 Aby zaimportować plik bazy danych do projektu, użyj **Kreatora konfiguracji źródła danych** , aby utworzyć źródło danych na podstawie pliku bazy danych. Kreator dodaje plik bazy danych i typ zestawu danych do projektu.

## <a name="deploy-the-database-file"></a>Wdróż plik bazy danych
 **Kreator konfiguracji źródła danych** używa ścieżki względnej w celu utworzenia połączeń z lokalnym plikiem bazy danych. Dzięki temu można skopiować rozwiązanie z jednego komputera do drugiego, jeśli zachowasz względne położenia plików.

 W przypadku wdrożenia rozwiązania na serwerze, a następnie rozesłania dokumentu do każdego użytkownika końcowego należy również ręcznie rozproszyć plik bazy danych i zainstalować go w tym samym miejscu względem dokumentu. Oznacza to, że użytkownik końcowy nie może przenieść dokumentu do nowej lokalizacji na jego komputerze, chyba że przeniesie również plik bazy danych.

## <a name="local-database-files-and-caching-the-dataset"></a>Lokalne pliki bazy danych i buforowanie zestawu danych
 W rozwiązaniach na poziomie dokumentu dla Microsoft Office Excel i Microsoft Office Word można buforować zestawy danych w dokumencie, zaznaczając wystąpienie DataSet z atrybutem <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Po dodaniu pliku bazy danych do projektu za pomocą **Kreatora konfiguracji źródła danych**, zestaw danych zostanie dodany do projektu automatycznie. Nie jest to rzadko konieczne do zastosowania <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> do tego zestawu danych, ponieważ dane są już lokalne na komputerze użytkownika. Aby uzyskać więcej informacji, zobacz [cache Data](../vsto/caching-data.md).

## <a name="see-also"></a>Zobacz też
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Instrukcje: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Dane pamięci podręcznej](../vsto/caching-data.md)
