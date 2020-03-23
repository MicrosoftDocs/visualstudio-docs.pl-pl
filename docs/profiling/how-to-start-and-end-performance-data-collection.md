---
title: 'Jak: Uruchamianie i kończy zbieranie danych o wydajności | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: da75306018cf19855c7cb7f74ac3ffc4e84bcd9a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774514"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Jak: Uruchamianie i kończy zbieranie danych o wydajności
Przed rozpoczęciem profilowania należy dodać docelowy plik binarny, który ma zostać profilowany do sesji wydajności. Aby dodać cel, kliknij prawym przyciskiem myszy pozycję **Cele** w **Eksploratorze wydajności,** a następnie kliknij polecenie **Dodaj plik binarny docelowy**. W oknie dialogowym **Dodawanie pliku binarnego obiektu docelowego** zaznacz nazwę pliku, a następnie kliknij przycisk **Otwórz**. Dodano nowy plik binarny.

### <a name="to-start-profiling"></a>Aby rozpocząć profilowanie

1. Kliknij prawym przyciskiem myszy nazwę sesji wydajności w oknie **Eksploratora wydajności** i wybierz jedną z następujących opcji:

    - **Uruchom z profilowania** - uruchamia aplikację i natychmiast rozpoczyna profilowanie.

    - **Uruchom z profilowania wstrzymane** - uruchamia aplikację, ale nie rozpoczyna profilowania. Profilowanie można rozpocząć, wybierając polecenie **Wznów zbieranie** danych w oknie **Kontrola zbierania danych.** Aby uzyskać więcej informacji, zobacz [Jak: Wstrzymanie i wznowienie zbierania danych o wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md).

### <a name="to-end-profiling"></a>Aby zakończyć profilowanie

- Preferowaną metodą zakończenia sesji profilowania jest wyjście z aplikacji. Aby natychmiast zatrzymać profilowanie, na pasku narzędzi **Eksploratora wydajności** kliknij przycisk **Zatrzymaj**.

## <a name="see-also"></a>Zobacz też
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)
- [Instrukcje: wstrzymywanie i wznawianie zbierania danych o wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md)
