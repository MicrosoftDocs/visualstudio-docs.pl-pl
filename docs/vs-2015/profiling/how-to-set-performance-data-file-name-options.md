---
title: 'Instrukcje: Ustawianie opcji nazwy pliku danych wydajności | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71ac053a24b3f765a58fc050ceec84115e1a4e3d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548398"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Instrukcje: Ustawianie opcji nazwy pliku danych wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie zapiszesz plik danych profilowania (. vsp) przy użyciu następującej składni:  
  
 *Path\VSP-File\YYMMDD (N)* **. vsp**  
  
 Wszystkie parametry nazewnictwa można zmienić na stronie Ogólne okna dialogowego właściwości dla sesji wydajności.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
|Element składni|Opis|  
|-|-|  
|*Ścieżka*|Katalog, który zawiera raport. Domyślną lokalizacją jest folder rozwiązania lub domyślna lokalizacja dla projektów i rozwiązań użytkownika.|  
|*VSP-File*|Nazwa pliku danych profilowania. Nazwa domyślna to nazwa rozwiązania lub pliku wykonywalnego, który jest profilowany.|  
|*YYMMDD*|Sygnatura daty, która pokazuje rok, miesiąc i dzień, w którym zbierane są dane profilowania.|  
|*Azotan*|Jeśli istnieje więcej niż jeden plik danych profilowania, do nazwy pliku między nawiasami zostanie dodany przyrostowy numer.|  
  
### <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Aby zmienić składnię nazewnictwa plików danych profilowania sesji wydajności  
  
1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.  
  
2. Kliknij pozycję **Ogólne**.  
  
3. W obszarze **raport**zmień dowolne z następujących ustawień:  
  
    |Nazwa|Opis|  
    |-|-|  
    |**Lokalizacja raportu**|Określ katalog, w którym mają być przechowywane pliki danych profilowania.|  
    |**Nazwa raportu**|Określ nazwę podstawową dla plików.|  
    |**Automatycznie Dodaj nowe raporty do sesji**|Zaznacz to pole wyboru, aby automatycznie dodać plik danych do sesji wydajności.|  
    |**Dodawanie zwiększania liczby do wygenerowanych raportów**|Zaznacz pole wyboru, aby dodać przyrostowy numer do nazwy pliku, gdy istnieje więcej niż jeden plik o tej samej nazwie. Usuń zaznaczenie tego pola wyboru, aby zastąpić istniejący plik.|  
    |**Użyj sygnatury czasowej dla liczby**|Zaznacz pole wyboru, aby dodać dateStamp do nazwy pliku.|
