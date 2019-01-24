---
title: 'Instrukcje: Ustawianie opcji nazwy pliku danych wydajności | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3d513010b94c61e09f8bda6a9fb3074ba949bdd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760417"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Instrukcje: Ustawianie opcji nazwy pliku danych wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie zapiszesz plik danych (Vsp) profilowania przy użyciu następującej składni:  
  
 *Path\VSP-File\YYMMDD(N)* **.vsp**  
  
 Można zmienić żadnych nazw parametrów, na stronie Ogólne, okno dialogowe właściwości sesji wydajności.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
|||  
|-|-|  
|*Path*|Katalog, który zawiera raport. Domyślna lokalizacja to folder rozwiązania lub domyślna lokalizacja dla projektów i rozwiązań użytkownika.|  
|*VSP-File*|Nazwa pliku danych profilowania. Domyślną nazwą jest nazwa rozwiązania lub pliku wykonywalnego która profilowana jest.|  
|*YYMMDD*|Sygnatura daty, która zawiera rok, miesiąc i dzień, zebranych danych profilowania.|  
|*(N)*|Jeśli istnieje więcej niż jeden plik danych profilowania, zwiększona liczba jest dodawany do nazwy pliku w nawiasach.|  
  
### <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Aby zmienić Składnia nazwy pliku danych profilowania w sesji wydajności  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **ogólne**.  
  
3.  W obszarze **raportu**, zmienić dowolne z następujących ustawień:  
  
    |||  
    |-|-|  
    |**Lokalizacja raportu**|Określ katalog do przechowywania plików danych profilowania.|  
    |**Nazwa raportu**|Określ nazwę bazową dla plików.|  
    |**Automatycznie Dodaj nowe raporty do sesji**|Zaznacz pole wyboru, aby automatycznie dodać plik danych do sesji wydajności.|  
    |**Dodaj zwiększającą się liczbę do wygenerowanych raportów**|Zaznacz pole wyboru, aby dodać zwiększającą się liczbę do nazwy pliku, jeśli istnieje więcej niż jeden plik o takiej samej nazwie. Wyczyść pole wyboru, aby zastąpić istniejący plik.|  
    |**Użyj sygnatury czasowej dla liczby**|Zaznacz pole wyboru, aby dodać datestamp do nazwy pliku.|
