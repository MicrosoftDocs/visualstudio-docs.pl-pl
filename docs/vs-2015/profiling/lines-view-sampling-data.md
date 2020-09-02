---
title: Widok linii — dane próbkowania | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64832967"
---
# <a name="lines-view---sampling-data"></a>Widok linii — dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok linie danych próbkowania zawiera dane dotyczące wydajności dla instrukcji, które były wykonywane, gdy próbki zostały zebrane w ramach uruchomienia profilowania.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 W pliku źródłowym instrukcja może obejmować więcej niż jeden wiersz w pliku źródłowym, a pojedynczy wiersz może zawierać więcej niż jedną instrukcję. Instrukcja jest identyfikowana przez następujące elementy:  
  
- Plik źródłowy, który zawiera instrukcję Function.  
  
- Funkcja, która zawiera instrukcję.  
  
- Wiersz źródłowy, w którym rozpoczyna się wykonywanie instrukcji.  
  
- Znak w wierszu źródłowym, w którym rozpocznie się wykonywanie instrukcji.  
  
- Wiersz źródłowy, w którym zostanie zakończona instrukcja.  
  
- Znak w wierszu źródłowym, w którym następuje zakończenie instrukcji.  
  
  Kolumna Nazwa wiersza zawiera konkatenację łączenia danych identyfikatora.  
  
  Zgodnie z definicją instrukcja nie wywołuje innych funkcji. W związku z tym wyświetlane są tylko wartości wykluczane.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|  
|**Nazwa procesu**|Nazwa procesu|  
|**Nazwa modułu**|Nazwa modułu, który zawiera wiersz funkcji.|  
|**Ścieżka modułu**|Ścieżka modułu zawierającego wiersz funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera wiersz funkcji.|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Adres początkowy funkcji.|  
|**Początek linii źródłowej**|Początkowy numer wiersza w pliku źródłowym, w którym zebrano ten przykład.|  
|**Koniec linii źródłowej**|Końcowy numer wiersza w pliku źródłowym, w którym zebrano ten przykład.|  
|**Początek znaku źródłowego**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym ten przykład został zebrany.|  
|**Końcowy znak źródłowy**|Przesunięcie znaku końcowego w wierszu pliku źródłowego, w którym ten przykład został zebrany.|  
|**Nazwa wiersza**|Wygenerowany przez profiler Identyfikator wiersza o następującej składni: `Source File` **; [** `Line Number Start` **,**`Character Start` **]->; [**`Line Number End`**,**`Character End`**]**|  
|**Próbki wyłączne**|Całkowita liczba próbek zebranych podczas wykonywania wiersza funkcji.|  
|**Wyłącznych próbek%**|Procent wszystkich próbek w przebiegu profilowania, który został zebrany podczas wykonywania wiersza funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wierszy — próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)
