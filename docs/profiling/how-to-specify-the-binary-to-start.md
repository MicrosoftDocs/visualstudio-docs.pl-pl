---
title: Określ plik binarny do uruchomienia | Microsoft Docs
description: Dowiedz się, w jaki sposób należy wprowadzić informacje w <Target> oknie dialogowym strony właściwości w celu profilowania plików binarnych, takich jak biblioteki DLL.
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
ms.openlocfilehash: 715c92a26ae33a4e909ec737c866be1cdc15251e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721843"
---
# <a name="how-to-specify-the-binary-to-start"></a>Instrukcje: Określanie pliku binarnego do uruchomienia

Aby profilować pliki binarne, takie jak biblioteki DLL, należy wprowadzić informacje w oknie dialogowym **\<Target> strony właściwości** . Te informacje wskazują, gdzie projekt DLL może znaleźć aplikację wywołującą.

1. W **Eksplorator wydajności** kliknij prawym przyciskiem myszy docelowy plik binarny, a następnie kliknij polecenie **Właściwości**.

2. W oknie dialogowym **strony właściwości** kliknij przycisk właściwości **uruchamiania** .

3. Zaznacz pole wyboru **Zastąp właściwości projektu** .

4. W polu tekstowym **plik wykonywalny do uruchomienia** Określ lokalizację pliku.

5. W polu tekstowym **argumenty** określ argumenty wymagane do uruchomienia aplikacji.

6. W polu tekstowym **katalog roboczy** Określ lokalizację katalogu.

7. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
