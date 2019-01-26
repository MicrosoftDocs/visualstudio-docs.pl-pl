---
title: 'Instrukcje: Określanie nazwy Menu Start dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2ac32b9be940883953d69e0347ffa5e12d5407a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945622"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Instrukcje: Określanie nazwy menu Start dla aplikacji ClickOnce
Gdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalacji aplikacji do użytku w trybie online i offline, wpis jest dodawany do **Start** menu i **apletu Dodaj lub usuń programy** listy. Domyślnie nazwa wyświetlana jest taka sama jak nazwa zestawu aplikacji, ale można zmienić nazwę wyświetlaną, ustawiając **nazwa produktu** w **opcji publikowania** okno dialogowe.  
  
 **Nazwa produktu** będą wyświetlane na *publish.htm* stronie; dla zainstalowanej aplikacji w trybie offline, będzie on nazwę wpisu w **Start** menu, a będzie również nazwę, która zawiera w **Dodaj lub usuń programy**.  
  
 **Nazwa wydawcy** pojawi się na *publish.htm* strony powyżej **nazwa produktu**, a dla zainstalowanej aplikacji w trybie offline, konieczne będzie również nazwę folderu, który zawiera aplikację Ikona w **Start** menu.  

 Odwołanie aplikacji lub skrót menu Start powstaje w *%appdata%\Microsoft\Windows\Start Start\Programy\\< nazwa wydawcy\>*. Odwołanie aplikacji lub skrót ma taką samą nazwę jak nazwa produktu.
  
 Możesz ustawić **nazwa produktu** i **nazwę wydawcy** właściwości w **opcji publikowania** okno dialogowe, dostępne na **Publikuj** strony z **Projektant projektu**.  
  
### <a name="to-specify-a-start-menu-name"></a>Aby określić nazwy menu Start  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **opcje** przycisk, aby otworzyć **opcji publikowania** okno dialogowe.  
  
4.  Kliknij przycisk **opis**.  
  
5.  W **opcji publikowania** okna dialogowego wprowadź nazwę, aby wyświetlić **nazwa produktu**.  
  
6.  Opcjonalnie można wprowadzić nazwę wydawcy w **nazwę wydawcy**.  
  
## <a name="see-also"></a>Zobacz także  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)