---
title: Wdróż & publikowanie rozwiązania SharePoint w lokalnej witrynie programu SharePoint
titleSuffix: ''
description: Zapoznaj się z tematem Wdrażanie lub publikowanie rozwiązań programu SharePoint na lokalnym serwerze programu SharePoint na komputerze deweloperskim.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 22fe46e2876b14551637dd97712e1728816b020e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913701"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Instrukcje: wdrażanie i publikowanie rozwiązania SharePoint w lokalnej witrynie programu SharePoint
  Rozwiązania programu SharePoint można wdrożyć lub opublikować na lokalnym serwerze programu SharePoint na komputerze deweloperskim. Proces wdrażania kopiuje plik *. wsp* do serwera programu SharePoint, instaluje rozwiązanie, a następnie aktywuje te funkcje. Proces publikowania kopiuje tylko plik *wsp* na serwer programu SharePoint i instaluje go. Należy ją uaktywnić ręcznie, aby włączyć ją w programie SharePoint.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Aby wdrożyć rozwiązanie SharePoint na lokalnym serwerze programu SharePoint

1. W **Eksplorator rozwiązań** wybierz projekt, który chcesz wdrożyć.

2. Na pasku menu wybierz **kompilacja**, **Wdróż rozwiązanie**.

     Plik *. wsp* jest tworzony i instalowany na lokalnym serwerze programu SharePoint. Ponadto funkcje są aktywowane.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Aby opublikować rozwiązanie SharePoint na lokalnym serwerze programu SharePoint

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu programu SharePoint, który chcesz opublikować, a następnie wybierz polecenie **Publikuj**.

2. W oknie dialogowym **Publikowanie** wybierz przycisk opcji **Publikuj w systemie plików** .

3. W polu tekstowym **Lokalizacja docelowa** wprowadź ścieżkę lokalną, a następnie wybierz przycisk **Publikuj** .

     Postęp publikowania pojawia się w oknie **danych wyjściowych** programu Visual Studio. Po zakończeniu procesu na lokalnym serwerze programu SharePoint jest instalowany plik rozwiązania (*wsp*). Jednak nadal musi być aktywowany, aby można go było używać w programie SharePoint. Jeśli plik rozwiązania już istnieje, wystąpi błąd i pyta, czy chcesz zastąpić istniejący plik. Informacje o uaktualnianiu pakietu znajdują się w sekcji dotyczącej uaktualniania pakietów zdalnych w artykule [jak: wdrażanie, publikowanie i uaktualnianie rozwiązań SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: wdrażanie, publikowanie i uaktualnianie rozwiązań SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
