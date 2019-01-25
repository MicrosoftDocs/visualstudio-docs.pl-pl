---
title: 'Instrukcje: Wdrażanie oraz publikowanie rozwiązania SharePoint w lokalnej witrynie programu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2efdc339500786de87c35b4caeb3c85cef5191b7
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864101"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Instrukcje: Wdrażanie oraz publikowanie rozwiązania SharePoint w lokalnej witrynie SharePoint
  Można wdrożyć i publikować rozwiązań programu SharePoint na lokalnym serwerze programu SharePoint na komputerze deweloperskim. Kopiuje procesu wdrażania *.wsp* pliku na serwerze programu SharePoint, instaluje rozwiązanie, a następnie aktywuje funkcje. Publikowanie przetwarzać tylko kopie *.wsp* pliku na serwerze programu SharePoint i instaluje je. Należy ręcznie aktywuj go, aby ją włączyć w programie SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Aby wdrożyć rozwiązania programu SharePoint do lokalnego serwera programu SharePoint  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt, który chcesz wdrożyć.  
  
2.  Na pasku menu wybierz **kompilacji**, **wdrożyć rozwiązanie**.  
  
     *.Wsp* pliku jest tworzony i zainstalowane na lokalnym serwerze programu SharePoint. Ponadto funkcje zostaną aktywowane.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Publikowanie rozwiązania SharePoint na lokalnym serwerze programu SharePoint  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu programu SharePoint, który chcesz opublikować, a następnie wybierz **Publikuj**.  
  
2.  W **Publikuj** okna dialogowego wybierz **opublikowanie w systemie plików** przycisku opcji.  
  
3.  W **lokalizacji docelowej** polu tekstowym wprowadź ścieżkę lokalną, a następnie wybierz **Publikuj** przycisku.  
  
     Publikowanie postępu jest wyświetlana w programie Visual Studio **dane wyjściowe** okna. Po zakończeniu procesu rozwiązania (*.wsp*) plik jest zainstalowany na lokalnym serwerze programu SharePoint. Jednak go nadal należy aktywować ma być używany w programie SharePoint. Jeśli plik rozwiązania już istnieje, występuje błąd i pyta, czy chcesz zastąpić istniejący plik. Aby uzyskać informacje na temat uaktualniania pakietu, zobacz sekcję na temat uaktualniania pakiety zdalne w [jak: Wdrażanie, publikowanie oraz aktualizowanie rozwiązań SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Wdrażanie, publikowanie oraz aktualizowanie rozwiązań SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
