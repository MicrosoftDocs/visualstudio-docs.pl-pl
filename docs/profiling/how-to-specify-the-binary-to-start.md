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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 575a55ae654ada9774abed510d66b94e4ce9d271
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899539"
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

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
