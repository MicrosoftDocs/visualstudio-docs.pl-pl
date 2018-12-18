---
title: Widok okresu istnienia obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cc2e17084809e691838ea0e681e3d2b766d0769
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756444"
---
# <a name="object-lifetime-view"></a>Widok okresu istnienia obiektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok okresu istnienia obiektu, jest dostępny, gdy **również zbieranie danych o okresie istnienia obiektu platformy .NET** zaznaczono na stronach właściwości sesji wydajności.  
  
 Moduł zbierający elementy bezużyteczne z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zarządza alokacją i zwolnieniem pamięci dla aplikacji. W celu zoptymalizowania wydajności moduł zbierający elementy bezużyteczne, zarządzanego stosu jest podzielony na trzy generacje: 0, 1 i 2. Moduł odśmiecania pamięci środowiska uruchomieniowego zapisuje nowe obiekty w generacji 0. Obiekty, które przeżyły kolekcje są promowane i przechowywane w generacji 1 i 2.  
  
 Moduł odśmiecania pamięci odzyskuje pamięć, cofnięcie przydziału całego generacji obiektów. Dla obiektów, które zostały utworzone przez profilowanej aplikacji widok okresu istnienia obiektu przedstawia liczbę i rozmiar obiektów oraz jego generacji, w którym są odzyskiwane.  
  
## <a name="general"></a>Ogólne  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa klasy**|Nazwa klasy przydzielonego typu.|  
|**Identyfikator procesu**|Identyfikator procesu uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
  
## <a name="instance-data"></a>Dane wystąpienia  
 Dane wystąpienia wskazuje liczbę obiektów tego typu, które zostały utworzone w profilowania i generowania, w którym obiekty zostały z cofniętą alokacją przez moduł odśmiecania pamięci.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wystąpienia**|Liczba alokacji obiektów tego typu.|  
|**% Łącznej liczby wystąpień**|Wartość procentowa łącznej liczby przydziałów, które zostały wprowadzone w profilowania wykonywania.|  
|**Zebrane wystąpienia generowania 0**|Liczba wystąpień tego typu, które zostały z cofniętą alokacją algorytm wyrzucania elementów bezużytecznych generacji 0.|  
|**Zebrane wystąpienia generowania 1**|Liczba wystąpień tego typu, które zostały z cofniętą alokacją algorytm wyrzucania elementów bezużytecznych generacji 1.|  
|**Zebrane wystąpienia generowania 2**|Liczba wystąpień tego typu, które zostały z cofniętą alokacją algorytm wyrzucania elementów bezużytecznych generacji 2.|  
|**Wystąpienia aktywne na końcu**|Liczba wystąpień tego typu, które zostały nie cofnięto przydziału aż do końca przebiegu profilowania.|  
  
## <a name="size-byte-data"></a>Danych o rozmiarze (bajty)  
 Rozmiar (bajtów) danych wskazuje rozmiar obiektów tego typu, które zostały utworzone w profilowania i ilość pamięci, które zostało odzyskane w każdej generacji, w którym zostały cofnięciu przydziału obiektów.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Łączna liczba przydzielonych bajtów**|Całkowita liczba bajtów dla wszystkich wystąpień tego typu.|  
|**% Łącznej liczby bajtów**|Procent całkowita liczba przydzielonych bajtów w trakcie uruchomienia profilowania, przydzielonych dla wystąpienia tego typu.|  
|**Zebrane bajty generowania 0**|Rozmiar wystąpienia typu, które zostały z cofniętą alokacją algorytm wyrzucania elementów bezużytecznych generacji 0.|  
|**Zebrane bajty generowania 1**|Rozmiar wystąpienia typu, które zostały z cofniętą alokacją algorytm wyrzucania elementów bezużytecznych generacji 1.|  
|**Zebrane bajty generowania 2**|Rozmiar wystąpienia typu, które zostały z cofniętą alokacją algorytm wyrzucania elementów bezużytecznych generacji 2.|  
  
## <a name="large-object-heap-data"></a>Dane sterty obiektów wielkich  
 Alokator pamięci .NET zarządza bardzo duże obiekty w lokalizacji, który jest oddzielony od standardowego zarządzanego stosu. Dane sterty dużych obiektów wskazuje liczbę i rozmiar obiektów tego typu, które były zarządzane w tej lokalizacji.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Zebrane wystąpienia sterty obiektów wielkich**|Liczba wystąpień tego typu, które znajdowały się w stosie dużego obiektu i które zostały zebrane w profilowania przebieg.|  
|**Zebrane bajty sterty obiektów wielkich**|Rozmiar w bajtach wystąpień tego typu, które znajdowały się w stosie dużego obiektu i które zostały zebrane podczas uruchomienia profilowania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki danych pamięci platformy .NET](../profiling/dotnet-memory-data-views.md)



