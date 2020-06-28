---
title: Błąd — serwer sieci Web nie może znaleźć żądanego zasobu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 5cce9afe8f27b25a01c0f6276164522a78a2ed9a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460354"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Błąd: serwer sieci Web nie mógł znaleźć żądanego zasobu
Ze względu na zabezpieczenia usługi IIS zwróciły błąd ogólny.

Jedną z możliwych przyczyn jest Konfiguracja zabezpieczeń serwera. W usługach IIS 6,0 i starszych wersjach użyto programu dodatkowego, znanego jako URLScan, do odfiltrowania podejrzanych i źle sformułowanych żądań. Usługi IIS 7,0 mają wbudowane Filtrowanie żądań w tym samym celu. W obu przypadkach nadmierne ograniczanie filtrowania żądań może uniemożliwić Debugowanie serwera przez program Visual Studio.

Inną możliwą przyczyną tego błędu jest to, że usługa W3SVC dla usług IIS nie została uruchomiona. Sprawdź, czy ta usługa jest uruchomiona (wyszarzona) w oknie usługi (*Services. msc*).

Istnieje wiele dodatkowych możliwych przyczyn tego błędu. Niektóre z najczęstszych przyczyn obejmują problem z instalacją lub konfiguracją usług IIS, konfiguracją witryny sieci Web lub uprawnieniami w systemie plików. Możesz spróbować uzyskać dostęp do zasobu za pomocą przeglądarki. W zależności od konfiguracji usług IIS może być konieczne użycie przeglądarki lokalnej na serwerze lub sprawdzenie dziennika błędów usług IIS w celu uzyskania szczegółowego komunikatu o błędzie.

 Aby uzyskać więcej informacji na temat rozwiązywania problemów z usługami IIS, zobacz [Zarządzanie usługami IIS i administrowanie](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration)nimi.

## <a name="see-also"></a>Zobacz też
- [Błąd: serwer sieci Web został zablokowany i blokuje czasownik debugowania](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)