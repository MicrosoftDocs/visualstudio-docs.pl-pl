---
title: 'Instrukcje: ClickOnce ustawienie wersji publikacji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd0f38fda93d1a91e72c547bdfe230354988da9d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869115"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Instrukcje: ClickOnce ustawienie wersji publikacji
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Właściwość określa, czy w przypadku publikowania aplikacji będzie traktowane jako aktualizację. Każda wersja czasu jest zwiększana, aplikacja zostanie opublikowana jako aktualizację.  
  
 `Publish Version` Właściwość można ustawić na **Publikuj** strony **projektanta projektu**.  
  
> [!NOTE]
>  Brak opcji projektu, który automatycznie powoduje zwiększenie `Publish Version` właściwość każdorazowo aplikacja została opublikowana; ta opcja jest włączona domyślnie. Aby uzyskać więcej informacji, zobacz [jak: Automatyczne ClickOnce zwiększenie wersji publikacji](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Aby zmienić wersję publikacji  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  W **opublikować wersję** pola, Zwiększ **głównych**, **pomocnicza**, **kompilacji**, lub **poprawki** wersji liczby.  
  
    > [!NOTE]
    >  Nigdy nie należy zmniejszyć numeru wersji; wykonanie tej tak może spowodować aktualizacji nieprzewidywalne zachowanie.  
  
## <a name="see-also"></a>Zobacz także  
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Instrukcje: Automatyczne ClickOnce zwiększenie wersji publikacji](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)