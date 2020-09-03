---
title: Jak uruchomić i zakończyć zbieranie danych wydajności | Microsoft Docs
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: eedc7f42f2372452fa2cb96279e8b936bdc15e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331340"
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
