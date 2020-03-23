---
title: Widok linii — dane próbkowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ff4d851937111400002de531696b9b69aec20ba9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778586"
---
# <a name="lines-view---sampling-data"></a>Widok linii — dane próbkowania
Widok Linie próbkowania danych zawiera listę danych wydajności dla instrukcji, które były wykonywane, gdy próbki zostały zebrane w przebiegu profilowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 W pliku źródłowym instrukcja może obejmować więcej niż jeden wiersz w pliku źródłowym, a pojedynczy wiersz może zawierać więcej niż jedną instrukcję. Oświadczenie jest identyfikowane przez następujące:

- Plik źródłowy zawierający instrukcję funkcji.

- Funkcja, która zawiera instrukcję.

- Wiersz źródłowy, w którym rozpoczyna się instrukcja.

- Znak w wierszu źródłowym, od którego rozpoczyna się instrukcja.

- Wiersz źródłowy, w którym kończy się instrukcja.

- Znak w wierszu źródłowym, w którym kończy się instrukcja.

  Kolumna Nazwa wiersza zawiera sortowalne łączenia danych identyfikatorów.

  Z definicji instrukcja nie wywoływać inne funkcje. W związku z tym wyświetlane są tylko wartości wyłączne.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu zawierającego linię funkcyjną.|
|**Ścieżka modułu**|Ścieżka modułu zawierającego linię funkcyjną.|
|**Plik źródłowy**|Plik źródłowy zawierający wiersz funkcji.|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres początkowy funkcji.|
|**Początek wiersza źródłowego**|Numer wiersza początkowego w pliku źródłowym, w którym pobrano ten przykład.|
|**Koniec wiersza źródłowego**|Numer wiersza końcowego w pliku źródłowym, w którym pobrano tę próbkę.|
|**Początek znaku źródłowego**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym pobrano ten przykład.|
|**Źródłowy koniec znaku**|Przesunięcie znaku końcowego w wierszu pliku źródłowego, w którym pobrano ten przykład.|
|**Nazwa wiersza**|Wygenerowany przez profiler identyfikator wiersza o następującej`Source File`składni:**;[** `Line Number Start` **,**,`Character Start`**]->; [**`Line Number End`**,**`Character End`**]**|
|**Ekskluzywne próbki**|Całkowita liczba próbek, które zostały zebrane podczas wykonywania wiersza funkcji.|
|**Próbki na wyłączność %**|Procent wszystkich próbek w przebiegu profilowania, które zostały zebrane podczas wykonywania wiersza funkcji.|

## <a name="see-also"></a>Zobacz też
- [Widok linii — próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)
