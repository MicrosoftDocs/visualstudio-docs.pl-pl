---
title: Widok linii - dane próbkowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2e5511e9e2e1c863db8f696a70195573d75429f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433871"
---
# <a name="lines-view---sampling-data"></a>Widok linii — dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uruchom wiersze widok pobierania próbek danych zawiera dane o wydajności dla instrukcji, które były wykonywane w chwili przykłady zostały zebranych podczas profilowania.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 W pliku źródłowym instrukcji może obejmować więcej niż jeden wiersz w pliku źródłowym, a jeden wiersz może zawierać więcej niż jedną instrukcję. Instrukcja jest identyfikowane przez następujące elementy:  
  
- Plik źródłowy, który zawiera deklarację funkcji.  
  
- Funkcja, która zawiera instrukcję.  
  
- Wiersza źródłowego, od której rozpoczyna się wykonywanie instrukcji.  
  
- Znak w wierszu źródłowym, w którym rozpoczyna się wykonywanie instrukcji.  
  
- Wiersza źródłowego, w którym kończy się instrukcji.  
  
- Znak w wierszu źródłowym, w którym kończy się instrukcji.  
  
  Kolumna Nazwa wiersza zawiera wzorzec sortowalnej łączenia danych identyfikator.  
  
  Zgodnie z definicją instrukcja wywołuje inne funkcje. W związku z tym są wyświetlane tylko wyłączne wartości.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera wiersz funkcji.|  
|**Ścieżka modułu**|Ścieżka modułu, który zawiera wiersz funkcji.|  
|**Plik źródłowy**|Plik źródłowy, zawierające następujący wiersz w funkcji.|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Adres początkowy funkcji.|  
|**Początkowy wiersz w źródle**|Numer wiersza początkowego w pliku źródłowym, w którym zostały zebrane w tym przykładzie.|  
|**Końcowy wiersz w źródle**|Końcowy numer wiersza w pliku źródłowym, w którym zostały zebrane w tym przykładzie.|  
|**Początkowy znak w źródle**|Przesunięcie początkowy znak w wierszu pliku źródłowego, w którym zostały zebrane w tym przykładzie.|  
|**Końcowy znak w źródle**|Przesunięcie końcowy znak w wierszu pliku źródłowego, w którym zostały zebrane w tym przykładzie.|  
|**Nazwa wiersza**|Generowane przez program profilujący identyfikator wiersza przy użyciu następującej składni:`Source File`**; [**  `Line Number Start` **,**`Character Start`**] ->; [** `Line Number End`**,**`Character End`**]**|  
|**Próbki wyłączne**|Łączna liczba próbek, które zostały zebrane podczas wykonywania wiersza funkcji.|  
|**% Wyłącznych próbek**|Procent wszystkich przykładów podczas uruchomienia profilowania, które zostały zebrane podczas wykonywania wiersza funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wierszy — Próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)
