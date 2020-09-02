---
title: Raport znaczników | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837700"
---
# <a name="markers-report"></a>Raport dotyczący znaczników
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Raport znaczniki wyświetla listę znaczników w wyświetlanym czasie.  Kadrowanie lub powiększanie lub ukrywanie ścieżek może spowodować, że znaczniki będą widoczne lub znikane. Raport zawiera te informacje o każdym znaczniku:  
  
- Godzina rozpoczęcia śledzenia, odnosząca się do początku.  
  
- Jego czas trwania. Czas trwania flag i komunikatów jest równy zero, ponieważ reprezentuje on natychmiastowe.  
  
- Identyfikator wątku, który go wygenerował.  
  
- Dostawca śledzenia zdarzeń dla systemu Windows (ETW), który go wygenerował.  
  
- Seria znaczników, z której został zapisany.  
  
- Kategoria zdarzeń, do której należy.  
  
- Jego poziom ważności.  
  
- Jego typ (zakres, flaga lub komunikat).  
  
- Ogólny opis tego, co reprezentuje  
  
  Wybierz przycisk **Eksportuj** , aby zapisać raport znaczników jako plik CSV. Możesz użyć danych z pliku CSV z innymi aplikacjami lub narzędziami.  
  
> [!NOTE]
> Raport znaczników może zawierać 1 000 znaczników. Aby wyświetlić wszystkie znaczniki, należy wyeksportować pełny raport do pliku CSV.
