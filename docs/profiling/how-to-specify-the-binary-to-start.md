---
title: 'Jak: Określ binarny, aby rozpocząć | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fd3379b9769cfd6bfe1335b12545e635a9bde782
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778690"
---
# <a name="how-to-specify-the-binary-to-start"></a>Jak: Określ plik binarny, aby rozpocząć

Aby pliki binarne profilu, takie jak biblioteki DLL, należy wprowadzić informacje w oknie dialogowym ** \<Strony właściwości> docelowej.** Te informacje wskazują, gdzie projekt biblioteki DLL można znaleźć aplikacji wywołującej.

1. W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy docelowy plik binarny, a następnie kliknij polecenie **Właściwości**.

2. W oknie dialogowym **Strony właściwości** kliknij właściwości **Uruchom.**

3. Zaznacz pole wyboru **Zastądeń właściwości projektu.**

4. W polu tekstowym **Wykonywalny do uruchomienia** określ lokalizację pliku.

5. W polu tekstowym **Argumenty** określ argumenty, które są wymagane do uruchomienia aplikacji.

6. W polu tekstowym **Katalog roboczy** określ lokalizację katalogu.

7. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
