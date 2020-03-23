---
title: 'Jak: Ustawianie opcji nazwy pliku danych wydajności | Dokumenty firmy Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778768"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Instrukcje: ustawianie opcji nazwy pliku danych wydajności

Domyślnie zapisujesz dane profilowania (.* vsp*) przy użyciu następującej składni:

*Ścieżka\VSP-File\YYMMDD(N)* **.vsp**

Można zmienić dowolny parametr nazewnictwa na stronie **Ogólne** okna dialogowego właściwości sesji wydajności.

|||
|-|-|
|*Ścieżka*|Katalog zawierający raport. Domyślną lokalizacją jest folder rozwiązania lub domyślna lokalizacja projektów i rozwiązań użytkownika.|
|*Plik VSP*|Nazwa pliku danych profilowania. Nazwa domyślna to nazwa rozwiązania lub pliku wykonywalnego, który jest profilowany.|
|*YYMMDD*|Sygnatura daty przedstawiająca rok, miesiąc i dzień, w którym dane profilowania zostały zebrane.|
|*(N)*|Jeśli istnieje więcej niż jeden plik danych profilowania, do nazwy pliku między nawiasami jest dodawany przyrostowy numer.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Aby zmienić składnię nazewnictwa profilowania plików danych sesji wydajności

1. W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

2. Kliknij **pozycję Ogólne**.

3. W **obszarze Raport**zmień dowolne z następujących ustawień:

    |||
    |-|-|
    |**Lokalizacja raportu**|Określ katalog do przechowywania plików danych profilowania.|
    |**Nazwa raportu**|Określ nazwę podstawową plików.|
    |**Automatyczne dodawanie nowych raportów do sesji**|Zaznacz to pole wyboru, aby automatycznie dodać plik danych do sesji wydajności.|
    |**Dołączanie numeru przyrostowego do wygenerowanych raportów**|Zaznacz to pole wyboru, aby dodać numer przyrostowy do nazwy pliku, gdy istnieje więcej niż jeden plik o tej samej nazwie. Wyczyść to pole wyboru, aby zastąpić istniejący plik.|
    |**Używanie sygnatury czasowej dla numeru**|Zaznacz to pole wyboru, aby dodać sygnaturę daty do nazwy pliku.|
