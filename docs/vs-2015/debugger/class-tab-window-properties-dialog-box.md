---
title: Karta Klasa, okno dialogowe Właściwości okna | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7f81a100b2c2311444732434df0f5c5599742a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161612"
---
# <a name="class-tab-window-properties-dialog-box"></a>Karta Klasa, okno dialogowe właściwości okna
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
