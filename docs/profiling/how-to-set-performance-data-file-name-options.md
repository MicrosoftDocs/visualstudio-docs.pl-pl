---
title: 'Instrukcje: Ustawianie opcji nazwy pliku danych wydajności | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cc42b63524a867c0893aa255180c740d03d4b5fe
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778768"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Instrukcje: Ustawianie opcji nazwy pliku danych wydajności

Domyślnie zapisujesz dane profilowania (. *VSP*), używając następującej składni:

*Path\VSP-File\YYMMDD (N)* **. vsp**

Wszystkie parametry nazewnictwa można zmienić na stronie **Ogólne** okna dialogowego właściwości dla sesji wydajności.

|||
|-|-|
|*Ścieżka*|Katalog, który zawiera raport. Domyślną lokalizacją jest folder rozwiązania lub domyślna lokalizacja dla projektów i rozwiązań użytkownika.|
|*VSP-File*|Nazwa pliku danych profilowania. Nazwa domyślna to nazwa rozwiązania lub pliku wykonywalnego, który jest profilowany.|
|*YYMMDD*|Sygnatura daty, która pokazuje rok, miesiąc i dzień, w którym zbierane są dane profilowania.|
|*Azotan*|Jeśli istnieje więcej niż jeden plik danych profilowania, do nazwy pliku między nawiasami zostanie dodany przyrostowy numer.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Aby zmienić składnię nazewnictwa plików danych profilowania sesji wydajności

1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

2. Kliknij pozycję **Ogólne**.

3. W obszarze **raport**zmień dowolne z następujących ustawień:

    |||
    |-|-|
    |**Lokalizacja raportu**|Określ katalog, w którym mają być przechowywane pliki danych profilowania.|
    |**Nazwa raportu**|Określ nazwę podstawową dla plików.|
    |**Automatycznie Dodaj nowe raporty do sesji**|Zaznacz to pole wyboru, aby automatycznie dodać plik danych do sesji wydajności.|
    |**Dodawanie zwiększania liczby do wygenerowanych raportów**|Zaznacz pole wyboru, aby dodać przyrostowy numer do nazwy pliku, gdy istnieje więcej niż jeden plik o tej samej nazwie. Usuń zaznaczenie tego pola wyboru, aby zastąpić istniejący plik.|
    |**Użyj sygnatury czasowej dla liczby**|Zaznacz pole wyboru, aby dodać dateStamp do nazwy pliku.|
