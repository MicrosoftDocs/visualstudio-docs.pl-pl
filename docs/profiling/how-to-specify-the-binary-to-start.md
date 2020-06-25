---
title: Jak określić plik binarny do uruchomienia | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 7f7cfd0d7a578d2ddaff28e9821f1d190bb2e10d
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331455"
---
# <a name="how-to-specify-the-binary-to-start"></a>Instrukcje: Określanie pliku binarnego do uruchomienia

Aby profilować pliki binarne, takie jak biblioteki DLL, należy wprowadzić informacje w oknie dialogowym ** \<Target> strony właściwości** . Te informacje wskazują, gdzie projekt DLL może znaleźć aplikację wywołującą.

1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy docelowy plik binarny, a następnie kliknij polecenie **Właściwości**.

2. W oknie dialogowym **strony właściwości** kliknij przycisk właściwości **uruchamiania** .

3. Zaznacz pole wyboru **Zastąp właściwości projektu** .

4. W polu tekstowym **plik wykonywalny do uruchomienia** Określ lokalizację pliku.

5. W polu tekstowym **argumenty** określ argumenty wymagane do uruchomienia aplikacji.

6. W polu tekstowym **katalog roboczy** Określ lokalizację katalogu.

7. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
