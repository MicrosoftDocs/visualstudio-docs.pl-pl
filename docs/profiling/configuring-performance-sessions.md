---
title: Konfigurowanie sesji wydajności | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bdf1c372ffcb3ad3a0ebf102827565853947e2b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777871"
---
# <a name="configure-performance-sessions"></a>Konfigurowanie sesji wydajności
Za [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pomocą narzędzi profilowania, można zbierać szeroką gamę danych o wydajności dla dużej liczby typów aplikacji. W tej sekcji pokazano, jak używać Kreatora wydajnościi właściwości sesji wydajności i docelowego pliku binarnego do konfigurowania narzędzi profilowania do zbierania danych, które Cię interesują. Właściwości konfiguracji narzędzi profilowania mogą być również używane do kontrolowania ilości danych gromadzonych w przebiegu profilowania. Aby uzyskać więcej informacji, zobacz [Kontrolowanie gromadzenia danych](../profiling/controlling-data-collection.md).

> [!NOTE]
> W wielu przypadkach przy użyciu domyślnych właściwości Kreatora wydajności jest skutecznym sposobem zbierania danych profilowania. Aby uzyskać więcej informacji, zobacz [Przewodnik dla początkujących dotyczący profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md) i [Wprowadzenie.](../profiling/getting-started-with-performance-tools.md)

## <a name="common-tasks"></a>Typowe zadania

| Zadanie | Powiązana zawartość |
| - | - |
| **Ustaw podstawowe opcje profilowania:** Należy [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] skonfigurować używanie serwera symboli firmy Microsoft. Zapewni to dostęp do symboli, takich jak nazwy funkcji i parametrów, dla bieżącej wersji systemu Windows i innych aplikacji firmy Microsoft. Można również określić inne opcje ogólne przed rozpoczęciem sesji profilowania, takie jak uprawnienia systemowe do narzędzi profilowania i nazwy plików danych profilowania. | -   [Jak: Odwoływanie się do informacji o symbolu systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Jak: Serialize informacje o symbolu](../profiling/how-to-serialize-symbol-information.md)<br />-   [Jak: Ustawianie bieżącej sesji](../profiling/how-to-set-the-current-session.md)<br />-   [Jak: Ustawianie uprawnień](../profiling/how-to-set-permissions.md)<br />-   [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Określ dane, które chcesz zebrać:** Procedury używane do konfigurowania sesji profilowania zależą od typu aplikacji docelowej, którą chcesz profilować i typu danych wydajności, które mają być zbierane. | -   [Jak: Wybierz metody zbierania](../profiling/how-to-choose-collection-methods.md)<br />-   [Zbieranie statystyk wydajności przy użyciu próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Zbieranie danych dotyczących alokacji pamięci i okresu istnienia .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Zbieranie szczegółowych danych dotyczących chronometrażu przy użyciu oprzyrządowania](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Jak: Profil kodu JavaScript na stronach internetowych](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Zbieranie danych dotyczących współbieżności wątków i procesów](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Zbieranie dodatkowych danych dotyczących wydajności](../profiling/collecting-additional-performance-data.md) |
| **Ustaw zaawansowane opcje konfiguracji:** Podczas profilowania aplikacji .NET Framework, które ładują wiele wersji wspólnego języka wykonywania (CLR), można określić, która wersja do profilu. Jeśli w sesji wydajności znajduje się wiele plików exe, można ustawić kolejność uruchamiania plików binarnych. | -   [Jak: Określ środowisko uruchomieniowe programu .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Jak: Określ plik binarny, aby rozpocząć](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>Powiązane sekcje
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>Zobacz też
- [Eksplorator wydajności](../profiling/performance-explorer.md)
