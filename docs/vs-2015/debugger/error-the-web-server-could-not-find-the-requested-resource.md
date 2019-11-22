---
title: 'Błąd: serwer sieci Web nie może znaleźć żądanego zasobu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 904d628b09c7add48460273ecaff7d8ac288cbc3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297426"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Błąd: serwer sieci Web nie mógł znaleźć żądanego zasobu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ze względu na zabezpieczenia usługi IIS zwróciły błąd ogólny.  
  
 Jedną z możliwych przyczyn jest Konfiguracja zabezpieczeń serwera. W usługach IIS 6,0 i starszych wersjach użyto programu dodatkowego, znanego jako URLScan, do odfiltrowania podejrzanych i źle sformułowanych żądań. Usługi IIS 7,0 mają wbudowane Filtrowanie żądań w tym samym celu. W obu przypadkach nadmierne ograniczanie filtrowania żądań może uniemożliwić Debugowanie serwera przez program Visual Studio.  
  
 Istnieje wiele możliwych przyczyn tego błędu. Niektóre z najczęstszych przyczyn obejmują problem z instalacją lub konfiguracją usług IIS, konfiguracją witryny sieci Web lub uprawnieniami w systemie plików. Możesz spróbować uzyskać dostęp do zasobu za pomocą przeglądarki. W zależności od konfiguracji usług IIS może być konieczne użycie przeglądarki lokalnej na serwerze lub sprawdzenie dziennika błędów usług IIS w celu uzyskania szczegółowego komunikatu o błędzie.  
  
 Aby uzyskać więcej informacji na temat rozwiązywania problemów z usługami IIS, zobacz [Zarządzanie usługami IIS i administrowanie](https://go.microsoft.com/fwlink/?LinkId=255872)nimi.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie URLScan Security](/iis/extensions/working-with-urlscan/urlscan-3-reference)   
 [Błąd: Serwer internetowy został zablokowany i blokuje czasownik DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
