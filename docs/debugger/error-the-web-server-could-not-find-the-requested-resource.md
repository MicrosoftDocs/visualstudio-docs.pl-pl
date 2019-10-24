---
title: 'Błąd: serwer sieci Web nie może znaleźć żądanego zasobu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5c9b428a03595f387c5ff6fb6f0b8ca35172752
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737248"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Błąd: serwer sieci Web nie mógł znaleźć żądanego zasobu
Ze względu na zabezpieczenia usługi IIS zwróciły błąd ogólny.

Jedną z możliwych przyczyn jest Konfiguracja zabezpieczeń serwera. W usługach IIS 6,0 i starszych wersjach użyto programu dodatkowego, znanego jako URLScan, do odfiltrowania podejrzanych i źle sformułowanych żądań. Usługi IIS 7,0 mają wbudowane Filtrowanie żądań w tym samym celu. W obu przypadkach nadmierne ograniczanie filtrowania żądań może uniemożliwić Debugowanie serwera przez program Visual Studio.

Inną możliwą przyczyną tego błędu jest to, że usługa W3SVC dla usług IIS nie została uruchomiona. Sprawdź, czy ta usługa jest uruchomiona (wyszarzona) w oknie usługi (*Services. msc*).

Istnieje wiele dodatkowych możliwych przyczyn tego błędu. Niektóre z najczęstszych przyczyn obejmują problem z instalacją lub konfiguracją usług IIS, konfiguracją witryny sieci Web lub uprawnieniami w systemie plików. Możesz spróbować uzyskać dostęp do zasobu za pomocą przeglądarki. W zależności od konfiguracji usług IIS może być konieczne użycie przeglądarki lokalnej na serwerze lub sprawdzenie dziennika błędów usług IIS w celu uzyskania szczegółowego komunikatu o błędzie.

 Aby uzyskać więcej informacji na temat rozwiązywania problemów z usługami IIS, zobacz [Zarządzanie usługami IIS i administrowanie](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration)nimi.

## <a name="see-also"></a>Zobacz także
- [Błąd: Serwer internetowy został zablokowany i blokuje czasownik DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)