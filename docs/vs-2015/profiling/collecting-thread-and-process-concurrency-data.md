---
title: Zbieranie danych współbieżności wątków i procesów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8a9de5f2a7e520a745fab81197016d6e1bd15d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568192"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Zbieranie danych współbieżności dla wątku i procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Metoda profilowania współbieżności narzędzia profilowania pozwala zbierać dane rywalizacji o zasoby zawierające informacje o każdym zdarzeniu synchronizacji, które powoduje, że funkcja w profilowanej aplikacji oczekuje na dostęp do zasobu.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Metodę profilowania współbieżności można określić przy użyciu jednej z następujących procedur:  
  
- Na pierwszej stronie kreatora profilowania kliknij pozycję **współbieżność**  
  
- Na stronie **Ogólne** okna dialogowego właściwości sesji wydajności kliknij pozycję **współbieżność**.  
  
- Na **Eksplorator wydajności** pasku narzędzi na liście **Metoda** kliknij pozycję **współbieżność**.  
  
## <a name="common-tasks"></a>Typowe zadania  
 Dodatkowe opcje można określić w oknie dialogowym _Performance Session_**strony właściwości** sesji wydajności. Aby otworzyć to okno dialogowe:  
  
- W **Eksplorator wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.  
  
  Zadania w poniższej tabeli opisują opcje, które można określić w oknie dialogowym**strony właściwości** _sesji wydajności_podczas profilowania przy użyciu metody współbieżności.  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|Na stronie **Ogólne** Określ szczegóły nazewnictwa dla wygenerowanego pliku danych profilowania (. vsp).|-   [Instrukcje: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na stronie **Uruchamianie** Określ aplikację, która ma być uruchamiana, jeśli w rozwiązaniu kodu masz wiele projektów. exe.|-   [Instrukcje: Określanie pliku binarnego do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|  
|Na stronie **interakcja warstwy** Dodaj dane wywołania ADO.NET do przebiegu profilowania.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na stronie **liczniki systemu Windows** Określ co najmniej jeden licznik wydajności systemu operacyjnego, który ma zostać dodany do danych profilowania jako znaczniki.|-   [Instrukcje: zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na stronie **Zaawansowane** określ wersję .NET Framework czasie wykonywania do profilowania, jeśli moduły aplikacji używają wielu wersji. Domyślnie pierwsza ładowana wersja jest profilowana.|-   [Instrukcje: Określanie środowiska uruchomieniowego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
