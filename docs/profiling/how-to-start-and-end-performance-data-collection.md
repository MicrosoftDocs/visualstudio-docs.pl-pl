---
title: Zbieranie danych o wydajności początkowej i końcowej | Microsoft Docs
description: Dowiedz się, jak dodać docelowy plik binarny, który ma być profilem sesji wydajności przed rozpoczęciem profilowania.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e28d582dbbe25d587611b6b3174a4d4277887a39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920694"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Instrukcje: uruchamianie i kończenie zbierania danych wydajności
Należy dodać docelowy plik binarny, który ma być profilem sesji wydajności przed rozpoczęciem profilowania. Aby dodać obiekt docelowy, kliknij prawym przyciskiem myszy pozycję **obiekty docelowe** w **Eksplorator wydajności**, a następnie kliknij polecenie **Dodaj docelowy plik binarny**. W oknie dialogowym **Dodaj docelowy plik binarny** wybierz nazwę pliku, a następnie kliknij przycisk **Otwórz**. Zostanie dodany nowy plik binarny.

### <a name="to-start-profiling"></a>Aby rozpocząć profilowanie

1. Kliknij prawym przyciskiem myszy nazwę sesji wydajności w oknie **Eksplorator wydajności** i wybierz jedną z następujących opcji:

    - **Uruchom przy użyciu profilowania** — uruchamia aplikację i od razu rozpoczyna profilowanie.

    - **Uruchamianie przy użyciu wstrzymania profilowania** — uruchamia aplikację, ale nie rozpoczyna profilowania. Profilowanie można uruchomić, wybierając pozycję **Wznów zbieranie** w oknie **kontroli zbierania danych** . Aby uzyskać więcej informacji, zobacz [jak: Wstrzymywanie i wznawianie zbierania danych wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md).

### <a name="to-end-profiling"></a>Aby zakończyć profilowanie

- Preferowaną metodą zakończenia sesji profilowania jest zamknięcie aplikacji. Aby natychmiast zatrzymać profilowanie, na pasku narzędzi **Eksplorator wydajności** kliknij przycisk **Zatrzymaj**.

## <a name="see-also"></a>Zobacz też
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)
- [Instrukcje: wstrzymywanie i wznawianie zbierania danych o wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md)
