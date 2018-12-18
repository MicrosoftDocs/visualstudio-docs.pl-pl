---
title: Raport dotyczący znaczników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 044df49c466c98466e15078b38e6240420b0a6fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809717"
---
# <a name="markers-report"></a>Raport dotyczący znaczników
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Raport dotyczący znaczników Wyświetla listę znaczników w wyświetlany przedział czasu.  Przesuwanie powiększanie lub ukrywanie pasm, może spowodować znaczniki do wyświetlone lub znikają. Raport zawiera informacje o poszczególnych znaczników:  
  
- Czas, kiedy go już się rozpoczął, względem początku śledzenia.  
  
- Czas jego trwania. Czas trwania jest zero dla flag i komunikatów, ponieważ stanowią one natychmiastowe.  
  
- Identyfikator wątku, który ją wygenerowało.  
  
- Dostawca zdarzeń śledzenia dla Windows (ETW), które ją wygenerowało.  
  
- Seria znacznika, w którym został zapisany.  
  
- Kategoria zdarzenia, dla której należy.  
  
- Jej poziom ważności.  
  
- Jego typ (zakres, Flaga lub komunikat).  
  
- Co określa opis wysokiego poziomu  
  
  Wybierz **wyeksportować** przycisk, aby zapisać raport dotyczący znaczników do pliku CSV. Można użyć danych w pliku CSV z innymi aplikacjami lub narzędzia.  
  
> [!NOTE]
>  Raport dotyczący znaczników można wyświetlić 1000 znaczników. Aby wyświetlić wszystkie znaczniki, należy wyeksportować pełny raport do pliku CSV.



