---
title: 'Instrukcje: Ustawianie opcji nazwy pliku danych wydajności | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b83b0aa083ca115797c9dc1cd8345d397307177
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626963"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Instrukcje: Ustawianie opcji nazwy pliku danych wydajności

Domyślnie zapisywać danych profilowania (. *Vsp*) plików przy użyciu następującej składni:

*Path\VSP-File\YYMMDD(N)* **.vsp**

Można zmienić nazw parametrów w **ogólne** strony okna dialogowego właściwości sesji wydajności.

|||
|-|-|
|*Path*|Katalog, który zawiera raport. Domyślna lokalizacja to folder rozwiązania lub domyślna lokalizacja dla projektów i rozwiązań użytkownika.|
|*VSP-File*|Nazwa pliku danych profilowania. Domyślną nazwą jest nazwa rozwiązania lub pliku wykonywalnego która profilowana jest.|
|*YYMMDD*|Sygnatura daty, która zawiera rok, miesiąc i dzień, zebranych danych profilowania.|
|*(N)*|Jeśli istnieje więcej niż jeden plik danych profilowania, zwiększona liczba jest dodawany do nazwy pliku w nawiasach.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Aby zmienić Składnia nazwy pliku danych profilowania w sesji wydajności

1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij przycisk **właściwości**.

2. Kliknij przycisk **ogólne**.

3. W obszarze **raportu**, zmienić dowolne z następujących ustawień:

    |||
    |-|-|
    |**Lokalizacja raportu**|Określ katalog do przechowywania plików danych profilowania.|
    |**Nazwa raportu**|Określ nazwę bazową dla plików.|
    |**Automatycznie Dodaj nowe raporty do sesji**|Zaznacz pole wyboru, aby automatycznie dodać plik danych do sesji wydajności.|
    |**Dodaj zwiększającą się liczbę do wygenerowanych raportów**|Zaznacz pole wyboru, aby dodać zwiększającą się liczbę do nazwy pliku, jeśli istnieje więcej niż jeden plik o takiej samej nazwie. Wyczyść pole wyboru, aby zastąpić istniejący plik.|
    |**Użyj sygnatury czasowej dla liczby**|Zaznacz pole wyboru, aby dodać datestamp do nazwy pliku.|