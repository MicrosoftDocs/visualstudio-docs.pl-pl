---
title: Korzystać z plików lokalnej bazy danych w rozwiązań Office ― omówienie
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 527b2e2561b89dc38e56c0d9d854034a791edf19
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939203"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Korzystać z plików lokalnej bazy danych w rozwiązań Office ― omówienie
  Można dołączyć plik bazy danych, takich jak SQL Server Express (*.mdf*) pliku lub Microsoft Office Access (*.mdb*) pliku w rozwiązania pakietu Office. To umożliwia użytkownikom końcowym zachować lokalnej bazy danych w sytuacji, w której obsługa scentralizowanej bazie danych nie jest wymagane, na przykład w przypadku rozwiązania lokalnego magazynu, jaka jest używana na pojedynczym komputerze.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="import-the-database-file-into-a-project"></a>Importowanie pliku bazy danych do projektu  
 Aby zaimportować plik bazy danych do projektu, należy użyć **Kreatora konfiguracji źródła danych** można utworzyć źródła danych, na podstawie pliku bazy danych. Kreator dodaje plik bazy danych i typizowany zestaw danych do projektu.  
  
## <a name="deploy-the-database-file"></a>Wdróż plik bazy danych  
 **Kreatora konfiguracji źródła danych** używa ścieżki względnej w celu utworzenia połączenia z pliku lokalnej bazy danych. Dzięki temu Kopiuj rozwiązania z jednego komputera na inny, jeśli to Ty masz względne położenie plików.  
  
 Jeśli wdrażać rozwiązania do serwera, a następnie rozpowszechnić dokument, aby każdy użytkownik końcowy, należy również ręcznie dystrybucji pliku bazy danych i zainstaluj go w tym samym położeniu względem dokumentu. Oznacza to, użytkownik końcowy nie może przenieść dokument do nowej lokalizacji, na swoim komputerze, chyba że jest on również przesuwa się pliku bazy danych.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Pliki lokalnej bazy danych i buforowania zestawu danych  
 W przypadku rozwiązań poziomie dokumentu dla programu Microsoft Office Excel i Microsoft Office Word może buforować zestawów danych w dokumencie, oznaczając wystąpienie zestawu danych za pomocą atrybutu <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Po dodaniu pliku bazy danych do projektu przy użyciu **Kreatora konfiguracji źródła danych**, typizowany zestaw danych jest automatycznie dodawany do projektu. Rzadko należy zastosować <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> do tego zestawu danych, ponieważ dane są już lokalnie na komputerze użytkownika. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Instrukcje: Zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Instrukcje: Aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Dane w pamięci podręcznej](../vsto/caching-data.md)  
