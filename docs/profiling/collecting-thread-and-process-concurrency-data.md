---
title: Zbieranie danych współbieżności procesu & wątku
description: Użyj metody profilowania narzędzia profilowania współbieżności, aby zebrać dane dotyczące każdego zdarzenia synchronizacji, które powoduje, że funkcja oczekuje na dostęp do zasobów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2f5065c3eafc9fb1cd9e36227a09bbf26ed321c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950211"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Zbieranie danych współbieżności dla wątku i procesu

Metoda profilowania w programie Visual Studio narzędzia profilowania pozwala zbierać dane rywalizacji o zasoby, które zawierają informacje o każdym zdarzeniu synchronizacji, które powoduje, że funkcja w profilowanej aplikacji oczekuje na dostęp do zasobu.

Metodę profilowania współbieżności można określić przy użyciu jednej z następujących procedur:

- Na pierwszej stronie kreatora profilowania kliknij pozycję **współbieżność**
- Na stronie **Ogólne** okna dialogowego właściwości sesji wydajności kliknij pozycję **współbieżność**.
- Na **Eksplorator wydajności** pasku narzędzi na liście **Metoda** kliknij pozycję **współbieżność**.

## <a name="common-tasks"></a>Typowe zadania

Dodatkowe opcje można określić w oknie dialogowym **strony właściwości** sesji wydajności. Aby otworzyć to okno dialogowe:

- W **Eksplorator wydajności** kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

Zadania w poniższej tabeli opisują opcje, które można określić w oknie dialogowym **strony właściwości** _sesji wydajności_ podczas profilowania przy użyciu metody współbieżności.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na stronie **Ogólne** Określ szczegóły nazewnictwa dla wygenerowanego pliku danych profilowania (. vsp).|- [Instrukcje: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stronie **Uruchamianie** Określ aplikację, która ma być uruchamiana, jeśli w rozwiązaniu kodu masz wiele projektów. exe.|- [Instrukcje: Określanie pliku binarnego do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|
|Na stronie **interakcja warstwy** Dodaj dane wywołania ADO.NET do przebiegu profilowania.|- [Zbierz dane interakcji warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **liczniki systemu Windows** Określ co najmniej jeden licznik wydajności systemu operacyjnego, który ma zostać dodany do danych profilowania jako znaczniki.|- [Instrukcje: zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stronie **Zaawansowane** określ wersję .NET Framework czasie wykonywania do profilowania, jeśli moduły aplikacji używają wielu wersji. Domyślnie pierwsza ładowana wersja jest profilowana.|- [Instrukcje: Określanie środowiska uruchomieniowego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
