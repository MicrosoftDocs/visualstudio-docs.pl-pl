---
title: Karta Klasa, okno dialogowe Właściwości okna | Microsoft Docs
description: Wybierz kartę Klasa w programie Visual Studio, Przenieś fokus do okna widok systemu Windows, wybierz węzeł okna i wybierz polecenie Wyświetl > właściwości, aby wyświetlić okno dialogowe Właściwości okna.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bf37d9e5d672f0ecce262699fdd5d704cde9efe
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729031"
---
# <a name="class-tab-window-properties-dialog-box"></a>Karta Klasa, okno dialogowe właściwości okna
Użyj karty **klasy** , aby wyświetlić informacje o klasie wybranego okna. Aby wyświetlić okno [dialogowe Właściwości okna](../debugger/window-properties-dialog-box.md), Przenieś fokus do okna [Widok systemu Windows](../debugger/windows-view.md) . Wybierz dowolny węzeł okna w drzewie, a następnie wybierz polecenie **Właściwości** z menu **Widok** .

 Na karcie **Klasa** dostępne są następujące ustawienia:

|Wpis|Opis|
|-----------|-----------------|
|**Nazwa klasy**|Nazwa (lub numer porządkowy) tej klasy okna.|
|**Style klas**|Kombinacja kodów stylu klasy.|
|**Bajty klasy**|Dane specyficzne dla aplikacji skojarzone z tą klasą okna.|
|**Atom klasy**|Atom dla klasy zwróconej przez wywołanie **RegisterClass** .|
|**Dojście wystąpienia**|Uchwyt wystąpienia modułu, który zarejestrował klasę. Uchwyty wystąpienia nie są unikatowe.|
|**Bajty okna**|Liczba dodatkowych bajtów skojarzonych z każdym oknem tej klasy. Znaczenie tych bajtów jest określane przez aplikację. Rozwiń pole listy, aby wyświetlić wartości bajtów w formacie DWORD.|
|**Proces okna**|Bieżący adres funkcji **WndProc** dla systemu Windows tej klasy. Różni się to od procedury **okna** na karcie **Ogólne** , jeśli okno jest podklasy.|
|**Nazwa menu**|Nazwa menu głównego, które jest skojarzone z systemem Windows tej klasy ("Brak", jeśli nie istnieje menu).|
|**Uchwyt ikony**|Uchwyt ikony, która jest skojarzona z systemem Windows tej klasy ("Brak", jeśli nie ma ikony).|
|**Uchwyt kursora**|Uchwyt kursora, który jest skojarzony z systemem Windows tej klasy ("Brak", jeśli nie ma kursora).|
|**Pędzel pędzel**|Uchwyt dla pędzla tła, który jest skojarzony z systemem Windows tej klasy lub jeden ze wstępnie zdefiniowanych COLOR_ * kolorów do rysowania tła okna ("Brak", jeśli nie ma żadnego pędzla).|