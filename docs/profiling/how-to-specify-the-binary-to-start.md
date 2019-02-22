---
title: 'Instrukcje: Określanie plików binarnych do uruchomienia | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a03bf203e5078bdbdf6327ec7bda186613a25c03
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622660"
---
# <a name="how-to-specify-the-binary-to-start"></a>Instrukcje: Określanie plików binarnych do uruchomienia

Do profilu plików binarnych takich jak biblioteki dll, należy wprowadzić informacje w  **\<docelowy > strony właściwości** okno dialogowe. Te informacje wskazują, gdzie znaleźć aplikacji wywołującej projektu DLL.

1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy docelowy plik binarny, a następnie kliknij **właściwości**.

2. W **stron właściwości** okno dialogowe, kliknij przycisk **Uruchom** właściwości.

3. Wybierz **zastąpienie właściwości projektu** pole wyboru.

4. W **pliku wykonywalnego do uruchomienia** tekst pola, określ lokalizację pliku.

5. W **argumenty** tekstu należy określić argumenty, które są wymagane do uruchamiania aplikacji.

6. W **katalog roboczy** tekstu określ lokalizację katalogu.

7. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)