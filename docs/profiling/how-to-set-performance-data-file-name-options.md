---
title: Jak ustawić opcje nazwy pliku danych wydajności | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1fc548f5e051be878382d81bd040accbb13e9755
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548125"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Instrukcje: ustawianie opcji nazwy pliku danych wydajności

Domyślnie zapisujesz dane profilowania (.* VSP*), używając następującej składni:

*Path\VSP-File\YYMMDD (N)* **. vsp**

Wszystkie parametry nazewnictwa można zmienić na stronie **Ogólne** okna dialogowego właściwości dla sesji wydajności.

|Parametr|Opis|
|-|-|
|*Ścieżka*|Katalog, który zawiera raport. Domyślną lokalizacją jest folder rozwiązania lub domyślna lokalizacja dla projektów i rozwiązań użytkownika.|
|*VSP-File*|Nazwa pliku danych profilowania. Nazwa domyślna to nazwa rozwiązania lub pliku wykonywalnego, który jest profilowany.|
|*YYMMDD*|Sygnatura daty, która pokazuje rok, miesiąc i dzień, w którym zbierane są dane profilowania.|
|*Azotan*|Jeśli istnieje więcej niż jeden plik danych profilowania, do nazwy pliku między nawiasami zostanie dodany przyrostowy numer.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Aby zmienić składnię nazewnictwa plików danych profilowania sesji wydajności

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
