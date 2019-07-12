---
title: Raport dotyczący znaczników | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97705dab6f11ca0d9d51c27bfc56d315b454bc52
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "64837700"
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
> Raport dotyczący znaczników można wyświetlić 1000 znaczników. Aby wyświetlić wszystkie znaczniki, należy wyeksportować pełny raport do pliku CSV.
